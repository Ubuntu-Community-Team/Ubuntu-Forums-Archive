---
title: "Ubuntu made me embarrassed"
date: 2008-05-10
forum: General Help
---

### Post by bobigeorge on 2008-05-10
Hello.. i have been using Ubuntu for quite a while now on my 256 mb home PC. Actually i was more than satisfied and became a fan of it. But now i m writhing this in utter disappointment. I've purchased a brand new hp 520 notebook(1gb ram core duo) which came with WINDOWS VISTA BUSINESS installed. I WAS such a hard core fan of Ubuntu that i have uninstalled vista and installed Ubuntu 7.04. I used to boast off about Ubuntu before my friends.....**[SIZE="3"]But Ubuntu crashed (nonrecoverable) 4 times since i have installed it and Ubuntu insulted me bfore my friends :cry::cry: I can't remember a single instance when my 256 mb home pc was hang when i used it with Ubuntu... now i have even lost data??? somebody plz help me:confused:[/SIZE]**

---

### Post by mano cazalet on 2008-05-10
hello is there any message with the crashes?
maybe in system logs?

---

### Post by bobigeorge on 2008-05-11
Actually i have reinstalled the whole system(i could not recover it)... so i can't post the system log..

---

### Post by nick_h on 2008-05-11
It would be worth checking your hardware.

Run *memtest* to check your memory and *fsck* and *badblocks* to check your disks.

Have a look at [this](http://www.linux.com/articles/55366) article.

---

### Post by metiosarius on 2008-05-11
> **bobigeorge said:**
> Hello.. i have been using Ubuntu for quite a while now on my 256 mb home PC. Actually i was more than satisfied and became a fan of it. But now i m writhing this in utter disappointment. I've purchased a brand new hp 520 notebook(1gb ram core duo) which came with WINDOWS VISTA BUSINESS installed. I WAS such a hard core fan of Ubuntu that i have uninstalled vista and installed Ubuntu 7.04. I used to boast off about Ubuntu before my friends.....**[SIZE="3"]But Ubuntu crashed (nonrecoverable) 4 times since i have installed it and Ubuntu insulted me bfore my friends :cry::cry: I can't remember a single instance when my 256 mb home pc was hang when i used it with Ubuntu... now i have even lost data??? somebody plz help me:confused:[/SIZE]**

Sounds like a hardware, not an OS, problem to me...run some diagnostics on your memory, hard drive, etc...

---

### Post by Johnsie on 2008-05-11
Sounds like a hardware issue to me too. That's probably now what you want to hear though :-(

If I guess you could try putting another OS on for a while and see what happens with that. Sometimes Ubuntu just doesn't like certain hardware configurations.

---

### Post by metiosarius on 2008-05-11
> **Johnsie said:**
> Sounds like a hardware issue to me too. That's probably now what you want to hear though :-(

Well if its a new computer, perhaps he could return it and get a replacement...

---

### Post by Johnsie on 2008-05-11
certainly... And then if the new/replacement computer doesn't work with ubuntu you'll know that it must be a compatibiliy issue with that type of computer. If you do that make sure and post soemthing on [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu) to make the Ubuntu developers aware of the problem.

---

### Post by Linux&amp;Gsus on 2008-05-11
Besides what is already said maybe try a newer version of Ubuntu. Who knows, maybe your computer and 7.04 don't play too well together.
Just a thought...


Cheers,
Steve

---

### Post by sgtGarcia on 2008-05-11
Maybe you should try Ubuntu 8.04, or at least 7.10. Ubuntu 7.04 is known to have some issues with some hardware. Test it before you give back computer or worst, You gonna install Win#$%s :)

---

### Post by bobigeorge on 2008-05-11
thanks everyone for your quick sujjestions... but is it possible to get a replacement for the above problem??? if yes i would like to know the procedure... i've already mailed hp service for more than one reasons(my audio output jack stoped functioning)... thankz in advance...

---

### Post by metiosarius on 2008-05-11
> **bobigeorge said:**
> thanks everyone for your quick sujjestions... but is it possible to get a replacement for the above problem??? if yes i would like to know the procedure... i've already mailed hp service for more than one reasons(my audio output jack stoped functioning)... thankz in advance...

The "procedure"?

Call the manufacturer, tell them that you've had endless problems with it, ask for a replacement or for your money back so you can buy a new one :) But, of course, thats just what I would do :)

You have a slight advantage if you've already had hardware issues, they *should* be more likely to ship a replacement or simply give you a refund. 

Just to be sure that it isn't an Ubuntu issue (although I highly doubt it) try downloading one of the latest iso's (8.04) and installing it.

---

### Post by nick_h on 2008-05-11
> **bobigeorge said:**
> thanks everyone for your quick sujjestions... but is it possible to get a replacement for the above problem??? if yes i would like to know the procedure... i've already mailed hp service for more than one reasons(my audio output jack stoped functioning)... thankz in advance...

Did you try to run any diagnostics?  It might help if you could tell them that you have identified a particular fault.

---

### Post by Barriehie on 2008-05-11
I can vouch for the correct assemblage of hardware contributing greatly to the funcionality of an OS.  For many years I went along reinstalling that other OS when humpty dumpty dumped.  One day it hit me and I purchased a mb with AMD processors and BIOS, a D-Link NIC, soundblaster for audio, and ATI for graphics.  When I got home I disabled ALL of the 'stuff' on the motherboard that I could replace with a PCI card.  

By todays standards this box might be appearing slow but it's been zooming along without so much as a sniffle for sneaking up on 1 1/2 years.  Since installing 7.10, about 2 months ago, it appears to zoom better than that other OS.  Only oops' so far have been part of my Ubuntu learning curve... :)

