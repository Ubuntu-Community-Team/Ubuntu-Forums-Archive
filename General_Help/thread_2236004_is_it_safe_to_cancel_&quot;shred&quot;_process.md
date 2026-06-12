---
title: "is it safe to cancel &quot;shred&quot; process"
date: 2014-07-24
forum: General Help
---

### Post by mus2 on 2014-07-24
Hi,

I am using 

**sudo shred -vzn 1 /dev/sdb**

on my 1.5 TB WD external hard disk. (About 700 GB of it was full)

1 day has passed and just the "random write" process is at 10%... I wonder how long the "write zeros" will last. Looks like it's going to last forever!

Is it safe to cancel this shredding process?

I don't have sensitive data in the HDD and I was using shred because I encountered some reading/writing problems with the HDD, hoping shred would fix the HDD.

Calling out experts... should I cancel it or not?

Thanks!

---

### Post by sudodus on 2014-07-24
Welcome to the Ubuntu Forums :-)

Yes, you can cancel it.

I suggest that you check the S.M.A.R.T. information of the drive. You might get a summary in a BIOS or UEFI menu. You can get more details if you install and run ***smartctl***.

```
sudo apt-get install smartmontools
```

```
 man smartctl
```

and run for example

```
sudo smartctl -H /dev/sda
sudo smartctl -a /dev/sda
sudo smartctl -t long /dev/sda

```

As you understand, the wiping is not complete, but the partition table  is probably overwritten, so you need to make a new partition table. Have  you used ***gparted*** before? And do you know what you want? If you have problems (that there are strange data, that confuse gparted), you can wipe the first megabyte, and gparted should be happy. See this link
[URL="http://ubuntuforums.org/showthread.php?t=1958073"]
Ubuntu Forums tutorial "Howto make USB boot drives"[/URL]

---

### Post by HermanAB on 2014-07-24
Shred is a very good tool for wearing out your disk drive.  For security, not so much.  

The best way to protect data is to encrypt it.  To erase encrypted data, simply hit yourself upside the head with a brick to forget the password.

---

