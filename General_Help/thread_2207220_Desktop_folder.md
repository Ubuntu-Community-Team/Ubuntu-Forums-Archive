---
title: "Desktop folder"
date: 2014-02-22
forum: General Help
---

### Post by phottomatt on 2014-02-22
I've accidentally moved my Desktop folder into my pictures folder and can not move it back, the "move to" option is grayed out. Is it merely a shortcut that I can delete?
[ATTACH=CONFIG]250582[/ATTACH]

---

### Post by ajgreeny on 2014-02-22
I think your system has automatically made a new Desktop folder if what is seen on your screenshot is correct.

Maybe you simply need to move any files that were in the old Desktop folder back to the new one with ```
cp Pictures/Desktop/* Desktop
```and then if necessary re-configure your new Desktop.

What do you see if you open the apparently new Pictures/Desktop folder in nautilus?  Any files or folders?

---

### Post by phottomatt on 2014-02-22
They are the same, and anything I do in one hapens in the other.
[ATTACH=CONFIG]250585[/ATTACH]

---

### Post by deadflowr on 2014-02-22
Did you run ajgreeny's command to try to move Desktop back to the top level of the home folder?

---

### Post by phottomatt on 2014-02-22
I just did with no change, how do I reconfigure desktop?

---

### Post by ajgreeny on 2014-02-23
> **phottomatt said:**
> I just did with no change, how do I reconfigure desktop?

You may not need to, but never having seen your situation before I was just saying that you might need to do so, eg add any icons you normally have on the Desktop that are no longer there, or change background to what you want.

If you right click on the Pictures/Desktop and choose Properties what does it tell you about the folder?
What is the output of command ```
ls -l Pictures/ | grep Desktop
```for the Desktop folder within it?

---

### Post by phottomatt on 2014-02-23
[ATTACH=CONFIG]250610[/ATTACH]
```
:~$ ls -l Pictures/ | grep Desktop
drwxr-xr-x 5 john john   4096 Feb 22 17:05 [COLOR=#ff0000]Desktop[/COLOR]

```

---

### Post by ajgreeny on 2014-02-23
Well, I am baffled!
Apart from suggesting you put the Pictures/Desktop folder into trash so it can be restored if you need to, I can not think of any other actions you can take.

However, before you do that let's see the output of ```
ls -l | grep Desktop
``` to see if that is a link to the one in Pictures, which was why I asked you to run the previous ls command; to see if the Desktop in Pictures was a link to the main Desktop, which it wasn't so let's see the opposite direction.

---

### Post by deadflowr on 2014-02-23
I wonder if there is a Desktop folder in the top level.
Perhaps a simple 
```
ls
```
just to see if one is there.
If not, maybe a mkdir Desktop to recreate it, then copy/move everything back into it.

---

### Post by phottomatt on 2014-02-23
```
:~$ ls -l | grep Desktop
drwxr-xr-x   3 john john  4096 Feb 22 19:49 [COLOR=#ff0000]Desktop[/COLOR]

```

---

### Post by phottomatt on 2014-02-23
> **deadflowr said:**
> I wonder if there is a Desktop folder in the top level.
Perhaps a simple 
```
ls
```
just to see if one is there.
If not, maybe a mkdir Desktop to recreate it, then copy/move everything back into it.
```
:~$ ls
android-utility  Developement  Downloads  Pictures   Theming
bin              dmesg         Dropbox    Public     Videos
Desktop          Documents     Music      Templates

```

---

### Post by CaptainMark on 2014-02-24
It could be you never actually moved the desktop folder but created a link to it, I think this is done in nautilus (At least used to be) by holding ctrl + shift and dragging, so could be easily be done by accident, try ```
unlink ~/Pictures/Desktop
```
 EDIT: I should get into the habit of reading the whole post first, I see this has already been mentioned now

---

### Post by phottomatt on 2014-02-24
> **CaptainMark said:**
> It could be you never actually moved the desktop folder but created a link to it, I think this is done in nautilus (At least used to be) by holding ctrl + shift and dragging, so could be easily be done by accident, try ```
unlink ~/Pictures/Desktop
```
 EDIT: I should get into the habit of reading the whole post first, I see this has already been mentioned now
Yeah that doesn't work because it's actually a directory. I'm wondering if the files are identical in both, would there be a way to delete one with out dleting the other, I gues I could just move all the files out so I don't lose anything and try some stuff.

---

### Post by phottomatt on 2014-02-26
Bump

---

### Post by phottomatt on 2014-03-28
```
ls
Android Developement  [COLOR=#a9a9a9]dmesg[/COLOR]      fontconfig       Public
android-utility       Documents  libdvdcss_build  Templates
bin                   Downloads  Music            Ubuntu One
Desktop               Dropbox    Pictures         Videos



```I have recently updated to 13.04 to see if that would fix the problem but it did not.

---

