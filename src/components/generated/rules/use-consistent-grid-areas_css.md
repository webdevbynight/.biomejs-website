**Since**: `vnext`
:::caution
This rule is part of the [nursery](/linter/rules/#nursery) group.
:::

Sources: 
- Same as: <a href="https://github.com/stylelint/stylelint/blob/main/lib/rules/named-grid-areas-no-invalid/README.md" target="_blank"><code>stylelint/named-grid-areas-no-invalid</code></a>

Disallows invalid named grid areas in CSS Grid Layouts.

For a named grid area to be valid, all strings must define:

- the same number of cell tokens
- at least one cell token

And all named grid areas that spans multiple grid cells must form a single filled-in rectangle.

## Examples

### Invalid

```css
a { grid-template-areas: "a a"
                         "b b b"; }
```

<pre class="language-text"><code class="language-text">code-block.css:1:26 <a href="https://biomejs.dev/linter/rules/use-consistent-grid-areas">lint/nursery/useConsistentGridAreas</a> ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

<strong><span style="color: Orange;">  </span></strong><strong><span style="color: Orange;">⚠</span></strong> <span style="color: Orange;">Inconsistent cell count in grid areas are not allowed.</span>
  
<strong><span style="color: Tomato;">  </span></strong><strong><span style="color: Tomato;">&gt;</span></strong> <strong>1 │ </strong>a { grid-template-areas: &quot;a a&quot;
   <strong>   │ </strong>                         <strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong>
    <strong>2 │ </strong>                         &quot;b b b&quot;; }
    <strong>3 │ </strong>
  
<strong><span style="color: lightgreen;">  </span></strong><strong><span style="color: lightgreen;">ℹ</span></strong> <span style="color: lightgreen;">Consider adding the same number of cell tokens in each string.</span>
  
</code></pre>

```css
a { grid-template-areas: "b b b"
                         ""; }
```

<pre class="language-text"><code class="language-text">code-block.css:1:33 <a href="https://biomejs.dev/linter/rules/use-consistent-grid-areas">lint/nursery/useConsistentGridAreas</a> ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

<strong><span style="color: Orange;">  </span></strong><strong><span style="color: Orange;">⚠</span></strong> <span style="color: Orange;">Empty grid areas are not allowed.</span>
  
<strong><span style="color: Tomato;">  </span></strong><strong><span style="color: Tomato;">&gt;</span></strong> <strong>1 │ </strong>a { grid-template-areas: &quot;b b b&quot;
   <strong>   │ </strong>                                
<strong><span style="color: Tomato;">  </span></strong><strong><span style="color: Tomato;">&gt;</span></strong> <strong>2 │ </strong>                         &quot;&quot;; }
   <strong>   │ </strong>                         <strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong>
    <strong>3 │ </strong>
  
<strong><span style="color: lightgreen;">  </span></strong><strong><span style="color: lightgreen;">ℹ</span></strong> <span style="color: lightgreen;">Consider adding the cell token within string.</span>
  
</code></pre>

```css
a { grid-template-areas: "a a a"
                         "b b a"; }
```

<pre class="language-text"><code class="language-text">code-block.css:1:33 <a href="https://biomejs.dev/linter/rules/use-consistent-grid-areas">lint/nursery/useConsistentGridAreas</a> ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

<strong><span style="color: Orange;">  </span></strong><strong><span style="color: Orange;">⚠</span></strong> <span style="color: Orange;">Duplicate filled in rectangle are not allowed.</span>
  
<strong><span style="color: Tomato;">  </span></strong><strong><span style="color: Tomato;">&gt;</span></strong> <strong>1 │ </strong>a { grid-template-areas: &quot;a a a&quot;
   <strong>   │ </strong>                                
<strong><span style="color: Tomato;">  </span></strong><strong><span style="color: Tomato;">&gt;</span></strong> <strong>2 │ </strong>                         &quot;b b a&quot;; }
   <strong>   │ </strong>                         <strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong><strong><span style="color: Tomato;">^</span></strong>
    <strong>3 │ </strong>
  
<strong><span style="color: lightgreen;">  </span></strong><strong><span style="color: lightgreen;">ℹ</span></strong> <span style="color: lightgreen;">Consider removing the duplicated filled-in rectangle: </span><span style="color: lightgreen;"><strong>a</strong></span>
  
</code></pre>

### Valid

```css
a { grid-template-areas: "a a a"
                         "b b b"; }
```

```css
a { grid-template-areas: "a a a"
                         "a a a"; }
```

## Related links

- [Disable a rule](/linter/#disable-a-lint-rule)
- [Configure the rule fix](/linter#configure-the-rule-fix)
- [Rule options](/linter/#rule-options)