---
title: "Every time I copy files to usb key and try eject after it &quot;Failed to Eject&quot;"
date: 2013-04-29
forum: General Help
---

### Post by finny388 on 2013-04-29
xubuntu 12.04
using Thunar 1.2.3
I copy a file from hard drive to usb key
When it finishes, I want to eject so I click the eject button and Thunar states:
```
Failed to Eject
Failed to eject medium; one or more volumes on the medium are busy..
```
and a notification pops up stating:
```
Writing data to device
There is data that needs to be written to the device "FILES" before it can be removed. Please do not remove the media or disconnect the drive
```

I've tried restarting Thunar but it doesn't help.
Only thing that seems to allow ejection is to reboot. I know the file is finished copying because it opens and is same size as original.

Why won't thunar or whatever file-copying utility does the copying release the drive?

thanks

---

### Post by BlinkinCat on 2013-04-29
Hi,

I believe you will find that you need to unmount USB before you can eject it.

Hope that helps.

---

### Post by finny388 on 2013-04-29
Thank you for the reply but it didn't help.
I think the Eject button should unmount or what is the button for?

Regardless, I went to Settings/Disk Utility, selected the drive and clicked the Unmount Volume button.

An error popped up:> Error unmounting volume
An error occurred while perfoming an operation on "FILES" (Partition 1 of Verbatim STORE N GO): The device is busy
Details> Cannot unmount because file system on device is busy

It may be interesting to note that in /media there is both a FILES and a STORE N GO mounted. But they are one and the same and Thunar only shows FILES.

I tried in terminal with sudo umount /media/FILES but same error
> umount: /media/FILES: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))

i tried typing lsof(8) in terminal but wasn't recognized

Is there a way to see what is keeping the drive busy?

---

### Post by BlinkinCat on 2013-04-29
All I know is that I used Disk Utility to unmount my USB's in 12.04 - then I could eject them.

Other than that I can't help.

---

### Post by r.stiltskin on 2013-04-29
When you get that message "Failed to eject medium; one or more volumes on the medium are busy.."
open a terminal and run this command:

**lsof | grep "/media"**

& see if you can tell from the output which process is using a file on the usb key.

---

### Post by BlinkinCat on 2013-04-29
Do you get an option to unmount if you right click on Store N Go?

---

### Post by finny388 on 2013-04-30
> **r.stiltskin said:**
> When you get that message "Failed to eject medium; one or more volumes on the medium are busy.."
open a terminal and run this command:

**lsof | grep "/media"**

& see if you can tell from the output which process is using a file on the usb key.

one line refers to FILES:
```
tumblerd  11335      finny   10r      REG       8,33  1478387712         95 /media/FILES/20130202.avi
```

upon googling tumblerd it appears to be a bothersome thumbnail generator [http://askubuntu.com/questions/89826/what-is-tumblerd]("http://askubuntu.com/questions/89826/what-is-tumblerd")
"And the damn thing can lock your USB drive..."

would you recommend uninstalling tumblerd?

---

### Post by r.stiltskin on 2013-04-30
No.  There are a few bug reports related to this.  According to this one on [=&sev[0]=&pri[0]=&due[0]=&reported[0]=&cat[0]=&status[0]=open&percent[0]=&opened=&dev=&closed=&duedatefrom=&duedateto=&changedfrom=&changedto=&openedfrom=&openedto=&closedfrom=&closedto="]bugs.archlinux]("https://bugs.archlinux.org/task/26707?string=tumbler&project=1&type[0) the problem seems to be a mistake in tumblerd's dependencies.  It seems to be missing one or more of gstreamer0.10-plugins.  Try installing gstreamer0.10-plugins-good.

sudo apt-get install gstreamer0.10-plugins-good

---

### Post by finny388 on 2013-04-30
thanks for the reply and link
I'll try the install tonight some time.

btw, what version of xubuntu are you running?

---

### Post by r.stiltskin on 2013-04-30
My main desktop now is running Xubuntu 12.10.  I've never had a problem like yours, but that may be because I've routinely installed alll of the gstreamer0.10 plugins on all of my Linux machines for years.

So I have Thunar on this machine & it "works", but I've never liked it so I use Nautilus (configured for "no-desktop").

---

