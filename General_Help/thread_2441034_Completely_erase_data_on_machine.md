---
title: "Completely erase data on machine?"
date: 2020-04-18
forum: General Help
---

### Post by dannyk2 on 2020-04-18
I want to sell a spare desktop computer i no longer use but there is a lot of personal data on the machine and i don't want anyone to be able to access it. So could anyone tell me if there is any 'free' programs out there that will completely erase all data from this machine please. Thanks

---

### Post by dino99 on 2020-04-18
Lot of choices:

Windows:
[https://www.wikihow.com/Permanently-Erase-Data-Off-a-Hard-Drive](https://www.wikihow.com/Permanently-Erase-Data-Off-a-Hard-Drive)
[https://www.raymond.cc/blog/permanently-delete-and-remove-sensitive-files-to-prevent-data-recovery/](https://www.raymond.cc/blog/permanently-delete-and-remove-sensitive-files-to-prevent-data-recovery/)

Linux;
[https://www.cyberciti.biz/faq/linux-remove-all-partitions-data-empty-disk/](https://www.cyberciti.biz/faq/linux-remove-all-partitions-data-empty-disk/)
[https://www.ostechnix.com/securely-permanently-delete-data-linux/](https://www.ostechnix.com/securely-permanently-delete-data-linux/)
[https://www.howtogeek.com/125157/8-deadly-commands-you-should-never-run-on-linux/](https://www.howtogeek.com/125157/8-deadly-commands-you-should-never-run-on-linux/)

---

### Post by ajgreeny on 2020-04-18
I have just done exactly what you wish to do and I used two different commands on two separate disks just to check the time it took and which was fastest; unfortunately I then forgot to keep looking and all I know is that both were slow, taking a couple of hours at least on the 500G drives.
```
sudo dd if=/dev/zero of=/dev/sdf bs=1M
sudo shred -v -n 1 -z /dev/sdf
```

Be ***very, very, very careful*** with both commands to get the /dev/sdx right or you're in big trouble and will never get the data back.
Be sure and run ```
sudo parted -l
``` first to check which disk is which.

---

### Post by CelticWarrior on 2020-04-18
SSD or HDD?

I've heard there's a difference.

---

### Post by TheFu on 2020-04-18
As long as the NSA isn't getting the used computer, a simple shred or DBAN with 1 pass should be more than sufficient. Then you cal load up the 20.04 or 18.04 Ubuntu flavor best for the machine 
OR
just sell it without any storage and keep the storage for your own needs like backups.

I've used 
```
sudo ddrescue /dev/random  /dev/sdz  /tmp/log
```
for a quick random wipe of an entire disk before.  "Quick" being relative.  Usually just start it and come back 6 hrs later or the next day.  
ddrescue will keep going even if the disk is damaged. dd will stop.

---

### Post by HermanAB on 2020-04-18
All of the above will work well enough and waste a lot of time.  

There is also allow level erase utility built into the drive controller of every disk drive made this century.  You can activate it with the hdparm utility.  It will of course waste even more of your time.

---

