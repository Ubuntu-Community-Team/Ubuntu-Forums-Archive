---
title: "Deleting File on HD from LiveUSB (Ubuntu does NOT boot)"
date: 2018-09-18
forum: General Help
---

### Post by antisthenes2 on 2018-09-18
I created a file (see [https://ubuntuforums.org/showthread.php?t=2400260&p=13801575#post13801575](https://ubuntuforums.org/showthread.php?t=2400260&p=13801575#post13801575)), which is causing Ubuntu not to boot properly; upon startup, the screen starts tearing and remains so until I force shutdown the computer.

I can access the hard disk (on which this file is stored) by booting from a LiveUSB, but I'm unable to  delete the problematic file because the access is read-only.

How can I get the necessary permissions to delete the file?

---

### Post by ajgreeny on 2018-09-18
Here is the text of your original post, and please do not create near duplicate threads about the same problem.
> So, I created an xorg.conf file and placed it in /etc/X11. In the file, I added only this line: Option "HWCursor" "off", which, from what I've read, is what disables the hardware cursor. I restarted the computer, and now Ubuntu does not load (during the boot, the screen tears and stays like that).

I can access the hard disk by booting from a LiveUSB, but I'm unable to delete the problematic file because I do not have the necessary permissions. How can I get the necessary permissions, and how can I disable the hardware cursor correctly? 
You should be able to boot to your installed Ubuntu system and at the login page hit Ctrl+Alt+F2 to get a tty command line.
Login there with username and password (password will not show on screen so type carefully and hit Enter).
From that screen rename the errant xorg.conf file with ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
``` then reboot with ```
shutdown -r now
```
Hopefully you will now get to normal GUI login.

---

### Post by antisthenes2 on 2018-09-18
> **ajgreeny said:**
> please do not create near duplicate threads about the same problem.

Apologies for doing so; it's just that the issue is quite urgent, and it didn't seem that I would get a response in my original thread.

> **ajgreeny said:**
> You should be able to boot to your installed Ubuntu system and at the login page hit Ctrl+Alt+F2 to get a tty command line.

I never reach the login page. The system boots, but there is no Ubuntu splash screen -- just some screen tearing, which eventually stops and remains so. I tried the Ctrl+Alt+F2 key combination to no avail.

Could you please advise me on what to do next?

---

### Post by deadflowr on 2018-09-18
If you need to do it from the live session (dvd cd or usb)
you need to mount the hard drive first, then run sudo command to remove
linux has empty directories to mount to, for this exact purpose.

Personally since you'll need to run successive sudo command I invoke sudo's interactive mode
```
sudo -i
```
then run something like
```
parted -l
or blkid
```
to find which partition my system is on.
Once located I run
```
mount /dev/sdXx /mnt
```
replace the Xx with the letter id and number id of the partition I need to mount.
when mounted, cd into the directory I need to.
(In this case the /mnt/etc/X11 directory)
```
cd /mnt/etc/X11
```
then run remove or move command to move (rename) or remove (delete)
```
rm xorg.conf
or 
mv xorg.conf xorg.conf-backup
```
then to clear out I can cd back to the main directory
```
cd 
```
then unmount the hard drive
```
umount /mnt
```
when done simply type
```
exit
```
to end the interactive session.
Then I can try rebooting and see if you can log into the hard drive install.
That's what I would do.

If you need help figuring out the partition you need to mount post back the parted -l and blkid commands outputs.
There are exceptions to the generic /dev/sdXx locations, such as nvme ssd drives and lvm which have there own naming schemes that differ.
So if either of those are the partition's scheme it might require a different name or set of commands to use.

---

### Post by antisthenes2 on 2018-09-19
Thanks! Your instructions worked.

**Any idea how I can solve my original problem, namely disabling the hardware cursor?** As a reminder, redshift (the colour temperature adjustment tool) doesn't affect the  colour of my mouse cursor. The issue seems to be that  the graphics  driver is configured to use hardware cursors. According to  the redshift  website, some graphics drivers have an option to disable  hardware  cursors in xorg.conf.

My GPU is an NVIDIA GeForce 9400M and the driver is the open source  X.Org X server nouveau (the other (proprietary) drivers that are  available for this GPU do not work well; only the open source one does).

---

### Post by antisthenes2 on 2018-09-23
Bump.

---

### Post by deadflowr on 2018-09-23
To know what the issue was that was causing the problem you'll need to post the xorg.conf file you created.
As not many psychics populate these forums.
So we don't know what or where in the file you erred, or if you erred.

---

### Post by antisthenes2 on 2018-09-23
In the OP, I provided a link to the original thread describing what I did, namely "I created an xorg.conf file and placed it in /etc/X11. In the file, I  added only this line: Option "HWCursor" "off", which, from what I've  read, is what disables the hardware cursor."

---

### Post by deadflowr on 2018-09-23
But you never posted the actual xorg.conf file which would help a lot.

---

### Post by antisthenes2 on 2018-09-23
What I explained in my previous post is exactly what the file is. I used the text editor to create a new file, in which I simply added that line, saving it as xorg.conf in /etc/X11. There's nothing more to the file.

---

### Post by antisthenes2 on 2018-10-04
If you really consider the file necessary, I may upload it, though I'm not sure how; the file extension (.conf) isn't considered valid under "Manage Attachments:".

---

### Post by jeremy31 on 2018-10-04
Just paste the contents of that file using code tags

---

### Post by antisthenes2 on 2018-10-06
Here is all that is written in the xorg.conf file that I created:

```
Option "HWCursor" "off"
```

---

### Post by deadflowr on 2018-10-07
So missing context and syntax.
xorg.conf files require certain syntax and not just random commands.
All things are required to be placed with sections (and each section encapsulated with an endsection.)

So basically you make a file with this
```
Section "Device"
Identifier "Nvidia 9400"
Driver "nouveau"
Option "SWCursor" "true"
EndSection
```
and place in a file in /etc/X11/xorg.conf.d.
name the file something like 20-something.conf
Note if the xorg.conf.d directory does not exist, just create it with
```
sudo mkdir /etc/X11/xorg.conf.d
```
Quick reference here:
[https://www.reddit.com/r/linuxquestions/comments/21h663/question_can_i_set_my_cursor_to_be_a_software/]("https://www.reddit.com/r/linuxquestions/comments/21h663/question_can_i_set_my_cursor_to_be_a_software/")


See if that helps at all.

---

### Post by antisthenes2 on 2018-10-07
Yes, it did! Thank you!

Unfortunately, a new issue has arisen. My mouse cursor is now constantly flickering and at times disappearing, as well as moving on its own.

How can I fix this?

---

### Post by oldos2er on 2018-10-08
> **antisthenes2 said:**
> Yes, it did! Thank you!

Unfortunately, a new issue has arisen. My mouse cursor is now constantly flickering and at times disappearing, as well as moving on its own.

How can I fix this?

Please create a new thread for your new question.

---

