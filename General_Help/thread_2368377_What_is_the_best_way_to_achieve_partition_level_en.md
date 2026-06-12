---
title: "What is the best way to achieve partition level encyption?"
date: 2017-08-10
forum: General Help
---

### Post by Bobby_James on 2017-08-10
I have a dual boot Windows / Ubuntu 16.04 system. I am wondering if there is a point to partition level encryption for the Ubuntu partition and, if so, what is the best way?

I use a BIOS password then have the Ubuntu login password. It's not entirely clear to me how any kind of encryption would benefit me. I assume the idea is that if the machine was attacked after I had logged in then encryption would provide an additional form of security.

What would be the best tool to use to encrypt an existing 16.04 partition?

Many thanks.

---

### Post by TheFu on 2017-08-10
Storage encryption helps when the system is off or to prevent causal access to data partitions which are not automatically mounted.

Also, if you have sensitive data - I consider all data "sensitive" - if a HDD fails or needs to be warranty replaced, shipping a disk full of sensitive data to the vendor to get a refurbished replacement means they will have access to all that data.  And don't forget that deleting files doesn't actually remove all the data blocks and wipe them.  The data is still on the disk, just without any file system pointers saying those blocks are used.  If you use encryption, there isn't any worry about someone else peeking at that data.

Lastly, for any portable device, there is a real risk of theft.  Encryption means the bad guys don't get to run through your personal data and look for other opportunities to screw with you, your life, your friends.  Encrypting all portable devices AND having them auto-lock after a few minutes is a responsible thing.  A friend had his smartphone stolen while traveling internationally.  Before he could change all the logins to other systems, the thieves had grabbed his calendar, all contacts, all emails and were in the process of asking all his friends for money to get out of jail.  I was traveling with him and got a few emails pleading for help from his account.

So ... it is nearly impossible to encrypt the OS partition after-the-install. There are just too many details and complexities.  I've tried.  Encrypt the OS during the install.

Encrypting a data partition after the fact isn't THAT hard, but there isn't any "in-place" method.  You'll need to backup all the data to other storage and be certain to capture all the ownership, groups, permissions, any xattrs and ACLs too.  Then you can use **cryptsetup** - and LUKS w/ dm-crypt to encrypt the data. Don't worry, the cryptsetup tool is all you'll use, those other terms are just connected projects that cryptsetup simplifies for our use. You may want to play around with a portable flash drive with cryptsetup to see it working before trying this on the internal disk.  Practice makes perfect, right?  If you learn by watching videos, cat5.tv has a video about using LUKS to encrypt a flash drive - look in tech clips season 10.

There are other methods to encrypt at the file level too, but those are generally considered weak and leak metadata information about each of the encrypted files.  encfs and eCryptfs are examples.  There are ubuntu how-to guides for each of these things. Google finds them easily - "ubuntu encrypt file system" is the search.

[https://help.ubuntu.com/community/EncryptedFilesystems](https://help.ubuntu.com/community/EncryptedFilesystems) is one of the results returned.

There are lots of choices when it comes to encryption.  To use LVM or not?  Whole drive or not?
```
$ lsblk
NAME                          MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                             8:0    0 119.2G  0 disk  
&#9500;&#9472;sda4                          8:4    0  47.5G  0 part  
&#9500;&#9472;sda2                          8:2    0   488M  0 part  /boot
&#9500;&#9472;sda3                          8:3    0  70.8G  0 part  
&#9474; &#9492;&#9472;crypt1                    253:0    0  70.7G  0 crypt 
&#9474;   &#9500;&#9472;ubuntu--vg-root   253:1    0  57.4G  0 lvm   /
&#9474;   &#9492;&#9472;ubuntu--vg-swap_1 253:2    0   4.1G  0 lvm   [SWAP]
&#9492;&#9472;sda1                          8:1    0   512M  0 part  /boot/efi
```
That is the disk layout of my laptop.  sda3 is a normal GPT partition.  "crypt1" is the dm-crypt device for the entire partition, then I use LVM to have a volume group and 2 logical volumes inside the same partition.
Note how sda1 and sda2 are outside the encryption. This is required so the system can boot.
My sda4 partition is NOT encrypted. I intend to place a small non-encrypted Linux there for quick uses, but haven't gotten around to that. 

There is an extensive how-to in the Security subforum, BTW. I've not followed it.
Getting my setup NOT to use the entire SSD was non-trivial.

---

