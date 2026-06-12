---
title: "FStab broken"
date: 2023-01-31
forum: General Help
---

### Post by Phil Binner on 2023-01-31
I'm trying to install a couple of 2Tb hard drives as archives.  They are physically installed and I used GParted to delete all old partitions and install a new Ext4 partition on each.  I then edited FStab to mount them, using UUID=and the address from BLKID, etc.

I don't think I got that wrong, but that is a question for the future.  What is happening now is that I can't boot because there is something wrong with the mount.  I can boot from a flash drive, but that doesn't let me get at FStab to comment out the lines.  How can I get at FStab to sort this out.

Thank you in advance

Phil B

---

### Post by oldfred on 2023-01-31
Part of issue is that live installer is user 999 and install is user 1000, so permissions issue.
You can chroot into install.
UEFI chroot, must include ESP - efi system partition
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)

Can you boot recovery mode and get to terminal? Then you an edit fstab from there.
sudoedit /etc/fstab

---

### Post by TheFu on 2023-01-31
> **Phil Binner said:**
> I'm trying to install a couple of 2Tb hard drives as archives.  They are physically installed and I used GParted to delete all old partitions and install a new Ext4 partition on each.  I then edited FStab to mount them, using UUID=and the address from BLKID, etc.

I don't think I got that wrong, but that is a question for the future.  What is happening now is that I can't boot because there is something wrong with the mount.  I can boot from a flash drive, but that doesn't let me get at FStab to comment out the lines.  How can I get at FStab to sort this out.

Thank you in advance

Phil B

I take it you don't want to post the fstab so we can point out the issue?
If you boot into a "Try Ubuntu" environment, then you'll need to temporarily mount the file system with the installation /etc/ directory on it - I'd mount it to /mnt/ then use the "ubuntu" account in the "Try Ubuntu" environment with sudoedit to modify the fstab there.  If you did an install with LUKS and/or LVM2, then things are just a little harder, but not too much for someone with your skills.  Run
```
lsblk -e 7 -o name,size,type,fstype,uuid,mountpoint
```
to see all the file systems.  If no LVM LVs are showing, run 'sudo vgchange -ay' for the OS to activate them (let the OS know they exist), then do the lsblk command above again.

---

### Post by Phil Binner on 2023-01-31
I have no problem posting the other stuff as soon as I have access to it.  I'm just trying to access the problems one at a time.  I'm fairly sure it's the drives or the partitions that are the problem, not the line in FStab.  Still, that is to be established.

Anyway, there are a couple of things to try tomorrow.  I'm guessing I'm several hours ahead of you.

Thanks for your help.

---

### Post by ajgreeny on 2023-01-31
For the future, it is always worth running command ***sudo mount -a*** after editing fstab.
That will attempt to run all the mount commands given in that file and you will immediately be shown errors if there are any problems after your edit.

No need to reboot so you will not be locked out of your computer and can remove or content the edit you made from your still running OS.

---

### Post by Phil Binner on 2023-02-01
I think you may be overrating my talents.  I have had to learn a few specific things, but the breadth of my knowledge is limited.  

When I attempt to boot into recovery mode I get a message "you have to load the kernal first", so that doesn't work.  I followed the link to booting into EUFI mode, and I don't see how to apply it.  The only way I can get to a terminal is by booting from a flash drive.

I then ran the lsblk commands.  This is the outcome:

```
xubuntu@xubuntu:~$ lsblk -e 7 -o name,size,type,fstype,uuid,mountpoint
NAME     SIZE TYPE FSTYPE  UUID                                 MOUNTPOINT
sda      1.8T disk                                              
&#9492;&#9472;sda1   1.8T part ext4    1cc344c9-9b5a-4493-878c-e2f60a25017d
sdb    111.8G disk                                              
&#9500;&#9472;sdb1     1M part                                              
&#9500;&#9472;sdb2   513M part vfat    3393-404A                            
&#9492;&#9472;sdb3 111.3G part ext4    dc1983f5-b91e-4f47-9d52-80a9aae80ed6
sdc     14.6G disk iso9660 2022-08-10-18-35-19-00               
&#9500;&#9472;sdc1   2.3G part iso9660 2022-08-10-18-35-19-00               /cdrom
&#9500;&#9472;sdc2   4.1M part vfat    8D6C-A9F8                            
&#9500;&#9472;sdc3   300K part                                              
&#9492;&#9472;sdc4  12.3G part ext4    e4c77008-a3fb-44d0-ba1c-7495bc528293 /var/crash
sr0     1024M rom                                               
xubuntu@xubuntu:~$ ^C
xubuntu@xubuntu:~$ sudo vgchange -ay
xubuntu@xubuntu:~$ lsblk -e 7 -o name,size,type,fstype,uuid,mountpoint
NAME     SIZE TYPE FSTYPE  UUID                                 MOUNTPOINT
sda      1.8T disk                                              
&#9492;&#9472;sda1   1.8T part ext4    1cc344c9-9b5a-4493-878c-e2f60a25017d
sdb    111.8G disk                                              
&#9500;&#9472;sdb1     1M part                                              
&#9500;&#9472;sdb2   513M part vfat    3393-404A                            
&#9492;&#9472;sdb3 111.3G part ext4    dc1983f5-b91e-4f47-9d52-80a9aae80ed6
sdc     14.6G disk iso9660 2022-08-10-18-35-19-00               
&#9500;&#9472;sdc1   2.3G part iso9660 2022-08-10-18-35-19-00               /cdrom
&#9500;&#9472;sdc2   4.1M part vfat    8D6C-A9F8                            
&#9500;&#9472;sdc3   300K part                                              
&#9492;&#9472;sdc4  12.3G part ext4    e4c77008-a3fb-44d0-ba1c-7495bc528293 /var/crash
sdd        2G disk                                              
&#9492;&#9472;sdd1     2G part vfat    BC99-83F8                            /media/xubuntu/S
sr0     1024M rom 
xubuntu@xubuntu:~$


```

The system is instaqlled to a 120G SSD, which is on SDB.  I don't see anything regarding LVM or LV in the output.

Where do I go from here.

I do have the option of just reinstalling the software.  I don't have much invested in it, but I'm hoping to learn something while pursuing this.  Your help is much appreciated.

---

### Post by TheFu on 2023-02-01
Code tags, please?  Thought we'd gone over that already with any terminal output, especially when the columns need to line up!

Also, the existing, installed, fstab file is needed WITH CODE TAGS.

---

### Post by Phil Binner on 2023-02-01
Sorry, I just realised I was vastly over-complicating this.  All I actually needed to do was boot from the flash drive, navigate to the SSD and the original /etc, then edit the FStab from there.  Job done.

I will mark this as solved then come back to the original problem next week.  Thanks to all.

Phil B

---

### Post by TheFu on 2023-02-01
> **Phil Binner said:**
> Sorry, I just realised I was vastly over-complicating this.  All I actually needed to do was boot from the flash drive, navigate to the SSD and the original /etc, then edit the FStab from there.  Job done.

That's what I tried to say in #3 above first.  Guess that asking for the specific lsblk output took focus away from everything above it? Sorry.

---

### Post by oldfred on 2023-02-01
Added code tags.
How to use Code tags, # in Forum's advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

