---
title: "Data encryption"
date: 2015-08-30
forum: General Help
---

### Post by fangorn2 on 2015-08-30
Hi,

my distribution is Ubuntu 14.04 LTS.
I would like to add an encrypted folder with subfolders and files within it in my home folder or even elsewhere, it does not matter: a password should be required whenever it is necessary to enter this directory.

Ubuntu was installed by someone else who chose to log in automatically. I must however use a password to make changes such as installing new software.

I read the following page about encryption in Ubuntu:

[https://help.ubuntu.com/community/EncryptedHome#Encrypted_Private](https://help.ubuntu.com/community/EncryptedHome#Encrypted_Private)


I think that an Encrypted Private directory can be what I am looking for, but I also read about 'encfs' and I imagine there may be other tools for encryption that might have good reputation.

What is in our opinion the best choice?


I also would like Ubuntu to require a password to log in, thus change the automatic login, and then eventually migrate to an encrypted home directory.


Many thanks in advance for your help

---

### Post by TheFu on 2015-08-30
Encrypted HOME directories use a slow encryption method. Better on a personal workstation to use whole drive encryption, IMHO. It is pretty easy to control during an installation, but the instructions for adding it later are out of date - I tried a few months ago and failed.  Ended up backing up my system, installing fresh with whole drive encryption enabled, then selectively restoring.  The encryption you should use is dm_luks.

Regardless, please have excellent backups.  Logical corruption on disk can make any encryption fail.

If you are going to the effort to do this, you might be interested in following Linux Foundation's Workstation Security Guide: [https://github.com/lfit/itpol/blob/m...on-security.md](https://github.com/lfit/itpol/blob/m...on-security.md)

Good luck. I realize this isn't what you asked. I believe **askubuntu** has detailed answers for this stuff already - definitely for how to enable a password at login.

---

### Post by fangorn2 on 2015-08-30
I read about dm_crypt, Cryptsetup and LUKS at the following, interesting link:

[http://thesimplecomputer.info/encrypt-your-linux-home-folder-2-ways-and-10-steps](http://thesimplecomputer.info/encrypt-your-linux-home-folder-2-ways-and-10-steps)


I agree that LUKS would be the best choice, however in the above article it is written that /root, /home and swap must all be separate partitions.
I only have 2 partitions: /root and swap, so I suppose I will not be able to use dm_crypt, Cryptsetup and LUKS, unless I decided to reinstall Ubuntu, choice that I would like to avoid if there are alternative choices.

---

### Post by Halbarad on 2015-08-30
I never tried whole drive encryption. For my sensitive data I use encfs, which seems to me quick and efficient. I have written two batch files for controlling my sensitive data quickly. The first one "opens" the encrypted directory (and creates it in case it does not exist).
> #!/bin/bash
CWD=$(pwd)
EncSource=$CWD"/.DataFolder"
echo $EncSource
EncOpen=$CWD"/Data"
encfs $EncSource $EncOpen

If you open a terminal from the device or folder in which your DataFolder is placed, you need not specify a path.
To close the encrypted directory:
> #!/bin/bash
CWD=$(pwd)
EncOpen=$CWD"/Data"
fusermount -u $EncOpen

or just shut down.
After opening it, I don't even perceive that it is slower than any "normal" folder. I've been using it for a couple of years.

---

### Post by TheFu on 2015-08-30
I've done disk performance testing. So have some reputable websites known for performance testing all-things-linux.  encfs is really slow. 2-3x slower than other options. If that is fast enough, fine.  That is the way of the world - fast enough **is** good enough.

My real issue with HomeDirectoryEncryption was that it broke my backups and system security wasn't helped, just personal security.

Ideally, LUKS needs 2 partitions - 
* /boot
* everything else controlled by LVM

Inside LVM, you can have as many LVs as you like - LVs are like partitions that can be resized as needed, often on a running system.```
$ lsblk
NAME                            MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                               8:0    0 119.2G  0 disk  
&#9500;&#9472;sda1                            8:1    0   243M  0 part  /boot
&#9500;&#9472;sda2                            8:2    0     1K  0 part  
&#9492;&#9472;sda5                            8:5    0   119G  0 part  
  &#9492;&#9472;sda5_crypt (dm-0)           252:0    0   119G  0 crypt 
    &#9500;&#9472;c720--vg-root (dm-1)      252:1    0  51.9G  0 lvm   /
    &#9492;&#9472;c720--vg-lv--swap (dm-2)  252:2    0   4.1G  0 lvm   [SWAP]
```
    
Make sense? sda5 is encrypted. Everything inside it is encrypted.  You can see there is about 50G free for use when needed. That can be added to existing LVs or new LVs can be created for /home or where ever it is needed - perhaps /var?  When needed, it is there and already encrypted.  

With LVM, other storage can be added too - either logically or not to new or existing LVs.

Anyway - I'm hope this is eye opening, but doing what you initially wanted seems possible too.

---

### Post by fangorn2 on 2015-08-30
I need time to understand it.

Anyway, this is my partition table:

```

~$ lsblkNAME   MAJ:MIN   RM   SIZE      RO   TYPE     MOUNTPOINT

 sda           8:0       0    465,8G    0    disk 
&#9500;&#9472;sda1         8:1       0    512M      0    part     /boot/efi
&#9500;&#9472;sda2         8:2       0    459,4G    0    part     /
&#9492;&#9472;sda3         8:3       0      5,9G    0    part     [SWAP]

```

Do you think I can use LUKS?

---

