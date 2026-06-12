---
title: "Anything put in my hard disk goes to trash"
date: 2007-06-05
forum: General Help
---

### Post by Jellyffs on 2007-06-05
Hello,

I've been a while now on Linux system as an end-user, and I've never seen such weird problem. That weird problem just made me lose 230Go of data... (I might seem calm but I'm not ;)  )

_Main problem_:

I have an external hard disk through Firewire (a "Mybook" from western digital). Any data that I put in it, appears straight away in my trash bin also... So last time I empty my bin, I lost these 230Go in 10 seconds....:shock:

I won't go through a big description, I think this video will talk better:

[http://dl.free.fr/zKeLhhmE/mavideo-beryl.avi](http://dl.free.fr/zKeLhhmE/mavideo-beryl.avi)

As you can see, this is rather anormal, and problematic... 

Thanks,

Alex.

---

### Post by tgalati4 on 2007-06-05
Cool video.  The wobbly windows are neat.  What does dmesg say when you first attach the firewire disk?  What does df -h say?  Could it be a device naming problem--internal SATA vs external SCSI both being /dev/sd*?

Is this a permanently mounted drive using /etc/fstab or a hotplug automount?

If one, then try the other and see if the behavior changes.

Put a piece of black tape over the trash bin icon, so you won't empty it so quickly.

---

### Post by Jellyffs on 2007-06-05
Thanks for the reply!

Yeah, I totally forgot to talk about this:

I use fstab rather than automount function. Here is the line:

```
/dev/sdc1  /MyBook         vfat    defaults,user,noauto         0       2
```Now, if I "umount" it, and turn it off I get:

```
[ 2908.844000] ieee1394: Error parsing configrom for node 0-00:1023
[ 2908.844000] ieee1394: Node suspended: ID:BUS[0-00:1023]  GUID[0090a991e011218
```Then I turn it on, it gets mounted straight away, according to what I wrote in fstab:

```
[ 2930.344000] ieee1394: Node resumed: ID:BUS[0-00:1023]  GUID[0090a991e011218b]
[ 2930.344000] scsi8 : SBP-2 IEEE-1394
[ 2931.460000] ieee1394: sbp2: Logged into SBP-2 device
[ 2931.464000] ieee1394: sbp2: Node 0-00:1023: Max speed [S400] - Max payload [2048]
[ 2936.964000] ieee1394: sbp2: aborting sbp2 command
[ 2936.964000] scsi 8:0:1:0: 
[ 2936.964000]         command: Inquiry: 12 00 00 00 24 00
[ 2938.828000] scsi 8:0:1:0: Direct-Access     WD       2500JS External  106a PQ: 0 ANSI: 4
[ 2938.832000] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
[ 2938.832000] sdc: Write Protect is off
[ 2938.832000] sdc: Mode Sense: 11 00 00 00
[ 2938.832000] sdc: cache data unavailable
[ 2938.832000] sdc: assuming drive cache: write through
[ 2938.836000] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
[ 2938.836000] sdc: Write Protect is off
[ 2938.836000] sdc: Mode Sense: 11 00 00 00
[ 2938.840000] sdc: cache data unavailable
[ 2938.840000] sdc: assuming drive cache: write through
[ 2938.840000]  sdc: sdc1
[ 2938.848000] sd 8:0:1:0: Attached scsi disk sdc
[ 2938.848000] sd 8:0:1:0: Attached scsi generic sg2 type 0
jelly@superdupont:~$ 
```Looks "ok" to me... 

And:

```
jelly@superdupont:~$ df -h
Sys. de fich.            Tail. Occ. Disp. %Occ. Monté sur
/dev/sda2             9,7G  4,4G  4,8G  48% /
varrun               1014M   92K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb           1014M  100K 1014M   1% /proc/bus/usb
udev                 1014M  100K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   23M  991M   3% /lib/modules/2.6.20-16-generic/volatile
/dev/sdb1             276G  238G   24G  91% /BigMama
/dev/sda1             9,8G  4,6G  5,3G  47% /Windows
/dev/sda4              56G   11G   42G  21% /home
192.168.0.1:/FATASS   184G  135G   41G  77% /FATASS
/dev/sdc1             233G   32K  233G   1% /MyBook
jelly@superdupont:~$ 
```That's seems pretty clean also.

Now, if I use automount function, I get the same result, the file appears in the trash bin. And If I have a look at the "properties" of this file (the one in the trash bin), it says it's on the disk... 

Another detail, I have the "hidden files shown" function activated in Nautilus, but no ".trash" folder appear in my disk... what the... ?!

---

### Post by fuse1001 on 2007-06-05
I think this same thing might explain why my entire drive emptied when I just emptied the trash for the first time.  I don't have everything backed up GULP.  Is there any way to salvage the files????

I'm brand new to Ubuntu/Linux so please treat me gently - words of one syllable etc. if I need to do anything in terminal.

:shock:  :cry:  [-o<

---

### Post by tgalati4 on 2007-06-06
I'm a Dapper Drake user, and I've never seen anything like this before.  Someone using Feisty will have to weigh in on what is going on.

In the meantime, comment out the fstab entry and let automounter do its thing and see if the behavior changes.  There is certainly something serious and strange going on.  Back up your data and burn a Dapper Live CD if you need a more predictable system in the meantime.

---

### Post by Jellyffs on 2007-06-06
I reinstalled the system last night, kept my /home and any other partition... But I have big suspicions on the "Trash applet", as I noticed some weird behaviours from it in the past (I put something in it, and it acts as if there weren't anything or the contrary).

I'll follow you advice if it happens again, and will report it as a bug.

Thanks.

---

### Post by strabes on 2007-06-06
This makes me nervous because I have a WD Mybook as well. I use KDE though.

---

### Post by 3006828 on 2007-06-06
hahahah what an awesome situation. :P

---

### Post by Jellyffs on 2007-06-11
Ok, got some news.

This is a confirmed bug. Someone found a way out on the french forum:

Delete this file:

```
.gnome/gnome-vfs/.trash_entry_cache
```

And reboot your machine, so Gnome can restart completely, and create a new ".trash_entry_cache".

Alex.

---

### Post by Tulsapoke on 2007-09-04
> **Jellyffs said:**
> Ok, got some news.

This is a confirmed bug. Someone found a way out on the french forum:

Delete this file:

```
.gnome/gnome-vfs/.trash_entry_cache
```

And reboot your machine, so Gnome can restart completely, and create a new ".trash_entry_cache".

Alex.

I had this exact same problem with my hard drive basically turning into a giant trash receptacle.  Luckily I noticed the trash had all my stuff in it before I hit the empty button.  Your fix fixed it in seconds!  Thanks.

Everything was fine on this drive until I gave it a permanent mount point and fstab entry, at that point everything on the drive was considered trash for some reason.

---

### Post by Jellyffs on 2007-09-05
thanks for the reply. Hope this bug get sorted soon...

---

### Post by RIVE on 2007-12-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/gnome-vfs2/+bug/119448](https://bugs.launchpad.net/ubuntu/+source/gnome-vfs2/+bug/119448) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I'm using Gutsy AMD64 and just "delete" about 120 G of music and ISO images from one of my HD's, at least i noticed on time that all my files where in the trash, this bug is marked as a "low importance", for me is not low importance, thinking of  moving to Debian.

---

