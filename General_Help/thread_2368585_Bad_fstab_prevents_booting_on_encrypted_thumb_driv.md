---
title: "Bad fstab prevents booting on encrypted thumb drive"
date: 2017-08-12
forum: General Help
---

### Post by steve169 on 2017-08-12
I installed Lubuntu 16.04 onto a thumb drive and fully updated it. I encrypted the thumb drive when I installed. Worked fine.

Then I edited fstab so it would mount my hard drives at bootup.

I must have made an error, because now the thumb drive won't boot.

I have the original fstab contents, but because the thumb drive is encrypted, I can't get to fstab to return it to its original state.

Is there a work-around for this? I hate to think of restarting from scratch.

---

### Post by TheFu on 2017-08-12
a) restore from a backup.  Whenever encryption is used, backups are extremely important.

b) You can boot from a live-boot environment (cdrom/dvd/flash drive), then install the lvm, luks, dm-crypt and cryptsetup tools, unlock the encrypted flash drive, use vgscan to capture the lvm information from the flash drive, then mount the specific logical volume and modify the contents of the fstab.  Simple.

It is a hassle and takes about 5 minutes when you know what you are doing.

The probable layout of everything looks like this:
```
$ lsblk
NAME                          MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                             8:0    0 119.2G  0 disk  
&#9500;&#9472;sda1                          8:1    0   512M  0 part  /boot/efi
&#9500;&#9472;sda2                          8:2    0   488M  0 part  /boot
&#9500;&#9472;sda3                          8:3    0  70.8G  0 part  
&#9474; &#9492;&#9472;crypt1                    253:0    0  70.7G  0 crypt 
&#9474;   &#9500;&#9472;ubuntu--mate--vg-root   253:1    0  57.4G  0 lvm   /
&#9474;   &#9492;&#9472;ubuntu--mate--vg-swap_1 253:2    0   4.1G  0 lvm   [SWAP]
&#9500;&#9472;sda4                          8:4    0  47.5G  0 part  

```

sda3 is the normal partition.
crypt1 is inside sda3 partition and encrypts everything inside it.
vg-root is the main logical volume for the OS (encrypted), inside crypt1
vg-swap_1 is the swap logical volume for swap (encrypted), inside crypt1
sda4 is NOT encrypted.  You won't have that. I had to do some fairly ugly things to make that outside the encrypted area and failed the 1st 3 attempts.

Hope this helps.

---

### Post by steve169 on 2017-08-14
Dear TheFu,

Many thanks for your detailed reply. I tried, but it was beyond the capabilities of this newbie. So I resigned to reinstalling from scratch, which eventually succeeded.

---

### Post by TheFu on 2017-08-14
Be certain to make versioned backups as needed.  I do daily, but many people seem happy with weekly backups - just before their weekly patching.

---

