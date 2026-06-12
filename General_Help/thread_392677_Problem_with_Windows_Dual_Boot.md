---
title: "Problem with Windows Dual Boot"
date: 2007-03-24
forum: General Help
---

### Post by Zeromark on 2007-03-24
Okay, first off, if this is in the wrong section, my sincerest apologies.

Next, I'm just starting to learn Linux, so unfortunately, I'm still getting familiar with how all this works. I appreciate any help you all can give, but please don't get too technical on me.

After toying with the Live CD for a few weeks, I decided to put Ubuntu on, at least as a back up. I ran through the install process, and sectioned off around 11 GB for Ubuntu.
After I run through the first boot and and the system updater, I restart to go back and make sure Windows XP Pro will boot successfully.

It won't. All that shows is "Starting up..." 
And nothing happens. The hard drive light is off, and  my computer's fans are on a lower speed, suggesting no activity. It's likely that the system's in a blank infinite loop, but that's just a theory.

Regardless, I've poked around Google for similar problems, and it may have something to do with the menu.lst file. At the end of my particular file it reads: 

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Any ideas?

---

### Post by Lord Illidan on 2007-03-24
Can you verify that /dev/hda1 still exists and contains a windows partition? Can you post the output of ```
cat /proc/mounts
``` here please?

---

### Post by Zeromark on 2007-03-24
Hda1 still does exist, but I'm not sure how to check if it still contains Windows. I'm pretty sure it should. 

[[IMG]http://img81.imageshack.us/img81/528/screenshotdevfilebrowsewe5.th.png[/IMG]](http://img81.imageshack.us/my.php?image=screenshotdevfilebrowsewe5.png)

As for the /proc/mounts - 

rootfs / rootfs rw 0 0
none /sys sysfs rw,nosuid,nodev,noexec 0 0
none /proc proc rw,nosuid,nodev,noexec 0 0
udev /dev tmpfs rw 0 0
/dev/hda2 / ext3 rw,data=ordered 0 0
/dev/hda2 /dev/.static/dev ext3 rw,data=ordered 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /lib/modules/2.6.17-11-generic/volatile tmpfs rw 0 0
tmpfs /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw 0 0
usbfs /dev/bus/usb/.usbfs usbfs rw 0 0
udev /proc/bus/usb tmpfs rw 0 0
usbfs /proc/bus/usb/.usbfs usbfs rw 0 0
tmpfs /var/run tmpfs rw,nosuid,nodev,noexec 0 0
tmpfs /var/lock tmpfs rw,nosuid,nodev,noexec 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0

---

### Post by Lord Illidan on 2007-03-24
But are you mounting it? In the code you posted above, it is not mounted..

---

### Post by Zeromark on 2007-03-24
Forgive my naivete, but I'm not familar with the mount command.

---

### Post by smokey edgy on 2007-03-24
Zeromark:

No problem. The mounting command attaches other filesystems to the current filesystem. You might want to try this:

1. Open up a terminal window (so you can get a command shell).
2. Type in these commands one after the other:

mkdir winxp
sudo mount -t ntfs /dev/hda1 winxp
sudo nautilus winxp &

A file browser showing the contents of winxp should show up soon after that. If it does, what do the contents show?

smokey edgy

---

### Post by Zeromark on 2007-03-24
Okay, now I've got a different problem.
I've followed the commands above, but it's asking for a password.
I've entered my standard windows logon password, but it's not taking it. If I had to guess, it wants the administrator account password - which I have at home.

So, I'll need to make a few phone calls, and I'll get back to you.
Thanks for the help so far.

---

### Post by qamelian on 2007-03-24
The password request is the result of the sudo command which is being used to give you temporary admin permissions in Ubuntu. The password it want is the password for your Ubuntu user account.

---

### Post by confused57 on 2007-03-24
> **Zeromark said:**
> Okay, now I've got a different problem.
I've followed the commands above, but it's asking for a password.
I've entered my standard windows logon password, but it's not taking it. If I had to guess, it wants the administrator account password - which I have at home.

So, I'll need to make a few phone calls, and I'll get back to you.
Thanks for the help so far.

You might want to make a copy of the Super Grub Disk(approx. 500 kb download):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
SGD is able to boot Windows or Linux, as well as restore Windows IPL code or grub to the mbr

Here's an excellent guide for mounting various filesystems:
[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

It may not make a difference for your Windows menu.lst entry, but you might try:
rootnoverify (hd0,0)

and some people have needed to remove the line with "savedefault"

You can try this as a temporary "fix", by highlighting your Windows entry in the grub menu at boot, press "e" to edit, make the changes, then press "b" to boot...this will determine if this will work.

---

### Post by Zeromark on 2007-03-25
Okay, here's what I got by running the terminal commands.
A window popped up with my WinXP files, and this message came up in the terminal

> zeromark@zeromark-desktop:~$ 
(nautilus:5695): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.



I also ran the Super Grub Disk, but it wasn't able to boot windows either.
I tried editing the grub menu as you suggested, but no dice.

---

### Post by confused57 on 2007-03-25
If you want to restore Windows IPL to your mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Hopefully, this will enable you to boot Windows.

If you want to try to reinstall grub, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

