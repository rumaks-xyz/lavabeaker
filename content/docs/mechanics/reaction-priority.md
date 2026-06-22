# reaction prioriyt

idk i don't feel like explaining this one, heres the code:

```cs
public int CompareTo(ReactionPrototype? other)
{
    if (other == null)
        return -1;

    if (Priority != other.Priority)
        return other.Priority - Priority;

    // Prioritize reagents that don't generate products. This should reduce instances where a solution
    // temporarily overflows and discards products simply due to the order in which the reactions occurred.
    // Basically: Make space in the beaker before adding new products.
    if (Products.Count != other.Products.Count)
        return Products.Count - other.Products.Count;

    return string.Compare(ID, other.ID, StringComparison.Ordinal);
}
```
