---
title: "Force mount left drive unusable -- I did a bad thing...."
date: 2008-04-05
forum: General Help
---

### Post by rabidg00se on 2008-04-05
Hey all, I'm primarily a Windows user (which, as it turns out, is the source of all my troubles) and a huge Ubuntu newbie. Yesterday I was running a diagnostic test on my primary computer which left it out of commission for a while, so I hooked up my 1TB Acomdata external to my laptop, running Hardy. I got this:

> helmut@helmut-m140:~$ sudo mount /dev/sda1 /media/sda1/
[sudo] password for helmut:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
clicking on the 'Safely Remove Hardware' icon in the Windows
taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
your own responsibility. For example type on the command line:

mount -t ntfs-3g /dev/sda1 /media/sda1/ -o force

(I copied that from a Google hit, so the directories may not have been the same.)

Being of the "hey, if I can do it I can undo it" mentality (and I *do* have Windows, so I'm really not quite sure what I was thinking), I of course forced the mount. I got a 'log file has been cleared' message, the drive mounted, I did what I had to, and shut down.

Now the drive is inaccessible through my Vista install, which I had expected (and expected to be able to fix somehow). What I hadn't expected was that now Ubuntu doesn't recognize it at all. It's currently plugged in, and the Computer screen shows a "USB Drive" that it can't mount. Worse, I have two partitions on it (a 15GB ext3 one for when I want to boot Ubuntu on my main computer and the rest of it is [was?] formatted NTFS), and neither of them are showing up.

I've got a LOT of data on this thing, please help!

---

### Post by rabidg00se on 2008-04-05
Oh, there's more. When I try to boot the Ubuntu partition, GRUB returns "Partition table corrupt or invalid." On top of that, the damn drive is clicking. IT'S CLICKING. This is not a good day for this hard drive.

---

### Post by rabidg00se on 2008-04-07
Bump, please help.

---

### Post by vanadium on 2008-04-08
If you attempt any repair, try it with Windows and Windows tools. You should realize that ntfs is a proprietary file system. Any code in Linux was reverse engeneered. The only operating system that knows all ins and outs of ntfs is MS Windows. Thus, you should first of all use Windowes tools to attempt repairing that drive or recovering data from it.

---

