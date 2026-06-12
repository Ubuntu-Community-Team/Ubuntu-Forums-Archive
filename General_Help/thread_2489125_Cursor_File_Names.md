---
title: "Cursor File Names"
date: 2023-07-19
forum: General Help
---

### Post by meetdilip on 2023-07-19
Hi, I made a test cursor theme with fallback as Yaru

> 
[Icon Theme]
Name=@test@
Comment=@test Green Cursor Theme by meetdilip@
Inherits=@Yaru@

I have 1 cursors folder and 1 index.theme file. In the cursors folder, I have the same pointer file named as 3 files with names

arrow.xmc
default.xmc
left_ptr.xmc

Sadly, none of them works for the default pointer and I get the Yaru pointer when I select the " test " cursor theme.

Wondering what the names are for each individual file in the Ubuntu cursor theme. I couldn't find any reliable documentation. Thanks.

PS: I created the xmc file using GIMP.

---

### Post by meetdilip on 2023-07-19
Found this man page for Jammy

[https://manpages.ubuntu.com/manpages/jammy/man3/X11::CursorFont.3pm.html](https://manpages.ubuntu.com/manpages/jammy/man3/X11::CursorFont.3pm.html)

Looks like I have the .xmc files named correctly. But why the cursor image is not showing up? Instead, I get the default cursor.

---

### Post by Dennis N on 2023-07-19
I think you have to rename them without the .xmc extension. 
 
There is a utility called **xcursorgen** to create mouse cursors. You might look into that. It's in the Ubuntu repository.

```
XCURSORGEN(1)               General Commands Manual              XCURSORGEN(1)

NAME
       xcursorgen - create an X cursor file from a collection of PNG images
```

Edit:
xcursorgen is part of **x11-apps** package, which is installed by default. 

```
dmn@Kayleigh:~$ apt search xcursorgen
Sorting... Done
Full Text Search... Done
x11-apps/lunar,now 7.7+9 amd64 [installed,automatic]
  X applications
```

---

### Post by meetdilip on 2023-07-19
You are right @Dennis N . It works when I removed the .xmc extension. Thanks :)

---

### Post by meetdilip on 2023-07-19
If I may, I ran 

xfd -fn cursor

trying to figure out things. Now when I use GIMP canvas, I get a some very old style icons. Is there any method to revert it back to the Ubuntu 22.04 default, which is much more polished. Thanks.

---

### Post by Dennis N on 2023-07-19
> **meetdilip said:**
> If I may, I ran xfd -fn cursor trying to figure out things. Now when I use GIMP canvas, I get a some very old style icons. Is there any method to revert it back to the Ubuntu 22.04 default, which is much more polished. Thanks.

As long as you didn't destroy the original Yaru theme, you should be able to switch back with the Gnome Tweaks Tool > Appearance > Cursor.

You might want to try modifying an existing cursor which keeps the style. Years ago, I created a blinking cursor to make it easy to locate by modifying a few of the existing theme's cursors. The most important one to change is the left pointer since it displays when there is no other activity. There is a thread on this forum about how to do that:

[https://ubuntuforums.org/showthread.php?t=2384798](https://ubuntuforums.org/showthread.php?t=2384798)

---

### Post by meetdilip on 2023-07-19
Thanks. :)

---

