---
title: "word-boundary/stop-sign characters (GEdit et al.)"
date: 2008-04-30
forum: General Help
---

### Post by Ace_NoOne on 2008-04-30
This issue is a bit hard to describe (thus the inept title), so I'll use a practical example:

Say I have the following code in GEdit:
```
function foo() {
	lorem = "ipsum dolor sit amet";
}
```
If I use CTRL+RightArrow to move the cursor, it will jump as follows (asterisk indicates cursor positions):
```
*function* foo*() {
	lorem* = "ipsum*";*
}*
```
However, I would expect it to move like this:
```
*function* foo()* {*
*	*lorem* =* "*ipsum*";*
*}*
```

Is there any way to change this behavior?

---

