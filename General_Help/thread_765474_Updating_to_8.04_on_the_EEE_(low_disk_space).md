---
title: "Updating to 8.04 on the EEE (low disk space)"
date: 2008-04-24
forum: General Help
---

### Post by sablefoxx on 2008-04-24
Okay i've got an [ASUS eee-pc]("http://www.newegg.com/Product/Product.aspx?Item=N82E16834220261") (w/2Gb RAM) trying to upgrade to 8.04 from 7.10 but i dont have enough space on the internal (4Gb SSD) to download all the packages, i do have a 8Gb SD card, is there any way i can store the needed files on the SD card while it installs onto the internal 4Gb, and delete them when im all done?

---

### Post by xerosis on 2008-04-24
Hi,

If you mount your SD card to /var/cache/apt/archives/ the packages will install to there and you will have enough space for the install.

---

### Post by sablefoxx on 2008-04-25
So how do i do that exactly?

---

### Post by natrixgli on 2008-04-25
**EDIT: You might wish to backup and clear out the SD card first to be safe..**

Well you will have to rock out some command line for this one.... 

First you have to identify your card in the system.. I would pop it in, and in a terminal type 'dmesg' and press enter. 

You will see a bunch of stuff, but what you are looking for will be towards the end, sort of like this:

```

[101338.462707] sd 5:0:0:0: [sdb] 7823360 512-byte hardware sectors (4006 MB)
[101338.463706] sd 5:0:0:0: [sdb] Write Protect is off
[101338.463714] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[101338.463718] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[101338.466323] sd 5:0:0:0: [sdb] 7823360 512-byte hardware sectors (4006 MB)
[101338.466936] sd 5:0:0:0: [sdb] Write Protect is off
[101338.466943] sd 5:0:0:0: [sdb] Mode Sense: 23 00 00 00
[101338.466946] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[101338.466952]  sdb: sdb1 sdb2
[101338.647457] sd 5:0:0:0: [sdb] Attached SCSI removable disk

```

The part between the brackets [sdb] is what we're interested in, specifically the letter after 'sd'. On mine, it's sd**b** and probably on the Eee it will be the same, but check just in case.

The card gets auto mounted to /media/whatever, so then you're gonna need to unmount the card with:

```
sudo umount /dev/sd**x**1
```

(replace 'x' with the actual letter from the dmesg output.)

Then you can mount the card using:

```
sudo mount /dev/sd**x**1 /var/cache/apt/archives/
```

(again, replace 'x' with the actual letter from the dmesg output.)

Now when you run the upgrade, the packages will be stored on the card during the upgrade. 

Hopefully my instructions aren't rubbish, please feel free to ask for clarification if they are.

-n8

---

### Post by chewit on 2008-04-25
I know that this is not releated to the question. But in that dir. I still have all the deb install files from my update. My update crashed after it installed everything. I didn't do the clean up part.

Is it ok for me to delete these install files?

---

### Post by natrixgli on 2008-04-25
> **chewit said:**
> I know that this is not releated to the question. But in that dir. I still have all the deb install files from my update. My update crashed after it installed everything. I didn't do the clean up part.

Is it ok for me to delete these install files?


```
sudo apt-get clean
```

should fix you right up. Check out 'man apt-get' for more info.

-n8

---

### Post by aapo4 on 2009-04-28
This low disk issue in upgrading is annoying, so I post one more solution.

First I suggest you use command line upgrading, because then you see all error messages.
```
sudo do-release-upgrade
```

Maybe you have home in another partition/disk and there are lots of space.

a) Make new directory, name isn't important. 
b) Make subdirectory named partial (name is important)
c) remove /var/cache/apt/archives
d) link your new directory to /var/cache/apt/archives

```

cd ~
mkdir upgrade_cache
mkdir upgrade_cache/partial
sudo rm -r /var/cache/apt/archives
sudo ln -s upgrage_cache /var/cache/apt/archives
sudo do-release-upgrade

```

And after that, rolling back:

```

sudo rm -r /var/cache/apt/archives
sudo mkdir /var/cache/apt/archives
sudo mkdir /var/cache/apt/archives/partial
cd ~
rmdir upgrade_cache/partial
rmdir upgrade_cache

```

---

### Post by eyal_allweil on 2010-03-21
I followed the instructions in this thread (created a link to a directory in my home (which has free space) and am still getting an out-of-space error based on the size of my / partition. Any ideas? I also tried the instructions here for an alternative way to do this:

[http://www.ubuntu-fl.org/2009/08/27/hacklet-apt-cache-redirect/](http://www.ubuntu-fl.org/2009/08/27/hacklet-apt-cache-redirect/)

How do I know if there isn't enough temporary space (during the upgrade) or actual space in the partition (it's 4 gb; I have an EEE 901)

---

### Post by aapo4 on 2010-03-22
Start release upgrade and then start another terminal and use 
```
df --si
```
to check current status of disk space.


----

This instructions moves only temporary cache directory. It is possible that new system will be take more space than older one. So it will not fit. You must uninstall some packages, specially them which are growing when ugrading (no easy way to know which one).

----
If you have lot's of (enough) space in home partition, you can boot with live-usb and use (e.g.) gparted to make home partition smaller and root partition bigger. 
Or you can move all stuff in home partition out of computer and delete whole home partition and use only one big partition as root (and then copy your home files back).

----
I check your link and it says same:
"if you don’t have enough space on your root partition for the new installation, you’ll have to delete some files or resize your partition."
I only add option to merge partitions together.

---

### Post by eyal_allweil on 2010-03-24
Well, I found out what my problem was, and it wasn't a temporary space problem- it was the old linux-headers and linux-images packages which weren't removed. I found them when I sorted my packages according to installed size, and after I removed them I had more than enough "permanent" space- I still needed to use my home partition for the apt-cache.

Thanks a lot- they were clear and useful instructions!

---

