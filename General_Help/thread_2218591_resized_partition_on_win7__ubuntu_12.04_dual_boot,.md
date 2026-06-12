---
title: "resized partition on win7 / ubuntu 12.04 dual boot, now cactus"
date: 2014-04-21
forum: General Help
---

### Post by Hodor on 2014-04-21
Hi
I've booted into a 12.04.4 live cd; I'm trying to reinstall to recover my system (background below).
I'm trying to follow these directions: [http://askubuntu.com/questions/94542/how-can-i-repair-my-installation](http://askubuntu.com/questions/94542/how-can-i-repair-my-installation)
I'm at the screen 'installation type'; all the 'format' check boxes are unchecked; when I click 'install now' I get an error message: 
'no root file system ....'.
Ho do I proceed?
If I select /dev/sda and click 'New partition table' I get a scary warning that all current partitions will be removed (is this correct even if I have unselected 'format')?


background follows:
===============================================
I booted with a 14.04 live cd and resized my 12.04 partion (reduced size).
When the system rebooted it went into win 7 start up (not really intended) - windows decided to do some stuff (message along the lines 'please wait while windows configures ..') or some such.
I restarted, now I can't boot into ubuntu:
- I get an error message about booting into low graphics mode and some options ('run in low graphics mode for just one session ...') - but I'm having trouble selecting anything (keyboard / mouse not really working).
- I tried rebooting again into live cd - but I can't select the f12 to boot from cd (goes straight to grub).
- I tried dpkg ? (some repair option) - but no joy.

So now I can boot into my windows 7, but not my ubuntu and I don't seem to be able to select booting into cd.

I'm quite stressed about this - my school work needs attention now but I can't do it in windows.
Can anyone help me please?
Is there someway I can boot into a recovery CD from within windows / windows command line, because I don't seem to be able to tell bios to boot from the cd (not sure what that problem is).
Thanks

update: so I've just managed to boot into a 12.02 recovery cd (pulled out a usb for wireless mouse /keyboard, which apparently was stopping regular keyboard working).
any tips?

---

### Post by Mark Phelps on 2014-04-21
I would be concerned about reinstalling Ubuntu at this point.  We've seen numerous posts from folks who've tried to do that and ended up with their previous Windows installation completely REMOVED! It appears, in some cases, when you tell the installer to replace an existing Ubuntu installation, it interprets that as reusing the entire disk -- which then results in complete reformatting and removal of the Windows partitions.

If you can, you should do an image backup of your Win7 setup to an external drive.  At the very least, use the Backup option in Win7 to create and burn a Win7 Repair CD.  A free Windows app you can use to do image backups is Macrium Reflect.

---

### Post by Hodor on 2014-04-21
OK, thanks.
Resized partition back up, now 12.04 working again!
All I need now is a new pair of trousers :)

---

