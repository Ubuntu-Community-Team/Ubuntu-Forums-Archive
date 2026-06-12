---
title: "Need help: X wont load when copying edgy from one partition to another"
date: 2006-11-01
forum: General Help
---

### Post by hexion on 2006-11-01
Need guru's guidance out there ;)

I have 2 HDDs, /dev/hda (main) and /dev/sda.

/dev/hda5 => dapper
/dev/hda6 => /home (for dapper installation)
/dev/sda3 => edgy (it doesn't use /dev/hda6 for /home)

After dealing with all my edgy problems, mainly related to lirc and gnome's issues, I've decided to move edgy from my test partition to my main one. This is moving /dev/sda3 (except home) to /dev/hda5.

Ok, backed up dapper system and copied all folders and files from edgy partition to dapper one.
Adjusted /etc/fstab and /boot/grub/menu.lst to boot properly.

Now, there comes the problems....

When I boot my system (now it's edgy in /dev/hda5 with /home in /dev/hda6) I cannot enter X. It relies about permisions in ~/.rdst (or something like that) and when solving that, gdm will through an error about permisions to launch an app called mkdtemp.

I don't know why but when I copied folders from one partition to the other (being root) owners and permisions were changed :-?

I've tried to solve this situation with a chown -R user:user /home/user without success.
Then I even tried to change permisions with a chmod -R 644 /home/user. No success at all...

I also tried to use /home of my previous edgy installation and same errors.

I'm lost now. Please, anybody can send light on this before I restore my dapper backup? ](*,)

Thanks in advance.

---

### Post by jallain on 2006-11-01
I suggest you start over. I've had success using this method: mount you empty partition to your root partition. Then, issue the following command:
find . -xdev | cpio -padm /mnt (mnt being wherever you mounted your empty partition. Then modify fstab and grub to reflect the new partition. I moved an entire distro using this and had no problems.

---

### Post by hexion on 2006-11-01
> **jallain said:**
> I suggest you start over. I've had success using this method: mount you empty partition to your root partition. Then, issue the following command:
find . -xdev | cpio -padm /mnt (mnt being wherever you mounted your empty partition. Then modify fstab and grub to reflect the new partition. I moved an entire distro using this and had no problems.

What's that command for?

EDIT: Ok, nevermind, I've been reading man pages over the internet (I'm at work and I don't have access to a linux system here).
When I arrive at home I'll try that command.

Thanks for your help.

---

### Post by hexion on 2006-11-02
WORKED!!!

Thanks a lot, I'll keep that two commands in my mind :)

---

