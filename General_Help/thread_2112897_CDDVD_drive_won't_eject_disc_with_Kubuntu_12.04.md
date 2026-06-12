---
title: "CD/DVD drive won't eject disc with Kubuntu 12.04"
date: 2013-02-06
forum: General Help
---

### Post by jhilp on 2013-02-06
I have an older Gateway computer with a CD writer/DVD player installed, and I just started using Kubuntu 12.04. After I insert a CD or DVD, I'm unable to eject it with the button on the drive. It sounds like it's spinning in there without stopping even though I'm not running the disk in a program. The only way I seem to be able to remove it is by restarting the computer and removing the disk as the computer boots up. I've been running standard Ubuntu 12.04 on this computer until recently, and never had this issue. Any thoughts? Thanks!

P.S. I just entered the command "eject" in the terminal, and it properly ejected the DVD media. However, after closing the tray, it won't reopen, so I entered the same command a second time, and received this response: 

john-hill@Gateway-E-4100:~$ eject
eject: unable to eject, last error: Inappropriate ioctl for device
john-hill@Gateway-E-4100:~$ 

Or maybe it's supposed to respond to that command like that, since there's no media in the drive?

---

### Post by carl4926 on 2013-02-06
If you are sure no application is still using it?

I have seen where users also have gnome applications installed such as Nautilus and when you originally insert the DVD/CD, Nautilus also takes hold of it.

---

### Post by jhilp on 2013-02-06
> **carl4926 said:**
> If you are sure no application is still using it?

I have seen where users also have gnome applications installed such as Nautilus and when you originally insert the DVD/CD, Nautilus also takes hold of it.
You may be right about that, but surely there's something I can do about it?  When I'm done using a CD or DVD i'd like to be able to remove it without restarting the computer.  I've never had this happen before.  Thanks!

---

### Post by carl4926 on 2013-02-06
> **jhilp said:**
> You may be right about that, but surely there's something I can do about it?  When I'm done using a CD or DVD i'd like to be able to remove it without restarting the computer.  I've never had this happen before.  Thanks!

Try running 'top' or the system monitor to see what is running that could possibly be responsible. Then kill the suspect app

---

### Post by SeijiSensei on 2013-02-06
"sudo lsof" is a better choice than top since it will list the applications with open files.  If you know the name of the mount point like /mnt/cdrom you can use "sudo lsof | grep cdrom" to extract just the relevant output.

lsof = "list open files"

But, to answer the original question, the operating system will usually lock the manual eject button if the drive is in use by some program.  In Kubutu, you can try clicking on the circular icon with the squiggle in the system tray to bring up the list of mounted devices.  There is a icon on the list to eject the medium from the drive.

Often I've found I either have a dolphin window open to the drive, or perhaps a terminal session where the current directory is one on the disc.

---

