---
title: "Problems copying data from old internal hard drive"
date: 2016-08-10
forum: General Help
---

### Post by goemonburo on 2016-08-10
I recently switched from Fedora 13 to Lubuntu 16.04 LTS.  Very happy with it overall and have Lubuntu 12.x LTS on a different machine.

At the time of upgrade, I went ahead and got a new hard drive, so this is a totally fresh install.

Having a strange problem copying data from my old (internal) hard drive though, which had full disk encryption.  I know the passwords and have attached it via USB.  I'm then prompted to unencrypt the drive, then unencrypt the /home/myhomedir partition.  

I've then used "rsync -a /my/old/internal/harddrive/home/myhomedir/ /home/mynewhomedir/" to copy over info.

Problem 1: rsync, usually incredibly reliable, seems to be stopping part of the way through.  Just hanging.  Often with a lot of I/O errors.

Problem 2:  Possibly connected, despite choosing "Remember forever" when I type in the passwords, I get prompts for the password again.  Often this is met with a long error saying that it can't connect because the drive has the wrong fs type or something (sorry, don't have the exact error on hand...)

Problem 3:  I can't seem to get the drive to reset at all.  Even if I unplug it completely from the computer, my file manager still shows the drives as options in the file list, often with the "unmount" arrows there.  If I try to unmount I get something like "cannot perform because action pending"

Problem 4:  POSSIBLY related, if I try to reboot the computer without the drive attached (since it also has a boot partition and I don't want the now-external drive getting confused with the new INTERNAL one...), I get prompted for the new drive's boot encryption password, then it pops me to an emergency shell, with "journalctl" as my option.  This is a bigger issue since once it happens, I've got a bricked computer.  No clue how to fix it other than to reinstall from scratch.  It was only this morning, at work, that I thought of trying to boot the system with the old hard drive still attached, that perhaps that's causing the issue...will try tonight.

I believe, perhaps, that something's going wrong with fstab, and maybe this drive is being seen as permanent or internal or something like that?

Anyone out there know what I can do?  It's probably useful to note that there's nothing faulty with the old hard drive.  It works fine if I plug it back in as the main internal drive and start up...boots into Fedora 13 without any issues at all.

Basically I just want to copy my old data to the new drive and disconnect it.  Seems like this should be fairly straightforward, but I guess I'm either doing something wrong or it's not as simple as I thought it would be!!!

Thank you!!!!!

---

