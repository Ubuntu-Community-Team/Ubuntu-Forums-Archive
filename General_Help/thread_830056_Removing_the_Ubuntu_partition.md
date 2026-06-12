---
title: "Removing the Ubuntu partition"
date: 2008-06-15
forum: General Help
---

### Post by dropscience on 2008-06-15
Hi, i would want to remove the Ubuntu partition from Windows Xp, since i cannot boot into Ubuntu, but without killing the boot loader. I have the two operating systems installed on different hard drives and i want to format the one with Ubuntu on. How can i do this without risking to mess up the boot loader. 

Thx beforehand!

---

### Post by Joeb454 on 2008-06-15
Do you have a full Windows XP install disc? If you do, it will make things a little easier

---

### Post by dropscience on 2008-06-15
Yes of course i have

---

### Post by Joeb454 on 2008-06-15
Ok, just checking :)

You could use the Live CD to delete Ubuntu, and then pop in the XP disc, and get into the Recovery Console, and type ```
fixmbr
``` Which should restore the XP bootloader :)

Or I believe you could use SuperGrubDisk :)

---

### Post by vexorian on 2008-06-15
Edit: god I am slow.

What boot loader? Grub? If it is grub then it is not hard since you will remove ubuntu anyway. If it is windows' boot loader, then don't worry. If you have another Linux distribution / OS, ignore this post:

- Boot windows XP, then go to the control panel, "administrative tools"
- Find the part that says disks.
- Now it should show your disks and partitions, it should be  clear which one is ubuntu, if you are not sure, post a screenshot here so we can help you.
- Take ubuntu's partition and tell the administrative tool to format it for windows, use NTFS, etc...

Now, you will NOT be able to boot windows yet, you need to restore windows' boot . For this you must use the windows XP installer CD, when you are giving the option to press "r for recovery console" press R. Put your XP administrator password and then, in the console type: "fixboot" (without the quotes)

---

### Post by dropscience on 2008-06-15
How exactly do i get into the Recovery Console, and what is Supergrubdisk? :)

---

### Post by dropscience on 2008-06-15
> **vexorian said:**
> Edit: god I am slow.

What boot loader? Grub? If it is grub then it is not hard since you will remove ubuntu anyway. If it is windows' boot loader, then don't worry. If you have another Linux distribution / OS, ignore this post:

- Boot windows XP, then go to the control panel, "administrative tools"
- Find the part that says disks.
- Now it should show your disks and partitions, it should be  clear which one is ubuntu, if you are not sure, post a screenshot here so we can help you.
- Take ubuntu's partition and tell the administrative tool to format it for windows, use NTFS, etc...

Now, you will NOT be able to boot windows yet, you need to restore windows' boot . For this you must use the windows XP installer CD, when you are giving the option to press "r for recovery console" press R. Put your XP administrator password and then, in the console type: "fixboot" (without the quotes)

I'm not sure i know of any XP administrator password. I am the administrator on this computer.

You mean that i should format the partition, so that everything on it is deleted. Then restart and restore the boot?

---

### Post by Joeb454 on 2008-06-15
When you boot the XP CD, somewhere it should mention about Recovering a broken install, which is what you need to choose.

[http://www.supergrubdisk.org](http://www.supergrubdisk.org)

---

### Post by vexorian on 2008-06-15
> **dropscience said:**
> I'm not sure i know of any XP administrator password. I am the administrator on this computer.

You mean that i should format the partition, so that everything on it is deleted. Then restart and restore the boot?
I think it depends on the service pack used when installing XP.

On service pack 2, windows XP asks you a password when you first install it, that's the administrator password, chances are that if you made the installation and you are the only user there, it is the same as your user password in XP.

---

### Post by dropscience on 2008-06-15
> **vexorian said:**
> I think it depends on the service pack used when installing XP.

On service pack 2, windows XP asks you a password when you first install it, that's the administrator password, chances are that if you made the installation and you are the only user there, it is the same as your user password in XP.

Ok, but is there any way to check what the password might be? I wouldn't want to remove Ubuntu and then not be able to boot into Xp. 

I don't have a user password, since i am the only user.

---

### Post by forestpixie on 2008-06-15
Before you start deleting partitions - boot with your xp disc - once it's finished doing what it needs see if you can get to the recovery bit - on 2k I believe it's R to repair, then you should get in - when it asks for a password try without or yours if you use one - as long as you can get to the command prompt you'll be able to do the fixmbr

Remove the disc, then get rid of the buntu partition and go through it all again.

Edit - alternatively you can repair win mbr from within linux

[http://ubuntuforums.org/showpost.php?p=3361231&postcount=2](http://ubuntuforums.org/showpost.php?p=3361231&postcount=2)

---

### Post by dropscience on 2008-06-15
Thank you, will do that first thing tomorrow morning!

---

