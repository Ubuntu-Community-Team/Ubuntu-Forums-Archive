---
title: "[SOLVED] Synchronize with memory stick"
date: 2008-02-23
forum: General Help
---

### Post by MONODA on 2008-02-23
Hi I frequently update files on my usb memory stick so that I can take them with me whereever i go. But this task can take time and sometimes I even forget to do so and its not good. Is there anyway I can have a directory on my memory stick sync with a directory on my computer? thanx

---

### Post by Beefeater on 2008-02-23
Well you could use rsync for it. Depends a bit on what you want to do.

rsync -vrlptgoD directory directory is what I use to backup my files to a USB-drive. You might wanna look over the arguments though.

Are you transferring files both ways?

If not you could for example create a script that syncs a specific folder to your mem-stick everytime you plug it in.

The possibilities are endless :-)

---

### Post by MONODA on 2008-02-24
yeah i want to make a script that would sync everytime i plug my memory stick in, but how could I make it do that automatically? Yeah I have heard about rsync but didnt really know how to use it

---

### Post by MONODA on 2008-02-24
Ok I got a script to sync with my memory stick but I have a few questions.
once I sync for the first time and then I do it again, will all of my old files be replaced?
second, how can I activate the scirpt to run once my memory stick is plugged in?
thanks for all the help

---

### Post by Beefeater on 2008-02-24
What we are doing here you could describe as an incremental backup, only the changes in the files will be updated.

But it's important to know that if you set it up to go hard drive -> memory stick and then change a file on the memory-stick and run the script, it will be overwritten with the file on the hard drive.

You could use -u in rsync to ignore files which are newer on the memory stick.
I guess it would be possible to run the script both ways with -u but still there are some limitations.
One step at the time.

To make it automatic we create an udev rule.

Plug in the memory-stick and look which device drive it's using (/dev/sdb, /dev/sdc ..)
```
$ dmesg
```

Mine is on /dev/sdc

Check vendor and model

```
$  udevinfo -q all -n /dev/sdc
```

For me it's:

model: DataTraveler 2.0
vendor: Kingston

Now we can create the udev rule.

```
$ sudo vim /etc/udev/rules.d/10-local.rules
```

and paste this line but replace it with your vendor and model.

SUBSYSTEMS=="scsi", ATTRS{vendor}=="Kingston", ATTRS{model}=="DataTraveler 2.0", RUN+="/usr/bin/usbbackup %k"

Create /usr/bin/usbbackup

```
$ sudo vim /usr/bin/usbbackup
```

and put whatever script you have in there.

Then

```
$ sudo chmod a+x /usr/bin/usbbackup
```

So that's pretty much the basics. How you do it is up to you :-)
Sorry for any mistakes, just got out of bed.

---

### Post by MONODA on 2008-02-24
I just got a pretty good Idea.
since sometimes I just need to put my memory stick in for a very short amount of time, could I have the script ask my if i want to update my memory stick when I plug it in, kinda like when u plug in a camera?

---

### Post by MONODA on 2008-02-24
ok i just plugged in my memory stick and nothing is happening...
EDIT: oops sry my fault it works great!!!!! thanks :D

---

### Post by Beefeater on 2008-02-24
Good :-)

---

### Post by MONODA on 2008-02-26
Well it worked once but when I plugged my memory stick in again it did not run the script. I tried manually running the script (usbbackup through terminal) and it worked so I dont think the problem is with the script.
here is the script:
> 
#!/bin/bash

rsync -ru /home/dany/Documents/"9th Grade homework"/* /media/DANY/Sync/ > /home/dany/Documents/Logs/Sync 2>&1


what could be the problem?

---

### Post by strabes on 2008-02-26
Edit: What I posted was posted above.

---

### Post by tgalati4 on 2008-02-26
A simpler solution is to put the file *autorun* in the root directory of the flash disk.  Activate scripts in gnome-volume-properties.  

Add execute permissions to autorun:  sudo chmod +x autorun

Put your rsync script inside autorun.  Now every time you plug in your usbstick, you will get a dialog that asks if you want to run the script.

---

### Post by MONODA on 2008-02-26
> A simpler solution is to put the file autorun in the root directory of the flash disk. Activate scripts in gnome-volume-properties.

Add execute permissions to autorun: sudo chmod +x autorun

Put your rsync script inside autorun. Now every time you plug in your usbstick, you will get a dialog that asks if you want to run the script.
it works perfectly, thanks. but is there anyway to also have a nautilus windows open displaying the flashdisk contents?
EDIT: nevermind I just added nautilus /media/disk to the script works great

---

