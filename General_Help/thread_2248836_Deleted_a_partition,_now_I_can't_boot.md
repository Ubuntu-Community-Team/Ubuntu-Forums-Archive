---
title: "Deleted a partition, now I can't boot"
date: 2014-10-17
forum: General Help
---

### Post by collin7 on 2014-10-17
I hope I am posting this in the right place.

I built a machine a few years ago with a friend of mine and I later made it a dual boot system. I was booting Ubuntu and Windows Vista but I had to type in the hard drive location every time because I didn't have all my HDs connected at the time of installation. Later during an oblivious moment that I had I overwrote a partition on my drive while in windows. Now I am unable to boot at all. I would like to be able to boot windows and could figure out or reinstall Ubuntu from there. I do not get grub. I get a black screen. I am at work now so I cant check but either I could not get to the bios or switching to the windows partition in the bios doesn't help. I have only the one computer that is down at home so that is a handicap.

Please help,
-C

---

### Post by Bashing-om on 2014-10-17
collin7; Hi ! Welcome to the forum .

Bad things can happen - that is a major reason we keep good backups .
It might be as simple as booting the ubuntu liveDVD, saving your files from the liveDVD environment, and then (RE-)installing ubuntu.

Post back the outputs - Between Code Tags - of terminal commands:
From the liveDVD(USB)
```

sudo fdisk -lu
sudo parted -l
ls -l /dev/sd*

```
with this information we can mount the file systems in the partitions, and take a look.
Then see what is to be done.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by nerdtron on 2014-10-17
Which partition did you deleted? If windows partition is still good, assuming windows 7, you can try booting on the windows 7 DVD (or USB if you have one) and select repair startup on the installer screen. I tried it a few times before and was able to boot windows 7. This will destroy GRUB but at least you'll get to boot windows.

---

### Post by yancek on 2014-10-17
Which partition did you delete?  Did you have a separate /boot partition or were the boot files on the Ubuntu system partition?  If you deleted the boot files from Ubuntu you will need to use your vista installation medium to reinstall the windows bootloader, instructions at the microsoft link below.  If you don't have one and know which partition had your Ubuntu install you could just reinstall Ubuntu and its bootloader to the master boot record.  If you have a Linux Live CD/flash drive you could boot that and open a terminal then run the command:  sudo fdisk -l(Lower Case Letter L in the command) and post the output here.

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by collin7 on 2014-10-17
I will make a live flash drive before I leave work and give those commands a try when I get home.

---

### Post by Bashing-om on 2014-10-17
collin7; OK !

As you can see, the situation is not hopeless, Do Not Panic .
You have an army at your back to bring you through this.

We learn the most from
[INDENT][INDENT][INDENT]those uh oh - moments
[/INDENT][/INDENT][/INDENT]

---

### Post by collin7 on 2014-10-19
Ok so, I was able to get into the bios and boot off the usb. So having booted ubuntu I installed over my last version of ubuntu. That fixed my problem all together. 
I did not have to use any of the commands suggested but thank you all for you help.
As an aside: What I had prviously deleted was a 4 Gb space that is not the Ubuntu partition but maybe has something to do with the Grub and having multiple OS on one machine.

Thanks,
-C

---

