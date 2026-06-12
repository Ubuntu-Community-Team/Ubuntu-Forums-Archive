---
title: "Drive failing / system setup"
date: 2014-01-29
forum: General Help
---

### Post by prem1er on 2014-01-29
I'm currently running 12.04. The drive I use for /, /home and swap is failing and I'm having and more and more crashes. I'm going to be replacing the drive soon, but I want to know what my options are for reinstalling my system. I would like to avoid running through the setup process again and installing/configuring all my software that I'm currently using. Is there a way to backup my old system as a whole and basically transfer it to the new drive? Any suggestions are welcome. TIA.

---

### Post by erind on 2014-01-29
I've been using successfully ***fsarchiver*** to backup my OS Linux partitions and it doesn't have any limits on the destination's partition's size. Assuming your OS/data is on /dev/sda1 and you want to back it up to a file named "*distro_name.fsa*" on /mnt/backup:

```
sudo fsarchiver savefs /mnt/backup/distro_name.fsa /dev/sda1
```
And restoring it:

```
sudo fsarchiver restfs /mnt/backup/distro_name.fsa id=0,dest=/dev/sda1
```

[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)
[http://crunchbang.org/forums/viewtopic.php?id=24268](http://crunchbang.org/forums/viewtopic.php?id=24268)

I've also seen *Clonezilla *recommended, but it needs to have the same or bigger destination partition size than the original (source) one. 
Lastly you can just backup your /home directory, and certain files from /etc, /var and a few more, can't  remember all, and also a list of all of your installed programs and start fresh again.

---

### Post by prem1er on 2014-01-29
This is exactly the information I was looking for. Thank you. I'll look into what works best for me.

Edit: What about grub? Do I need to install again?

---

### Post by erind on 2014-01-29
Yes, simply run *Boot-Repair* (Live CD) after restoring the OS to the new partition. From the **fsarchiver**'s FAQs:

> Can the restored file-system be a boot filesystem (like the root partition) ?

Yes, FSArchiver can backup the root file-system, but you may have to run grub-installer again after you restore the file-system where the boot-loader (grub) is installed. FSArchiver has been successfully able to save and restore the root file-system of a Fedora-8 with SELinux on it as you can see in the status page. 

[http://www.fsarchiver.org/FAQ](http://www.fsarchiver.org/FAQ)

---

