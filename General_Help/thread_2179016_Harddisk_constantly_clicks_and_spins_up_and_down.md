---
title: "Harddisk constantly clicks and spins up and down"
date: 2013-10-06
forum: General Help
---

### Post by Arjunanda on 2013-10-06
Hi,

I recently installed Ubuntu on my new Asus F202X after previous one got stolen. I had the same laptop model previously, and all was working fine. After I installed 13.04 on this one, I have noticed one problem: My harddisk is constantly making clicking sounds and spinning up and down:

Click -- spin down -- spin up; Click -- spin down -- spin up; Click -- spin down -- spin up.

This goes in about 10 sec sycles. Usually the time between two clicks is 10 sec, but sometimes 7, sometimes 5 sec, sometimes 3 sec, and occasionally 20 sec. And then sometimes it remains quiet for several minutes. The click sound is similar as if the harrdisk is parking the reading head. I'm worried this will break the disk, or at least greatly reduce the lifetime.

What is causing this? I never had this kind of problem before. I used the default install and the default partitioning, with home dir encryption and LVM. Can it be that this is caused by that?

---

### Post by The Cog on 2013-10-06
A program called **iotop** will show you what's using the disk. But it won't tell you why the disk is clicking. I have no idea what that's about.
```
sudo apt-get install iotop
sudo iotop
```

---

### Post by varunendra on 2013-10-06
> **Arjunanda said:**
> My harddisk is constantly making clicking sounds and spinning up and down

It happens when the head tries to find or read something which it expects but can't find on the disk platter, because either the address is 'outside' the physical boundaries of the platter, or the head just looses its track and tries to search/locate it again.

Usually, this is an indication that the hard disk is trying to say its last good-byes to you, hoping you take notice in time. But sometimes it can happen due to logical file-system errors too (or physical bad clusters on critical areas). Since you said your system is "New", the latter maybe true.

But in any case, you should back up your data as soon as possible, then try "fsck" on the disk (from a live session) if it is an Ubuntu-only disk, or "chkdsk" from windows if it is a dual-boot with windows. In some cases, you may have to re-partition/full-format the drive.

Oh, and if it is easily accessible, try removing/re-seating the hard disk to ensure it is not a loose contact problem.

---

### Post by Arjunanda on 2013-10-07
Thanks guys.

As suggested, I installed iotop, but it tells me nothing useful. I dont think it is any program polling the disk, but rather what Varunendra wrote.

Anyhow, I have taken backup, and will shrotly try fsck to see what is going on. I think I cannot easily access the disk as it may void the varranty. But I'll see what are the warranty options that could be of use in this case.

---

### Post by varunendra on 2013-10-08
In almost all of the laptops I've seen so far (except one "Emachine" model), parts like RAM, HDD, WiFi card are located in user-accessible areas and can be easily accessed / swapped without voiding the warranty.

Take a look at the bottom plates and if you have a few of them without warranty seal stickers on their screw holes, it means they can be safely opened.

---

### Post by heir4c on 2013-10-08
Try this command:
```
sudo hdparm -B 254 /dev/sda
```
Look out! see that sda is your drive. If it's not and it's sdb, sdc or.... change that.
That would stop the clicking. 
I have that from Pjotr his site.  (member of the Dutch forum)  (in Dutch on the right site of the page): [https://sites.google.com/site/computertip/fouten#TOC-Sommige-laptops:-parkeerklik-slijtage-vermijden](https://sites.google.com/site/computertip/fouten#TOC-Sommige-laptops:-parkeerklik-slijtage-vermijden)

---

### Post by varunendra on 2013-10-08
> **heir4c said:**
> Try this command:
```
sudo hdparm -B 254 /dev/sda
```
Nice trick that heirc4c, thanks for sharing. :)

However, be aware that *some* hdparm commands [COLOR="#FF0000"]can be Extremely Dangerous, although the above one is not[/COLOR]. It is advisable to read the man page for hdparm (man haparm) before trying any options. Similarly, it is also advisable to post the effect of the command if you are suggesting one.

From "man hdparm" (stripped info) -
>  **-B**     Get/set Advanced Power Management feature, if the drive supports
              it.  A  low  value  means aggressive power management and a high
              value means better performance.  Possible  settings  range  from
              values  1  through  127 (which permit spin-down), and values 128
              through 254 (which do not permit spin-down).

So that's it. But given the fact that the time between two clicks is less than a minute (even down to 3 sec !!), and varying, I highly doubt it can be a power management issue.

---

### Post by heir4c on 2013-10-09
> Nice trick that heirc4c, thanks for sharing. 
It's not my trick, and I would not give that here when I don't know it works, I use it a few times. Pjotr is on this forum Pjotr123 and have a site with many info and tips and tricks.i(in Dutch).
If it works it can write down in the hdparm.conf file.
He write also that the reason of the click are from the energy settings. When you set it to extra energy saving than it "parks" to aggressive. (some laptops have a problem with that, something to do with the firmware)

---

### Post by Arjunanda on 2013-10-09
thanks for the tip, heir4c :)

I tried it a few minutes ago and so far no clics. But today the laptop was quiet anyway most of the day, without any settings. So I really don't get what is causing it, as it is so irregular. But anyway, as the laptop was quiet today without clicks, I wanted to wait until the clicking starts again. And it just started and I issued this command, effectively stopping the clicking again.

I will let it be like this and test it tomorrow the whole day, and if it works, will ad it to the .conf file. But I think I'll adjust the value a bit, allowing the powersave to work to some degree.

---

### Post by heir4c on 2013-10-09
Ok, but thank Pjotr123. It's his site and his tip. And he have a site in English too but there he don't mentioned this tip. (I don't now why). [https://sites.google.com/site/easylinuxtipsproject/Home](https://sites.google.com/site/easylinuxtipsproject/Home)

---

### Post by Arjunanda on 2013-10-11
Yes, this solved the issue. :) Thank you all :)

---

### Post by Pjotr123 on 2013-10-12
> **heir4c said:**
> Ok, but thank Pjotr123. It's his site and hits tip. And he have a site in English too but there he don't mentioned this tip. (I don't know why). [https://sites.google.com/site/easylinuxtipsproject/Home](https://sites.google.com/site/easylinuxtipsproject/Home)

I fixed that omission today:
[https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Some-laptops:-hard-disk-constantly-clicks-and-spins-up-and-down](https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Some-laptops:-hard-disk-constantly-clicks-and-spins-up-and-down)
(item 8, right column)

Thanks for pointing this out. :)

---

### Post by heir4c on 2013-10-12
ThanX Pjotr for adding it to your English site.

---

