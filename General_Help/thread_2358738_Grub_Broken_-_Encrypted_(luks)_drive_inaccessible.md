---
title: "Grub Broken - Encrypted (luks) drive inaccessible"
date: 2017-04-16
forum: General Help
---

### Post by patrick550 on 2017-04-16
Hi,

I have a Dell Precision 5510 laptop.  My hard-drive is encrypted and Grub broke (apparently).  When I boot up the machine asks me if I want to boot into Ubuntu 16.04 (the only installation on this machine) and when I say yes, the screen goes black and the caps lock starts blinking (normally, I would get the password prompt for decrypting the drive.)

I would like to (best case) be able to fix grub or whatever is causing the laptop not to boot right now or (worst case) be able to retrieve my files (possibly by booting via a live-CD).  

I can't figure out what to do (newbie) in order to fix grub (seems that this is a fairly rare setup with encryption(?).  
 
On Option 1: I attempted to make changes and fix grub ([http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd))  but I have issues with permissions with the Live CD, can't get sudo access and none of my research has yielded any workable password.

In order to attempt to fix option 2, I was able to boot from a LiveCD and then open the encrypted drive but I can't move any of the files because I don't have permissions and can't figure out how to get ubuntu to prompt me for the password in order to access my home folder/directory.  Note: I thought I figured out how to get ubuntu to prompt me for a login but when I do, I'm missing a package and wifi is HARD OFF (don't know why, there's no switch on the laptop and wifi is on in BIOS.  What else could there be?

I've spent hours researching this and everything I've run into is a dead-end.  The encryption of the drive makes the whole problem much more complex (IMHO).  Again, the best situation would be fixing grub but I'll be delighted with either solution, I need to get this laptop back up and running again!

In advance thank you for you any insight you might have.

Patrick550

---

### Post by oldfred on 2017-04-16
I do not know LVM nor encryption.

But if you get to grub menu then grub actually is ok.
And then if system is not booting, it may be just corruption on your drive that needs fsck to fix.
Did you have or cause an abnormal shutdown? That can corrupt data.

Your instructions were for a  standard chroot. But you have LVM & encryption and have to mount the LVM and decrypt drive.

Instructions are older but still valid for BIOS installs. If UEFI you may have to add mounting that.
Run the 4 steps on these instructions before the resize until where it says you can manage partitions. You then may need fsck.
 How to: Mount & Resize an Encrypted Partition (LUKS) also mount for repairs
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641) 

 fsck on encrypted LUKS 
[http://serverfault.com/questions/375090/using-fsck-to-check-and-repair-luks-encrypted-disk](http://serverfault.com/questions/375090/using-fsck-to-check-and-repair-luks-encrypted-disk)

---

### Post by patrick550 on 2017-04-23
Thank you for your response!  I had a crazy work week and didn't get a chance to look at this until now.  

I've now been able to use Ubuntu Live CD as well as the directions contained in the links to connect to the encrypted partition from the terminal.  However, when I run fsck:

```
sudo fsck -C -V -y /dev/mapper/crypt1 
```

I get this output:

```
fsck from util-linux 2.27.1 
```

That's it.  Nothing else.  I researched on Google but can't find anything in this regard.  Note: it does not matter what fsck command I issue, I always get the same output (see line above)

Any ideas?  If not, how can I provide the proper password for my home directory so that I can backup the files in that folder?  

Thank you!!!

---

### Post by oldfred on 2017-04-23
Is this actually the LVM partition?
/dev/mapper/crypt1
I have seen this:
 /dev/mapper/ubuntu--vg-root 

If you correctly mounted it and unencrypted it, you should see all your data.

But all I really know is that those who know about LVM & encryption say you must have really good backups procedures.

---

### Post by patrick550 on 2017-04-23
That was it:  /dev/mapper/ubuntu--vg-root (I should have run lsblk command)

BUT it tells me that it's clean.  So why can't I boot from it?  Why don't I get a prompt for the password from LUKS?

In addition, when logged in via LiveCD I can see my data, except that since I'm not logged in as my regular user, I can't see anything in my home folder.  In other words I can see all the folders on the drive but my own folder is locked.  

What would you do if you were in my shoes?

Thanks again!

---

### Post by oldfred on 2017-04-23
I do not think you did the steps to unencrypt your data. You are just seeing the default partitions.
[https://ubuntuforums.org/showthread.php?p=4530641](https://ubuntuforums.org/showthread.php?p=4530641)

---

### Post by patrick550 on 2017-04-23
I believe I did the steps.  It asked me for the password to decrypt the drive and I can see all of the folders on the drive.  I can see the contents of the /etc folder.  I can see the contents of the /home folder but I can't get to the contents of the /home/myuser folder because that folder requires a login but I don't know how to login and can't find any information about this online (probably not doing the correct search but not sure what that would be).

That being said, I just looked in the boot for the encrypted partition (/media/ubuntu/f1ea2039a-5a4c-47af-b62d-6293222932/boot) and it's empty!  Looking to see how to recreate the boot files ...

---

### Post by oldfred on 2017-04-23
That boot is normally empty as you have the /boot as a separate partition outside the LVM.

You have your normal login password, but to get the the .encrypt folder to open you have to use your passphase.

---

### Post by pete-br on 2017-04-26
From the Live CD you can Chroot into your installed Linux and from there repair your Grub configuration.
You should use the same Live CD as the version of Linux you have installed.

Mount your encrypted partition to /target.
then mount more stuff:
mount --bind /dev /target/dev
mount --bind /proc /target/proc
mount --bind /sys /target/sys
finally you can chroot into your installed Linux:
chroot /target

Look in /etc/default/grub.
It should contain an entry:
GRUB_ENABLE_CRYPTDISK=y
Maybe you will need to make more changes, I can tell.
Check what you need to check, change what you need to change.

To finalize the changes, execute:
update-grub

---

