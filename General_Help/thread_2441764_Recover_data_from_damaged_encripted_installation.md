---
title: "Recover data from damaged encripted installation"
date: 2020-04-26
forum: General Help
---

### Post by nsuria on 2020-04-26
Hi!

I had an encrypted installation of Ubuntu 18.04 and I was about to install Windows to have a dual boot on my machine. To prepare the partitions I started the PC with a Ubuntu live stick to set a partition for the new windows installation. There was just one partition, so I was about creating another for Windows. The thing is that accidentally I erased the space marked as free. Now ubuntu don't start. It takes a long time booting and it's finally stuck with a "Failed to connect lvmetad" error. 

If I check the drive partitions with the live stick, I see several partitions: loop1 to loop8, sda and sdb. 

I have already tried to use udisksctl unlock commands as suggested in this post ([https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line](https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line)), but the console don't ask me for any password.

Is there any chance I can recover it?

Thank you a lot in advance for your help!

---

### Post by CelticWarrior on 2020-04-26
Welcome.

Sorry, no chance.

---

### Post by ActionParsnip on 2020-04-27
Is there valuable data on the storage? If so, why did you not make a backup before making such an enormous change to the system?

---

### Post by ajgreeny on 2020-04-27
Using encryption demands that you must have known good backups of all data and important files in the system just in case something fails to work properly. Encryption is, let's  face it, a method of keeping others away from your files and if something does go wrong you will be unable to get anything back yourself.

If you still have the pass phrase which works you might be able to get something back, but that is my guess as I've never used encryption and it's  a bit of a mystery to me.

Good luck!

---

### Post by nsuria on 2020-04-28
Hi!

Thank you a lot for your answers. I really appreciate it.

I'm also wondering why I did not a backup. The data in this hard drive is not crucial, but I'm interested in recovering some files.

I have the password, and as I deleted just the free part of the partition, I guess that at least one chance must be. Ubuntu is showing signs of trying to boot, so I think that things are not that bad.

I'm starting to study computer science, so I would like to get deeper into what does Ubuntu store into the free part of de drive when you do an encrypted installation and what is really happening when you delete just this part. Do you know were can I find additional documentation?

Best regards,

Nil

---

### Post by oldfred on 2020-04-28
Encrypted installs use LVM - logical volume management.
That is an advanced way to split drive into volumes instead of partitions. It normally uses one large partition for all the volumes. You may have an ESP if UEFI boot and may have a separate /boot partition, both small and rest of drive as the LVM.

LVM is better for knowledgeable users, but if you must have full drive encryption you have to jump into the deep end of the pool and use LVM.

For mounting encrypted see first few lines:
[https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu](https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu)

Recover files on encrypted drive
[https://ubuntuforums.org/showthread.php?t=2382995](https://ubuntuforums.org/showthread.php?t=2382995) & 
[https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line](https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line)

---

### Post by CelticWarrior on 2020-04-28
In any non-encrypted partition it should always be possible to recover *some* of the files in cases like yours where only one small part of the data was affected.

With encryption it's a very different situation. All data is garbled/truncated, it's meaningless in that state. So, even a small part missing makes the whole thing unusable. It must be recovered completely, pristine, to same state as before in order to be decrypted. This is the reason for my terse response earlier. It is indeed game over and that's why we use encryption.

---

### Post by nsuria on 2020-04-29
Hi! 


Thanks again for your answers!


I marked the thread as solved. However, I'm going to try to understand the problem better and if I get something interesting I will post it here. 


Best regards and best wishes for this days of cuarentene. 


Cheers,

---

### Post by dragonfly41 on 2020-04-29
If you are studying this as a computer science  exercise then I suggest that you add the string "forensics" to your google search and you will get into posts from various computer forensics investigators. [Here is one at random]("https://articles.forensicfocus.com/2018/02/22/bruteforcing-linux-full-disk-encryption-luks-with-hashcat/").  There are some forensics threads in ubuntuforums if you search.

---

