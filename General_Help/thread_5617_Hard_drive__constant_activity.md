---
title: "Hard drive : constant activity ??"
date: 2004-11-20
forum: General Help
---

### Post by troutrou on 2004-11-20
That's a weird one.

My hard drive is CONSTANTLY working !

It's periodic/cyclic, every 3 seconds or so , it works for half a second... like "ggrrr........ggrrrr..........grrrr.....grrrrr....", and so on. it NEVER stops.

it's not noticeable during the day as there is always background noise and I often put music, but at night, when everything is quiet, and I try to concentrate on reading an on-line resource (ncurses howto at present) there is nothing to be heard but all the little noises emanating from the compouter, and I can't concentrate because of this periodic noise. Constant noise like the fans, or the hard drive spinning, is not a problem, but this little "grrr....grrr" noise now drives me completely mad now !!! Help. :o(((

I don't know what the driv eis doing, writing or reading, but it does work !

Regardless of what I am doing or not doing, whether there are apps running or not, the hard drive always acts as if it were working every 3 seconds !!!

Never stops.

Given it appears to be completely unrelated to what app is running, and given I can' t see any reason why Gnome or X would need to use the drive, I assume this could be kernel related ? After all he is the one responsible for swap etc, so is already used to managing hard drive activity when he feel slike it, no ?

Now, I could be wrong, but I can't remember that my previous distro (Mandrake 9.2) had this problem. It was using the previous kernel, 2.4 I think.

Could this really be kernel related ? Does someone here knows his onions about kernels, is it likely to cause this problem, is this a known issue ? 
If it is, does Ubuntu provide a 2.4 kernel ??

I suppose if one has a very noisy computer and puts is several meters away from the screen/keyboard then you can't hear it, but my computer is not that noisy and sits on the table only 2 feet from me so I can hear it and it does drive me real mad now. :o(((

No, I don't want to put the tower case on the floor, I like to have it on the table, I find it much more practical.  And I don't have the space to put it farther away from me either. So I really need to sort the root cause of this problem !!! :o(


Thanks for sharing similar experiences or ideas/info/suggestions on what could cause this... :o(


Vince.

---

### Post by troutrou on 2004-11-20
Update: installed a 2.4 kernel from synaptic.  Problem is still exactly the same :o(

---

### Post by wallijonn on 2004-11-20
did you set it up as Reiserfs? or ext3?

---

### Post by jdong on 2004-11-20
That is abnormal. What filesystem are you running?
 
 Switch back to a 2.6 kernel.. that probably isn't the problem!!
 
 
 Does 'top' show any processes using CPU while your computer is idle?
 
 Give us more system specs: RAM, swap setup, etc.

---

### Post by ynef on 2004-11-21
Try adding noatime as an option in your /etc/fstab -- the atime option keeps track of the files' access times, which is pretty pointless unless you specifically need that feature.

[http://libranet.com/support/2.8/0417](http://libranet.com/support/2.8/0417)

---

### Post by troutrou on 2004-11-21
Thanks for the replies.

I tried the noatime options it does seem to improve things a little bit :-) but it still does it, only less frequently. Maybe some other parameters of my fstab need 'tuning' ? Or maybe I didn't put the 'noatime' parameters in the right place on one of the partitions ?
I reproduced it below. To start with, what does the last two parameters "dump" and "pass" mean ? Maybe there are not set properly/ideally.

Fiule system: I let Ubuntu partition automatically. As you can see from my fstab, apparently it used ext3 for both the root and home partitions. if another file system is preferable, then I guess I can't convert ext ? I guess I must lrepartition and lose all data ? I don't mind (data are safe, on separate drive, hdd1), if it solves the problem

Kernel : yep, installed a 2.4 but it didn't change a thing so now back to using the 2.6 K7

"TOP": thanks for pointing me to this text app, seems nicer than Gnome's graphical front end. I can't see any activite at all. Only process is "XFree86" that uses 1.3%, and "cupsd" that uses 0.3 every now and then. But due to the refresh rate of 'TOP', it hard to say if cups happens at the same time as the hard drive spurious activity. Although so far, that's my only clue so why not. What is "cupsd", does it have to do with the printing server ? How can I switch it off, just to see if it makes any difference ?

Specs: 

Motherboard : MSI K7 420 Pro (AMD processor)
RAM: 512 MB (PC 2100)
Processor: AMD Athlon XP 1700+
SWAP: according to gnome system monitor, device section, Ubuntu used 252MB for the swap partition, and mounted it  in /dev/shm with a "tmpfs" filesystem.

Maybe Ubuntu/the Kernel does not handle very well the IDE controller of my motherboard ? I will try re-installg Mandrake 9.2 on another hard-drive, see if it does it or not, can't remember now, I think it doesn't.

# /etc/fstab: static file system information.
## <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,noatime,errors=remount-ro 0       1
/dev/hda5       /home           ext3    defaults,noatime        0       2
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdd1       /mnt/Data       vfat    noatime,umask=0,codepage=850,iocharset=iso8859-15 0 0
/dev/hdb4        /media/zip0     auto    rw,user,noauto  0       0
/dev/sda4        /media/zip1     auto    rw,user,noauto  0       0


I am glad that this is not normal, it means there is hope it can be cured...

Regards,

Vince

---

### Post by oddabe19 on 2004-11-21
It sounds like it's trying to access swap non-stop, Swap (iirc) should be 1.5x's the amount of memory.  For example, since you have 512 megs, i would make at least a 700 meg swap partition, i'd rather go with 1 gig.  I don't use swap because I have 1 gig of memory, and i almost never run out.

Anyway, Try increasing the swap partition, that amount seems really low.  Do you have anything running in the background (like a constant server back up) or something that always writes to your hard drive in real time? cause that'll do it too.

[edit] Now that i reread your post, it sounds like you didn't even make a swap partition, make one, and make it 700 megs or more, cause you could be always running out of memory (for some unknown reason).

---

### Post by troutrou on 2004-11-21
*> It sounds like it's trying to access swap non-stop, Swap (iirc) should be 1.5x's the amount of memory.  *

Most of the time, like tirght now, it uses well under 200MB of physical RAM, which means I have 300MB still available, so in pratice it never uses swap, so I guess even if I had no swap like you, it wouldn't change a thing ?

[I]> Do you have anything running in the background (like a constant server back up) or something that always writes to your hard drive in real time? cause that'll do it too.
[/I]

Yes, it feels as thought there is a thread constantly torturing my hard-drive, but I do'nt have anything fancy, just a very basic home desktop install. As I said, looking at the "top" command, I can't identify a thread that comes up at the same time as the drive's spurious activity. So it must be a thread that uses so little CPU load that 'TOP' doesn't even show it. 
What would be great, is to have a way to "trace" what processes are accessing the filesystem. Sure must be some system utility that can do that, but where is it ! :-/

*> Now that i reread your post, it sounds like you didn't even make a swap partition*

I didn't make anything, I let the Ubuntu installer partition automatically. The nly thing I asked it, is to have a distinct partition for /home.
According to my etc/fstab, Ubuntu did make a partition for swap, it's hda6.
I did try to partition myself "by hand", but I don't really what I am doing, and every time, I got a fatal error saying GRUB could not be installed. So had to gobackwards, to the partitioning step again. Did that half a dozen times, always got a GRUB error. In the end, I let Ubuntu partition itself and it woked...this is the only reason why I let it partition itself.  I think my proble is that on my hard drive I have a first partition for Windows XP, which is noted as "primary". And when I go to create the other partitions for Ubuntu, it asks me if I want a primary or logical partition, and I don't really know what to answer. Tried several configurations (all primary, XP primary and all Ubuntu partition logical, and also XP and root partition primary and other partitions as logical) but I would always get a GRUB fatal error :o(

---

### Post by troutrou on 2004-11-21
[QUOTE=ynef]Try adding noatime as an option in your /etc/fstab -- the atime option keeps track of the files' access times, which is pretty pointless unless you specifically need that feature.

[http://libranet.com/support/2.8/0417](http://libranet.com/support/2.8/0417)[/QUOTE]

noatime helped.  On you web page it also talks about a daemon called "noflushd".

I had a look ain synpatic and found it. The description makes it sound like it could help, so installed it. Synaptic automatically started the daemon.

But where in Gnome, can I see all the daemons, and start/stop them at will, and configure them ? In Marndrake I used to have a system utility for that, but I can' t seem to find a similar program in Gnome ? Is there a new package I should install ?

Vince

---

### Post by jdong on 2004-11-21
Try turning off swap temporarily with **swapoff /dev/hda6**. Do you still get thrashing?

---

### Post by troutrou on 2004-11-21
"Noflushd" worked, after a few minutes, it spinned down the hard drive(s, both I think ?), but only seconds later, it spinned up again so as to perform its favorite spurious activities... :o( 

When discs where "turned off" though, I enjoyed 10 seconds of a near silent PC, feels really superb. 

Vince

---

### Post by troutrou on 2004-11-21
[QUOTE=jdong]Try turning off swap temporarily with **swapoff /dev/hda6**. Do you still get thrashing?[/QUOTE]

Yes, still does it :o(

---

### Post by p!=f on 2004-11-21
Could you post outputs from the following commands?
1) sudo hdparm -i /dev/hda
2) ps aux
3) lsmod
4) ls /etc/init.d/

Also check your system log for possible drive errors.

---

### Post by troutrou on 2004-11-21
[QUOTE=p!=f]Could you post outputs from the following commands?
1) sudo hdparm -i /dev/hda
2) ps aux
3) lsmod
4) ls /etc/init.d/

Also check your system log for possible drive errors.[/QUOTE]

I redirected the output of these commands to text files, which I have uploaded with this message... see attached:

hdparm.txt
ps_aux.txt
lsmod.txt
init.d.txt

To help a bit with reading the lsmod file, my peripherals are :

IDE :  two (system + data) hard drives, one DVD drive, one IOMEGA ZIP 100  drive
PCI : TV card, Ethernet controller, SCSI Adaptec Controller
SCSI peripherals : AGFA Snapscan 1236s scanner
Ethernet peripherals : Cable modem for internet access
AGP: Video ATI Rage 128 Pro
Parallel port: IOMEGA ZIP 100 drive (yes, another one ;o) + Printer HP LaserJet 6P

To help with ps aux, here are the apps I had running when executing the ps command:

- Volume control / mixer
- Nautilus browser window
- E-mail : Evolution
- Web browser : Epiphany
- Acrobat reader
- Gnumeric (Gnome's Spreasheet)
- Gnome terminal, of course ;-)

Thank you so very much for taking the time to look at all the data, I really appreciate it very much....

Regards,

Vince

---

### Post by p!=f on 2004-11-22
I'm not sure if following helps but you never know... :)
Try to stop these services:
```

evms
mdadm
mdadm-raid
powernowd

```
Tweak your harddrive by editing /etc/hdparm.conf (well documented, put it at the very bottom):
```

/dev/hda {
        mult_sect_io = 16
        io32_support = 1
        write_cache = on
        dma = on
}

```
and restart hdparm.

Can you feel any difference?

---

### Post by troutrou on 2004-11-22
Services ? Well.... HOW do I start/stop them ?

As I said earlier in this thread, I used to use Mandrake which has a GUI to control services. But in Ubuntu, I didn't find a similar program ! So I guess I must tweak some configuration file by hand . Which file  is it ? How to modifiy it ? Please help :-)

Hdparm : had a look at the "man" page for it. Looks brilliant, many options to control the IDE driver and hard drives. Several options to control the speed/power managment, and even an option, although experimental only, that is designed specifically to control the NOISE the heads make when accessing the drive ! Incredible, Linux rocks :-)

The problem : how do I "restart" hdparm ? I modified the hdparm.conf file as you suggested, then typed "hdparm /dev/hda", but I don't think it did anything.
What do I have to type exactly on the command line, to make hdparm re-read it's configuration file and apply the changes accordingly ? Can ALL settings be applied  "live", or do some of the options require to re-start the session, or even worse, reboot the machine altogether ??

Sorry to ask even more questions...  only trying to understand what I am doing ! ;o)

