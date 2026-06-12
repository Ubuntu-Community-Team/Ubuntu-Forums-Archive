---
title: "I borked sudo"
date: 2005-06-24
forum: General Help
---

### Post by JamesNorris on 2005-06-24
somehow, I managed to change the mode of /etc/sudoers to 0640, so now I can't sudo anymore. Is there any way I can fix this without reinstalling again...

---

### Post by nictuku on 2005-06-24
Here's one possible way.

While in the GRUB menu, press "e" to edit the boot parameters.

Insert "init=/bin/bash".

Press "b" to boot.

As far as I remember you will fall in limited shell with a read-only file system.[1]

Re-mount the filesystem as read-write: 
 
# mount -o remount,rw /

Change the permission you need and reboot.

----
[1] - Now, maybe this isn't true. Maybe it asks for root password, which is bad. In that case, you should boot using the Installation CD and go through the hardware detection steps.

Then, mount your old root filesystem from there, and fix your permissions

# mkdir /mnt
# mount /dev/hda1 /mnt

Probably there won't be a /dev/hda. You'll need to find where is your root partition. Come back with your achievements.

---

### Post by JamesNorris on 2005-06-24
Erm... I don't have a root partition. I just have a / and a /home one.

---

### Post by JamesNorris on 2005-06-24
[QUOTE=JamesNorris]Erm... I don't have a root partition. I just have a / and a /home one.[/QUOTE]


Although, that doesn't matter, cos I've fixed it using the first method... it didn't ask for a password :)

---

### Post by shakin on 2005-06-24
[QUOTE=JamesNorris]Although, that doesn't matter, cos I've fixed it using the first method... it didn't ask for a password :)[/QUOTE]

In the future, simply booting to the recovery console will likely work. I've never done it, but I assume it drops you into a single user system, so you'd be root. If it doesn't put you into single user mode, when you edit your grub, don't add 'init=/bin/bash'. Just add 'single' and it will boot you into single user mode.

---

### Post by shakin on 2005-06-24
FWIW, I always enable my root account just in case this happens. I manage servers remotely so I can't always get there to fix little problems like a borked sudo. I still use my system normally using sudo instead of su, but having su available is a good thing.

---

### Post by nictuku on 2005-06-24
[QUOTE=shakin]In the future, simply booting to the recovery console will likely work. I've never done it, but I assume it drops you into a single user system, so you'd be root. If it doesn't put you into single user mode, when you edit your grub, don't add 'init=/bin/bash'. Just add 'single' and it will boot you into single user mode.[/QUOTE]

I'm not sure. At least in my case, when I have a password set for my root accounts, it asks for root password when entering single user mode. That is true for Debian as well, just for the record. That's why one needs init=/bin/bash.

I may be wrong, though  :???:

---

### Post by az on 2005-06-24
[QUOTE=shakin]FWIW, I always enable my root account just in case this happens. I manage servers remotely so I can't always get there to fix little problems like a borked sudo. I still use my system normally using sudo instead of su, but having su available is a good thing.[/QUOTE]

Grub is installed with the single option already.  In the grub menu it is call recovery mode.  No need to enable root, or edit your menu list.  Just pick recoverymode and hit enter (If Ubuntu is the only OS on your computer, press ESC to reveal the grub menu on boot)

If you are running a remote box, of course, this is not an option.

---

