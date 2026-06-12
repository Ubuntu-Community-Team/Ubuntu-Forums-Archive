---
title: "Disable Middle (or scroll) mouse button"
date: 2007-02-06
forum: General Help
---

### Post by Gen2ly on 2007-02-06
I just purchased a new mouse and have been issues with it.  I was writing a document, and when I went through it the next day it seemed to have random clippings of my work all over.  I hadn't used a three button mouse before, and couldnt think what had occured.

Well, what happened it the scroll wheel when pressed down acts as both a copy and paste mechanism.  This could be a behavior I need to get used to, but for now I found it extremely annoying and want to get rid of it.  Here's the way to do it:

To see the mouse mappings:
> xmodmap -pp

If you don't haven't done any configuring before it'll look something like this:
```
There are 9 pointer buttons defined.

    Physical        Button
     Button          Code
        1              1
        2              2
        3              3
        4              4
        5              5
        6              6
        7              7
        8              8
        9              9
```

Swapping button 2 with button 9 (which may be unused) should disable middle-click: 
> xmodmap -e "pointer = 1 9 3 4 5 6 7 8 2"
while retaining wheel support.  If this works, put it in the Sessions Control-Panel under startup programs.

---

### Post by Steve H on 2007-02-10
I have the opposite problem, my mouse wheel works but when i try to scroll by holding down the mouse wheel (as i do in windows) then nothing happens.

When i did xmodmap -pp i got the following:

There are 9 pointer buttons defined.

    Physical        Button
     Button          Code
        1              1
        2              2
        3              3
        4              4
        5              5
        6              6
        7              7
        8              8
        9              9

which is i a different order from yours......is this why my scroll button doesn't work? should i set it up to be in the same order as the one you have shown?

---

### Post by Gen2ly on 2007-03-10
Oops thats my bad.  I had inadvertantly added the changed version instead of the original.

Fixed.

---

### Post by Gen2ly on 2007-03-24
This isn't I've discovered the best solution.  Though this fixes pastings throughout the documents as I scroll through them, in Firefox it still behaves like the Mouse #1 button (i.e. select).  Someone have a better idea on how to do this?

---

### Post by Gen2ly on 2007-03-30
This middle mouse button is very annoying.  If i scroll down alot of times the button is pushed and it inadvertantly head to an another website.  I not sure how its possible to fix it.

---

### Post by yabbadabbadont on 2007-03-30
> **Dirk.R.Gently said:**
> This middle mouse button is very annoying.  If i scroll down alot of times the button is pushed and it inadvertantly head to an another website.  I not sure how its possible to fix it.

I assume you are using Firefox.  Edit->Preferences->Advanced->Use Autoscrolling  (enable this)

Then, when you inadvertantly click the wheel, you won't be redirected to another website.

---

### Post by Gen2ly on 2007-04-02
> **yabbadabbadont said:**
> I assume you are using Firefox.  Edit->Preferences->Advanced->Use Autoscrolling  (enable this)

Then, when you inadvertantly click the wheel, you won't be redirected to another website.

Heeeeeeeyyyyy!   You're onto something yeah!  lol, didn't hear about that before!  Cheers!

---

### Post by maniac_X on 2007-04-15
> **yabbadabbadont said:**
> I assume you are using Firefox.  Edit->Preferences->Advanced->Use Autoscrolling  (enable this)


Thx Yabba,
Solved my somewhat similar problem, I had to revert to using an old IBM PS2 3-button mouse because my $40 gaming mouse is having intermittent button problems(mouse buttons giving up the ghost). Fortunately it has a long warranty(Logitec) and I'll be able to get a replacement. 
Your post gave me back my middle-button scrolling. :D

Just curious, what does the "**Smooth Scrolling**" option do or add?  :confused:

Thx again!

---