regards,

Vince.

---

### Post by p!=f on 2004-11-22
```

sudo /etc/init.d/<initscript> <start|stop|restart|force-reload>
*example:*
sudo /etc/init.d/gdm restart
sudo /etc/init.d/hdparm start

```

---

### Post by troutrou on 2004-11-22
> sudo /etc/init.d/<initscript> <start|stop|restart|force-reload>

Ah thanks, that's simple enough for me  :o)

I stopped all the services you said, but it didn't change anything sadly :o(
I will try stopping more services, like atd, cron, sysklogd, postfix, see if that helps :-/

I tried a ```
hdparm -B 0 /ded/hda
```, as according to the man page, it should put the drive in a super "economy" mode. But alas, all I get is 
```
 HDIO_DRIVE_CMD failed: Input/output error
```
Maybe that means my drive is too old and does not support this command ? :-/
It's a 40GB Western digital disk, is that too old already ? Maybe I should get a super modern drive (albeit small/cheap, as 40GB is plenty enough for my needs) just so as to be able to use all the nice options hdparm is capable of ?
However if I have to resort to buying a brand new hardrive, I would need to be SURE that it does support all hdparm power/noise functionalities.... but how to be sure.... :-/

It would still be ideal if we had a program that tell us what process(es) access the drive ! I mean, sure enough, the Kernel has to give permission for this process to access the drive, so said process must identify itself, no ? So, the kernel surely KNOWS the little b****d that keeps accessing my drive ! Can't believe there is not a little program somewhere to interrogate the Kernel about who accesses the drive.
I shall start hunting for such a program I guess.... :-/

