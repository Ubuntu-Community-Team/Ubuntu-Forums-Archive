---
title: "Mouse right click trouble in firefox"
date: 2008-06-15
forum: General Help
---

### Post by Robbyx on 2008-06-15
I am having trouble copying with the right click context menu. When  I right click after blocking some text it takes me back to the previous page. Could some one point me to the cure? I understand it is a known fault but could not find the solutions myself.

---

### Post by y-lee on 2008-06-15
> **Robbyx said:**
> I am having trouble copying with the right click context menu. When  I right click after blocking some text it takes me back to the previous page. Could some one point me to the cure? I understand it is a known fault but could not find the solutions myself.

What exactly do you mean by "after blocking some text"?

---

### Post by Robbyx on 2008-06-15
> **y-lee said:**
> What exactly do you mean by "after blocking some text"?

If I want to copy something on a web page I first block it and then right click and choose copy. If the cursor is in the area highlighted a right click is treated as a go back instruction. If the cursor is outside the blocked text it might allow me to see the options, but not necessarily on the first attempt. It will treat it as a go back but when I go forward it might then let me choose to copy.

Copy from the drop down menu works ok.

---

### Post by y-lee on 2008-06-15
> **Robbyx said:**
> If I want to copy something on a web page I first block it and then right click and choose copy. If the cursor is in the area highlighted a right click is treated as a go back instruction. If the cursor is outside the blocked text it might allow me to see the options, but not necessarily on the first attempt. It will treat it as a go back but when I go forward it might then let me choose to copy.

Copy from the drop down menu works ok.

Hmmm, very odd. I don't really know but which version of firefox do you have? And also which version of ubuntu?

Have you tried a new profile, type the code below into a terminal and create a new one

```
firefox -P
```

Do you have the same behavior in the new profile?

---

### Post by Robbyx on 2008-06-16
I have created a new profile and without any addons or extensions I am not getting the problem. So it seems to be one of the extensions relating to mouse gestures. I will check that out by disabling it in the default profile and see what happens.

Thanks for your help

Robin

---

### Post by y-lee on 2008-06-16
> **Robbyx said:**
> I have created a new profile and without any addons or extensions I am not getting the problem. So it seems to be one of the extensions relating to mouse gestures. I will check that out by disabling it in the default profile and see what happens.

Cool, let us know which add on caused the problem.

Anytime firefox doesn't work right always try a new profile, that is a general firefox debug trick ;)

---

