---
title: "can't use external harddrive with windows password protection"
date: 2007-07-22
forum: General Help
---

### Post by gyeti on 2007-07-22
I just bought an  external 120 Gb USB 2.0 disk by Toshiba for my notebook (Dapper Drake) and ran into a truely annoying problem. When I plug it in it mounts as a CDROM read-only with some bloody windows crap on it. Then I realized that is says something about "Password security" on the box. But hey, it's just a harddrive afterall, **that's what I thought**.

The sad story is that I didn't find a way to access the disk, yet. All attempts to partition, format, and install a linux file system failed miserably! Does anybody have experience with similar problems? I couldn't find anything on the net. If this really is a problem, people should be warned not to buy this kind of trash. And I probably will return the disk to the retailer and let Toshiba know what I thinkt about this:mad:

Here is some info that may help in solving the problem:
Disk model: Toshiba 120 Gb external usb mini hard drive (px1279e-1g12)

This is what shows up in /var/log/messages:
```
Jul 22 12:32:01 localhost kernel: [17326754.224000] usb 4-4: new high speed USB device using ehci_hcd and address 3
Jul 22 12:32:01 localhost kernel: [17326754.364000] scsi1 : SCSI emulation for USB Mass Storage devices
Jul 22 12:32:06 localhost kernel: [17326759.368000]   Vendor:           Model:                   Rev:
Jul 22 12:32:06 localhost kernel: [17326759.368000]   Type:   CD-ROM                             ANSI SCSI revision: 00
Jul 22 12:32:06 localhost kernel: [17326759.428000] sr0: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
Jul 22 12:32:06 localhost kernel: [17326759.428000] sr 1:0:0:0: Attached scsi generic sg0 type 5
Jul 22 12:32:06 localhost kernel: [17326759.428000]   Vendor: Toshiba   Model: USB 2.0 Ext. HDD  Rev: 1.15
Jul 22 12:32:06 localhost kernel: [17326759.428000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jul 22 12:32:06 localhost kernel: [17326759.432000] sd 1:0:0:1: Attached scsi disk sda
Jul 22 12:32:06 localhost kernel: [17326759.432000] sd 1:0:0:1: Attached scsi generic sg1 type 0

```

When I try to find out something about the file system it shows:

```

fdisk -l /dev/scd0
Note: sector size is 2048 (not 512)

Disk /dev/scd0: 22 MB, 22020096 bytes
255 heads, 63 sectors/track, 0 cylinders
Units = cylinders of 16065 * 2048 = 32901120 bytes

Disk /dev/scd0 doesn't contain a valid partition table


```

Somehow it hides everything, particularly the partition table!

Any help is highly appreciated,

gyeti

---

### Post by Daveth on 2007-07-22
yes, I see in the spec that it proudly vaunts its password protection but, like you, you might just think it was a mass-storage device and that is that.

[http://eu.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/individualOptions.do?ACTION=SHOW_ATTRIBUTES&OPTION_ID=118385&tab=1#1](http://eu.computers.toshiba-europe.com/cgi-bin/ToshibaCSG/jsp/individualOptions.do?ACTION=SHOW_ATTRIBUTES&OPTION_ID=118385&tab=1#1)

this model does not seem to have protection, so you could return it. I think it depends if you want to risk getting a refund/exchange by leaving it as it is and seeking another model, or try to overwrite the drive i.e. re-format it, probably by using a windows pc if one is to hand. Being read-only seems to blow out the option of tackling it from within Ubuntu, unless root can overcome such stuff. Might be worth asking Toshiba if it can be removed.
Very annoying for you though.

---

### Post by gyeti on 2007-07-22
Thanks for the link. It really doesn't say anything about password protection.

I live happily being 100% Microsoft-free and I intend to keep it this way. Using a windows machine to fix this problem is not really an option. Of course I used root privileges when I tried to access the disk. But the problem is more fundamental since the system can't find a partition table and the physical disk is somehow hidden.

If this can't be fixed, all linux users should be warned to stay away from Toshiba disks. I hope this info will spread.

---

### Post by Daveth on 2007-07-22
yes, the point of the link it that there is another shopping option for you. Sounds more trouble than it is worth over-coming the barrier they have installed, and that if I was you i would seek a refund or exchange with the other model.

---

### Post by gyeti on 2007-07-22
Oups, didn't notice that your link refers to a different model. I guess it's the same disk and I got the one with the propritary password crap on it. I still wonder if there is any way to get rid of this stuff. I'm also curious what the retailer will say when I ask him to exchange for the other model. Of course they didn't have the other one at the store. And I really got pissed at Toshiba anyway!

---

### Post by bodhi.zazen on 2007-07-22
You can try overwriting the disk with dban and re-formatting it .

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by gyeti on 2007-07-22
Thanks for the dban hint. However, this sounds a little dangerous since I certainly don't want to wipe out the main disk of my notebook. I'm also sceptical that it would work because on the dban site they write

"DBAN will automatically and completely delete the contents of any hard disk **that it can detect**"

Do you think it will detect a disk for which I cannot read a partition table? May be worth trying (after a complete backup of my machine:-( )

---

### Post by bodhi.zazen on 2007-07-22
Yea, you need to be VERY CAREFUL with dban

---

### Post by gyeti on 2007-07-26
OK, here is an update on this unpleasant affair.

I sent a support request to Toshiba, explaining my problem with the stupid windows password and the missing linux solution. The answer was a shame - of course exactly as anticipated. "No, you cannot circumvent the password protection. No, we cannot offer any help because we do not support linux. bla bla bla" **** them! Based on this I should have returned the disk no matter what. Unfortunately, curiosity drove me to find out how stupid they really are.

After eating tons of garlic, burning two pounds of incense and praying an hour to Tux for forgiveness, i took a 10 foot pole and switched on the bloody windows PC of our secretary, plugged in the disk and disabled the password protection. Wow, surprisingly no stroke hit me (yet). I removed the disk and plugged it into my linux box and, voila, a FAT32 disk popped up - along with a stupid CDROM containing this password crap.

Now I had a little fun with that buddy. fdisk and parted didn't tell much but with qtparted I found a hidden partition. I read out the first 1k block with dd, piped it through hexdump and checked if I could find out something. There was a bunch of windows and MSDOS related stuff, not really interesting. To make sure I could restore the original state, I used dd to backup the disk. I was still not decided whether or not I should return it to the retailer.

Next I used dd to overwrite the first sector of the disk and flatten all the nasty pre-installed stuff. After that, it was no problem to make partitions with parted and install ext3 file systems. Finally, I used encfs to create an encrypted virtual file system, which works just fine.

CONCLUSIONS
1) Stay away from Toshiba hardware!
2) If you don't, you may have to sell your linux soul to disable the f...ing windows password protection. (Maybe you don't need to if you're courageous enough to overwrite the first sector right away)
3) Afterwards, you can partition and format the disk at your will.
4) It seems that you have to live with the stupid CDROM popping up whenever you insert the disk.
5) Stay away from Toshiba hardware! 
If you can, avoid buying hardware from manufacturers hampering linux users. If I only had known, I wouldn't have touched this thing in my wildest dreams.

gyeti

---

