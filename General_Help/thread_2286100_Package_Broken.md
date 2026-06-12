---
title: "Package Broken"
date: 2015-07-09
forum: General Help
---

### Post by ccbmailroom on 2015-07-09
I just tried to update Ubuntu 14.04 LTS and twice I got a package broken.  Now Ubuntu will not load up.  I get a curser underline in the upper left corner of the screen.  Any thoughts?  

I'm needing my files/documents as I've recently over the past couple of months reinstalled Ubuntu from the login loop issue where I couldn't get past that screen.  I am in serious need of getting my

---

### Post by ccbmailroom on 2015-07-09
..well that post didn't work.  I'm needing my files off the OS.  I'm needing to back up everything to put Windows 8 back on the laptop as Ubuntu will not work and has not worked as a reliable laptop since it was imaged last summer.  Run time on the OS has always been off and there has been very little help in the forums.  Any help would be GREATLY appreciated, thank you.

---

### Post by Frogs Hair on 2015-07-10
Post the output of the following terminal command .```
sudo apt-get update 
``` 

Try This:   ```
sudo apt-get -f install
```

---

### Post by ccbmailroom on 2015-07-11
> **Frogs Hair said:**
> Post the output of the following terminal command .```
sudo apt-get update 
``` 

Try This:   ```
sudo apt-get -f install
```

As I stated in the first post, no option to type anything.  There is an underscore curser in the upper left corner of the screen.  I did find something at help.ubuntu.com/community/LiveCDRecovery where it gave these instructions

sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
(((at this stage I get an error that states "chroot: cannot run command '/bin/bash':Exec format error)))
apt-get update
apt-get upgrade

Apart from getting the error, I still cannot access my laptop.

My laptop came back up in June after having crashed a few months back due to the login loop issue.  It was nice to have it working again, I'm just very tired of the unreliability Ubuntu has been on this laptop.  It's truly disappointing.

---

### Post by ian-weisser on 2015-07-11
Are you using the correct 32-bit/64-bit LiveMedia to match your  installed system? They needn't match for mounting and copying. They must  match for chrooting.

If you just want to recover your files, boot your LiveMedia, mount the hard drive (you did that in the previous post), and copy your data to a different media.

As you surely figured out already, a 'login loop' means the X server was crashing, and the X server logs in /var/log will usually tell you why.

An unusable blinking cursor on an otherwise blank screen usually means that the kernel has loaded and works, but the rest of initrd (which uses the kernel to load the system) does not contain the instructions to load the system (or they are unreadable). The specific error you cite ('/bin/bash':Exec format error) has several possibilities, [explained on this AskUbuntu thread]("http://askubuntu.com/questions/14280/during-a-chroot-attempt-i-got-this-error-chroot-failed-to-run-command-bin").

---

### Post by Frogs Hair on 2015-07-14
Excuse me , I was thinking of broken package indicator which would appear on the right side of the panel if it had appeared. Is this a partitioned dual boot or a Wubi installation ?

---

