---
title: "Running RedoBackup?"
date: 2012-11-08
forum: General Help
---

### Post by felkar on 2012-11-08
I have successfully created a CD that holds the "Redo" package.

I find the supplied "method of use" information to be too cryptic.

The most relevant texts  appear to be:

Quote:

[I]At the  boot  screen,  use the UP/DOWN arrows and  ENTER  key
to select your boot mode; some systems  may  only run  in one
particular mode;

* Remember that hardware support is limited to that of Ubuntu, and that your hardware must be compatible with Ubuntu in order to work with Redo Backup
[/I]

End of Quote.

If more detailed instructions exist, I would welcome being pointed to them.

felkar

---

### Post by mastablasta on 2012-11-08
boot from cd and select the mode you wan to boot in. for example if you card can not boot into normal mode (you get a black screen or screen with blinking cursor) you would need vesa (which is probably standard video mode) mode. this is basic video mode that is not as preety but does the job.

---

### Post by felkar on 2012-11-08
> **mastablasta said:**
> boot from cd and select the mode you wan to boot in. ....

The CD, that I created from "redobackup-livecd-1.0.3.iso" has the following content:

/media/felixk/Redo Backup/casper
/media/felixk/Redo Backup/install
/media/felixk/Redo Backup/isolinux
/media/felixk/Redo Backup/autorun.exe
/media/felixk/Redo Backup/autorun.inf
/media/felixk/Redo Backup/md5sum.txt

What needs to be done to use the cd and launch the "boot" routine?

"/media/felixk/Redo Backup/autorun.exe" looks to me like a "MS Windows" routine.  And my computer has no MS packages installed.

"/media/felixk/Redo Backup/isolinux" directory contains "isolinux.bin" file.  That looks more promising.

And the next step is???



felkar

---

