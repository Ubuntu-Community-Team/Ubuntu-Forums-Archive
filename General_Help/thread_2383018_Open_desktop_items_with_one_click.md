---
title: "Open desktop items with one click"
date: 2018-01-19
forum: General Help
---

### Post by raleigh3 on 2018-01-19
I can not find out how to open desktop items with a single click.

---

### Post by deadflowr on 2018-01-19
You mean like files (like a text file you might have on your desktop?)

Open your file manager and go to the preferences section.
There should be an option to select with double and single clicks.
Set it to single click.

Preferences should be in the Edit menu list.
Look in the Behavior tab.

---

### Post by raleigh3 on 2018-01-20
No, I mean clicking on any of the icons I have on my desktop.

---

### Post by vasa1 on 2018-01-20
See if you have something like this:

---

### Post by raleigh3 on 2018-01-20
Here is what I have.

---

### Post by vasa1 on 2018-01-20
Then this setting maybe tucked away somewhere else?

---

### Post by raleigh3 on 2018-01-20
I will look around more.

---

### Post by vasa1 on 2018-01-20
Just an idea ...
Run```
gsettings list-recursively | grep mouse
```and see if anything there offers a clue.

Another thing to try is to install *dconf-editor*, run it and explore. I don't use GNOME and so can't give you specifics.

---

### Post by deadflowr on 2018-01-20
> **raleigh3 said:**
> No, I mean clicking on any of the icons I have on my desktop.

The file manager controls the desktop, so did you even try what I asked?

Edit: Works as expected for me on mate 16.04.

---

### Post by raleigh3 on 2018-01-20
Yes, I did try it. It only works within the file manager.

This works.

```
Caja -> Edit -> Preferences 
Click Behavior tab
Select "Single click to open items"
```

---

### Post by vasa1 on 2018-01-20
> **raleigh3 said:**
> Yes, I did try it. It only works within the file manager.

This works.

```
Caja -> Edit -> Preferences 
Click Behavior tab
Select "Single click to open items"
```

"This works" for what?

---

### Post by raleigh3 on 2018-01-21
_Caja_ -> Edit -> Preferences 
Click Behavior tab
Select "Single click to open items"

---

### Post by deadflowr on 2018-01-21
> **raleigh3 said:**
> _Caja_ -> Edit -> Preferences 
Click Behavior tab
Select "Single click to open items"

That's what post #2 told you to do.
caja = file manager.

---

### Post by raleigh3 on 2018-01-21
I use thunar as file manager. Caja is one of several managers.

---

### Post by deadflowr on 2018-01-21
I assumed you were using the default file manager.
From [Posting Guidelines]("https://ubuntuforums.org/showthread.php?t=2158945")
> Always assume the the user has a default installation unless you are told otherwise

But it seems like you solved the problem though.
(regardless of how we misread each other)
Go ahead and mark this thread as solved if you will.

---

