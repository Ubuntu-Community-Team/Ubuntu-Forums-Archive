---
title: "Having MAJOR problems with livecd"
date: 2005-10-13
forum: General Help
---

### Post by saadghauri on 2005-10-13
Hi , ive just begun using live cd 5-6 hours ago , and i need help :

1) I can't change my desktop resolution from 640-480 :( is this a limitation of livecd or a problem with my pc?

2) I can't access any files on my hd , in computer it shows only "CD-Rom" and "File Ssytem" and in file system i can only access the cd. Again , is this a limitation of livecd or a problem with my pc?

3) PLus , i cantt access https sites. firefox says Page cannopt be found

Pleeze help. Much thanks

---

### Post by Jeff Hunter on 2005-10-13
[QUOTE=saadghauri]Hi , ive just begun using live cd 5-6 hours ago , and i need help :

1) I can't change my desktop resolution from 640-480 :( is this a limitation of livecd or a problem with my pc?

2) I can't access any files on my hd , in computer it shows only "CD-Rom" and "File Ssytem" and in file system i can only access the cd. Again , is this a limitation of livecd or a problem with my pc?

3) PLus , i cantt access https sites. firefox says Page cannopt be found

Pleeze help. Much thanks[/QUOTE]
Okay, I can't help you with your first or third problems (I'm new myself)...I will tell you that for your first problem, that is not the LiveCD doing that, since my LiveCD booted me to 1280x1024 by default and let me play around with my settings, so I don't know what might cause that.

Your second problem is not really a problem so much as Ubuntu does not auto-mount file systems.  I can't give you the best run-down of it, but I can tell you where to look.  You might have to play around with it a bit, and if you try to mount the wrong device, it might cause your computer to lock up.

NOTICE:  This uses the command line prompt.  Access this either by selecting Applications->System Tools-> Terminal, or by holding down Ctrl+Alt+F1.  Before you do the second, let me warn you that this will take you to a full screen black terminal.  To get back to your desktop, simply type Alt+F7.  You can use anything from 1 through 6, and 7 is always your GUI front-end (some distros will let you use 8-12 as well for additional desktops, but it really isn't nessisary).

Okay, first you need a directory to mount it to.  Decide where you want it to be, something like /home/ubuntu/C:.  Then type [COLOR="Blue"]mkdir /home/ubuntu/C:[/COLOR] (or whatever you want it to be) and voila!  Note: It will only say something if it didn't work.  You can type [COLOR="Blue"]ls /home/ubuntu[/COLOR] to see if that worked (this will list all files and folders in that directory, sort of like DOS's dir command, only more powerful).

Next, you mount your file system.  If you are using NTFS, you might have some trouble with this, because NTFS support is shaky at best.

type [COLOR="Blue"]ls /dev[/COLOR] to get a list of all system "devices".  the list will likely be long, but it should include something like hda1, and this is what you are looking for.  Just make sure it is there.

Type [COLOR="Blue"]mount /dev/hda1 /home/ubuntu/C:[/COLOR] (or whatever it is you decided on).  If it spits out an error message, add sudo to the start of the line and try again.

Then your file system *should* be mounted!  Good luck!

---

