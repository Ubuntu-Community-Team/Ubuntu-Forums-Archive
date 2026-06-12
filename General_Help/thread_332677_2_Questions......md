---
title: "2 Questions....."
date: 2007-01-06
forum: General Help
---

### Post by nezermundy on 2007-01-06
Is there a way for Windows XP to boot up automatically and then if you want to ubuntu you hold down a key?

and also:

Does anybody know how to get the Windows XP Home Edition style login, where just click on the name and it logs you in.

Thank you very much!:p

---

### Post by nezermundy on 2007-01-06
I am sorry but I really need these answered by tonight otherwise I will have to remove it because it will cause problems unless the boot issue is solved and the login thing solved would be great.

---

### Post by lvlo on 2007-01-06
Maybe use autologin?

---

### Post by nezermundy on 2007-01-06
> **lvlo said:**
> Maybe use autologin?

I have 4 Users though, that is why I want it like Windows XP where you click on the user and it logs in without typing in the password.

But more important is the boot option for now, I want the computer to boot xp automatically and not have the boot option where you choose to ubuntu, I just want it to boot xp!!!

---

### Post by Mike'sHardLinux on 2007-01-06
Look for the file /boot/grub/menu.lst

This is the list that shows up when you first boot. You edit that file so that XP will be the default. If you don't how to do that, search for a grub how to. Here's an older link, but still should apply: [http://www.linuxquestions.org/questions/showthread.php?t=388283]("http://www.linuxquestions.org/questions/showthread.php?t=388283")

---

### Post by lvlo on 2007-01-06
:")

---

### Post by RandomJoe on 2007-01-06
Is it not sufficient to change the primary/default boot selection in GRUB?  Then GRUB will still run (you get the "press Escape for menu") but if you don't do anything it'll start Windows.  To run Ubuntu you press Escape, and select it from the menu.

To do that, edit /boot/grub/menu.lst and change the line "default 0" to point to the XP boot selection.  (I'm a command-line junkie, don't know if there's a graphical way to do this...)  The only hangup with this is XP will get listed last, so any time a new kernel is released through updates the number changes unless you remove old kernels.  To fix that, I *think* (haven't done this, but the comments in menu.lst suggest it!) you can move (or copy) the XP boot section to before the line that says "BEGIN AUTOMAGIC KERNELS LIST" so that it becomes boot option 0 no matter what.

(Be careful in that file, or you may not boot afterward...!)

---

### Post by nezermundy on 2007-01-06
Thanks moving it top of the list works however it highlights "Other Operating Systems" bit which means I can lower the boot time to 1 Second because gets the error.

I cannot find wheres you put this "default 0" if I put it in the windows xp section it gets an error on boot, is there any chance someone could paste a file with it already setup or show me where you put it exactly.

That would be great!

---

### Post by nezermundy on 2007-01-07
Anyone?](*,)

---

### Post by RandomJoe on 2007-01-07
On mine, the 'default 0' is already there - actually the first uncommented entry in the menu.lst file:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

```
This is on 6.06, perhaps it's different on 6.10 if that's what you have installed?

---