Vince

---

### Post by p!=f on 2004-11-23
Hmmm... I was afraid of this. Nothing changed, right? I would bet something's wrong with the harddrive itself.
The best way to be sure what's going on would be to get another HDD and clone your partitions onto this one.

I had similar problem on an old 20GB Maxtor. It didn't make noise every 3 secs but every 5-7 mins. It wasn't even the system disk.
As soon as I replaced it with a new one, the noise had gone.

You may also take a look at the BIOS if there's something "wierd". 32-bit support for HDDs, PCI Latency Timer too high, ...

---

### Post by troutrou on 2004-11-23
I don't think there is anything wrong with th drive. I has never been "noisy" ;o)  with windows XP, nor Mandrake 9.2 nor Mandrake 10.1. It only does it with Ubuntu.

Maybe Hoary will be more quiet, you never know.

Anyway, I give up on this problem. I will just get moder drive so that it (hopefully) supports all the power and noise saving functionnalities that hdparm is capable of. Then change my power supply for a silent one, and resort to put my tower case under the table instead of on the table, next to my right ear...

So basically, "hardware" solutions rather than software ! ;o)

Thanks for your help anyway, especially for telling about 'hdparm', looks like a great program to me, which I will no doubt "play"  with ! ;o)

Regards,

Vince.

