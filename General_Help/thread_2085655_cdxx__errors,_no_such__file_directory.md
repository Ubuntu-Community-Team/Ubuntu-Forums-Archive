---
title: "cd/x/x  errors, no such  file directory"
date: 2012-11-18
forum: General Help
---

### Post by ramblinche81 on 2012-11-18
This weekend I've made it through the 12.04 boot load screen failures, and now am trying to permanently apply the fixes.

When I activate a Terminal cntl alt f2, it goes to 
user@machine ~$

When I attempt to follow guidance to update grub with 
cd/etc/default

I get a reply no such directory before I can sudo gedit grub

cntl c, cntl z, other command breaks don't seem to release me.

I used sudo su to go to root, and same system response

The system is stuck on something ?

Where do I start ?

---

### Post by steeldriver on 2012-11-18
You need some space between the command (cd) and the filename argument (/etc/default)

Also you should use gksudo rather than sudo for GUI applications such as gedit

```
cd  /etc/default
gksudo gedit grub
```

---

### Post by ramblinche81 on 2012-11-18
steeld, thanks for the guidance.... for those of us who do things infrequently, the obvious is not always apparent, especially when follow sticky notes etc.

OK...I can move around the file structure.

When I attempt to activate gksudo gedit grub, I get an error message
gktsudo 6394   gtkwarning cannot open display


When I attempt to open sudo gedit grub, I get an error message similar with more details
gedit 6423  warning command line  dbus-launch - autolaunch xxxxxxxxxxxxxx - binary syntax  close std err     exited with non zero exit  status  1  autolaunch error  x11 initialization failed /n     cannot open display

Being the stubborn problem solver, I tried to edit grub file directly (its just a txt file ???), but it is coded read only and will not let me save.

I am tempted to save with new name, then edit file back to grub.  do you see any issues ?

---

### Post by Bashing-om on 2012-11-18
try steeldriver's codes with copy paste, unless your last is a typo "gktsudo" is not valid ...should be gksudo as directed. ("gktsudo" I expect would generate error).

"gksudo" will generate password window ..enter password-> grub file opens for editing and as now having admin privileges can save the changes.
[INDENT]just try'n to help ==> BDQ

[/INDENT]

---

### Post by ramblinche81 on 2012-11-18
Bashing , thanks for trying to help
gksudo gedit grub 
generates a similar error message

cannot open display

something has it lock up or reserved.

Back to my cheating question to at least get the start up load going semi automatically.

Can I edit grub, save with new name, then change name of file to grub ?  or will system security block me ?

---

### Post by steeldriver on 2012-11-18
if you're having issues with graphical applications and/or gksudo you can use a terminal based editor e.g. nano

```
sudo nano /etc/default/grub
``` When you are done press Ctrl-O to save, confirm the file name, then Ctrl-X to exit.

EDIT: DOH! just noticed you are doing this in a virtual terminal (Ctrl-Alt-F2) - so you WILL need to use a terminal based editor for sure. Sorry I didn't spot that earlier.

---

### Post by ramblinche81 on 2012-11-18
That got me in !:):):)...sometimes I have to remember I am learning a new language and there are different dialects in play.
 
edit of command lines complete
 
sudu update grub complete
 
check of command lines verifies edits in place.
 
now I will go research what I can learn about features and purpose of virtual terminals vs real terminals.
 
Thanks for being patient and walking me through the finer points of the command line requirements. I only do this about once every couple of years becuase overall the system is really stable and doesn't need a lot of my manual refinements unless I am installing something , in this case, the whole ISO OS.
 
Next is figure out why my machine is going through a cycle of restart updates.

---

