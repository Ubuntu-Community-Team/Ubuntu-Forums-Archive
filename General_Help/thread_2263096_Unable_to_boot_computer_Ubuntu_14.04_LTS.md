---
title: "Unable to boot computer Ubuntu 14.04 LTS"
date: 2015-01-29
forum: General Help
---

### Post by patagriff253 on 2015-01-29
Upon trying to boot my laptop I received the message "Error: Failure-Attempt to read outside disk HD00"

I booted the computer from a DVD and tried to use boot-repair, reinstalling GRUB, but I still get the same message. 

Running from the DVD, I've attempted to save a few files to a flashdrive before I reinstall the operating system, but of course, I don't have the necessary permissions to access the files.

Is there a way around this?

Anyone have a recommended course of action other the reinstalling the OS?

Boot information summary can be read at [http://paste.ubuntu.com/9939816/](http://paste.ubuntu.com/9939816/)

---

### Post by yancek on 2015-01-29
> I booted the computer from a DVD and tried to use boot-repair, reinstalling GRUB, but I still get the same message. 

Your boot repair output shows the message below.  You selected NOT to do anything other than produce this script so no change was made.  Don't know if it will work but it isn't working now so not much to be lost. 

> =================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



No change has been performed on your computer.

Running from a Live CD to access and move files, you will need root or sudo permissions.  So if you want to copy files from your hard drive, 
first create a mount point, then mount sda1 there and copy the files to the other medium.

---

### Post by patagriff253 on 2015-01-29
Create a mount point? I don't understand.

How do I give myself root permissions?

---