---

### Post by troutrou on 2004-11-24
UPDATE !!!  :-)

I have given up finding out what process access my drive all the time, but I have nonetheless managed to make it silent !

Thanks to hdparm's magic !  This is a truly great piece of program ! :o)

I fiddle with it, took the time to read the man page carefully, experimented a bit, and I eventually managed to mkae my drive silent !

Thanks to the 'acoustic managment' (as they call it) functions !

I typed 'hdparm -M 128 /dev/hda' and it instantly made my drive silent !

I tried loading big apps like OOo or Gimp, and it doesn't make ANY noise when reading ! And of course, I can't hear the intermittent "grr.... grrr" noise anymore either ! :o)

So, in short, hdparm is a REALLY sweet piece of code, I love it !!! :o)

Vince, super happy with hdparm....

---

### Post by p!=f on 2004-11-24
Awesome news. Thanks for sharing the result with us.
Glad to hear you're saving your nerves. :)

---

### Post by wayover13 on 2004-11-24
[QUOTE=troutrou]Thanks to hdparm's magic !  This is a truly great piece of program ! :o)

I fiddle with it, took the time to read the man page carefully, experimented a bit, and I eventually managed to mkae my drive silent !

Thanks to the 'acoustic managment' (as they call it) functions !

I typed 'hdparm -M 128 /dev/hda' and it instantly made my drive silent !
[/QUOTE]

I don't really get this.  Were you concerned about just noise, or about the fact that unnecessary access to the HD was going on, which brings with it added wear and shorter HD life?  And maybe other problems?  Making it quieter is just hiding the problem, if you're concerned about those things.  I have the same situation as you, but I'm more concerned that my HD may give out sooner than I am about the noise.

James

---

### Post by troutrou on 2004-11-25
> I don't really get this.  Were you concerned about just noise, or about the fact that unnecessary access to the HD was going on, which brings with it added wear and shorter HD life?  

James, I was mad at the noise mainly. Sure, I was also a bit concerned about the wear and tear, but it appears that many daemons/services access the drive all the time anyway, be it system logs or file indexers or what have you , so I don't think that a quick squirt on the drive every 10 seconds is doing any harm, at least not any measurable harm in the practical life time of the disk.
Obviously, my precious data are on separate hard drive which spends 99% of it's time turned off. So at worst, but this won't happen anyway, I lose my system drive, which can be quickly restored from a backup/image if need be. It's a small 40GB 3.5" IDE drive, and these cost next to nothing now, actually my buddy gave an old spare 40BG disk he had lying around, because he couldn't bother putting it on Ebay and get only 5 bucks from it.

Obviously, from a technical point of view, and as a matter of principle, I don't find it very elegant to write to the disk all the time if it's not necessary. So, if you do find the root cause of the problem, I would still be interested to hear about your findings. :-)


Vince

---

### Post by sbn on 2005-02-27
If anyone else could contribute to this thread I would be happy too ...

I'm currently sitting at my laptop (Acer TM4501WLCi) with a 40gig seagate harddrive ...

I've tried all the "solutions" mentioned above - but unfortunately they didn't work in my case :( 
Apparantly my hd doesn't support accoustic management...

So ... when all comes to all, I still get that annoying "scratch" sound from the HD every 5 seconds or so 

Ideas ?
I do not have anything to keep it and surely no solution - but _could_ the kjournald be the culprit ? - it's set at 5 sec at bootup - but how do I change it ?

dmesg | grep kjournald:
"kjournald starting. Commit interval 5 seconds"

/sbn
Denmark

---