Barrie

Note: Only thing I'ld change so far would be my video card.  I sometimes have to reset the screen resolution and logout/in for it to take effect.

---

### Post by bobigeorge on 2008-05-11
when i tried fsck ->


fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)?

when i tried memtest ->


Usage:

memtest <mem<B|K|M|G>> [runs] [-l or --log]
    mem          - memory to test (B=bytes, K=KiB, M=MiB, G=GiB)
                   Byte values will be rounded down to nearest multiple of 64.
                     e.g. 2G   =  2 GiB
                          12M  = 12 MiB
                   Special value 'all' tests all available memory.
    runs         - times to run tests (default: 2^32 - 1)
    -l or --log  - log to file memtest.log

and i can't find memtest.log


and badblocks ->


Usage: badblocks [-b block_size] [-i input_file] [-o output_file] [-svwnf]
 [-c blocks_at_once] [-p num_passes] [-t test_pattern [-t test_pattern [...]]]
 device [last_block [start_block]]


am i doing something wrong???? i just typed it in terminal!!!!

---

### Post by RJARRRPCGP on 2008-05-11
> **nick_h said:**
> It would be worth checking your hardware.

Run *memtest* to check your memory and *fsck* and *badblocks* to check your disks.

Have a look at [this](http://www.linux.com/articles/55366) article.


I SO agree! I'm sick of people blaming the OS, when it's the hardware being fritzy!

Run Memtest86+ (It's on the Ubuntu 8.04 CD, IIRC)

---

### Post by nick_h on 2008-05-12
> am i doing something wrong???? i just typed it in terminal!!!!

For memtest, do as RJARRRPCGP suggested and run it from the Ubuntu CD or from the grub menu (press ESC when booting).

For fsck, you need to run it on an unmounted filesystem.  To check the root filesystem you will need to boot to a Ubuntu live CD or run it at boot.  You can do this by creating a file in the root filesystem:
```
sudo touch /forcefsck
```

For badblocks, have a look at the link I gave you, it gives an example syntax.  Replace *HDD_DEVICE* with sda1.

---

