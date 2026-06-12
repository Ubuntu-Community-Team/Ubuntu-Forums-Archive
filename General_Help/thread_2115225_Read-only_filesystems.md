---
title: "Read-only filesystems?"
date: 2013-02-12
forum: General Help
---

### Post by EmilyRose on 2013-02-12
Hi there, I'm running Ubuntu 12.10 with GNOME Desktop installed alongside Unity. 4 days ago when my husband was at work, his suddenly started acting 'wonky', when he got home from work yesterday I realized that portions of it had been set to 'read-only' and after a bit of googling decided that it might be the hard drive failing, but thought I'd try re-installing. Initially I re-installed, w/o formatting his /home partition, which initially worked using Unity. But after I re-installed GNOME and updated it, it went back to not functioning... at which point I did a full reformat and it now (running Unity - with very little else installed) seems to be OK.

However, in the midst of this, my computer suddenly started doing the *exact same thing* - I'm now in the midst of backing up my data on our third 'backup' desktop which is usually my childrens' system (Xubuntu 12.10). 

When I restart my system it says there are errors in the /home partition and asks if I want to fix them, when I say yes, it seems to and then boots OK... but the next time I shutdown/reboot it does this again, and after working on it for a couple of hours the file system will suddenly set itself to 'read only'... which is exactly what his was doing. 

Any thoughts or suggestions?

---

### Post by matt_symes on 2013-02-12
Hi
 
What is the in the log file /var/log/syslog ?
 
Kind regards

---

### Post by EmilyRose on 2013-02-12
Lots... I'm trying to get a browser to open on it, but not a lot of luck... 

Towards the end are several dozen lines similar to this:

... kernel: [428xx.4xxxx] iwlwifi: 0000:0x:00xx fail to flush all tx fifo queus

---

### Post by matt_symes on 2013-02-12
Hi
 
Let's try to narrow the syslog output down a bit.
 
Please post the output of
 
```
egrep 'sd[a-z]' /var/log/syslog
```

Kind regards

---

### Post by Seb71 on 2013-02-12
See this bug:
[Sudden Read-Only Filesystems]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1063354")

---

### Post by EmilyRose on 2013-02-12
Feb 12 12:20:55 Final-Frontier kernel: [    1.071058] sd 1:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
Feb 12 12:20:55 Final-Frontier kernel: [    1.071099] sd 1:0:0:0: [sda] Write Protect is off
Feb 12 12:20:55 Final-Frontier kernel: [    1.071102] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
Feb 12 12:20:55 Final-Frontier kernel: [    1.071127] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Feb 12 12:20:55 Final-Frontier kernel: [    1.096029]  sda: sda1 < sda5 > sda2 sda3
Feb 12 12:20:55 Final-Frontier kernel: [    1.096793] sd 1:0:0:0: [sda] Attached SCSI disk
Feb 12 12:20:55 Final-Frontier kernel: [    2.473485] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
Feb 12 12:20:55 Final-Frontier kernel: [    2.829481] sd 6:0:0:0: [sdb] 7813120 512-byte logical blocks: (4.00 GB/3.72 GiB)
Feb 12 12:20:55 Final-Frontier kernel: [    2.831108] sd 6:0:0:0: [sdb] Write Protect is off
Feb 12 12:20:55 Final-Frontier kernel: [    2.831111] sd 6:0:0:0: [sdb] Mode Sense: 03 00 00 00
Feb 12 12:20:55 Final-Frontier kernel: [    2.832013] sd 6:0:0:0: [sdb] No Caching mode page present
Feb 12 12:20:55 Final-Frontier kernel: [    2.832015] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Feb 12 12:20:55 Final-Frontier kernel: [    2.835971] sd 6:0:0:0: [sdb] No Caching mode page present
Feb 12 12:20:55 Final-Frontier kernel: [    2.835974] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Feb 12 12:20:55 Final-Frontier kernel: [    2.836850]  sdb: sdb1
Feb 12 12:20:55 Final-Frontier kernel: [    2.839847] sd 6:0:0:0: [sdb] No Caching mode page present
Feb 12 12:20:55 Final-Frontier kernel: [    2.839850] sd 6:0:0:0: [sdb] Assuming drive cache: write through
Feb 12 12:20:55 Final-Frontier kernel: [    2.839851] sd 6:0:0:0: [sdb] Attached SCSI removable disk
Feb 12 12:20:55 Final-Frontier kernel: [   15.624144] Adding 15625212k swap on /dev/sda2.  Priority:-1 extents:1 across:15625212k 
Feb 12 12:20:55 Final-Frontier kernel: [   16.116298] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
Feb 12 12:20:55 Final-Frontier kernel: [   16.962782] sd 7:0:0:0: [sdc] Attached SCSI removable disk
Feb 12 12:20:55 Final-Frontier kernel: [   66.941600] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
Feb 12 12:22:57 Final-Frontier udisksd[2217]: Mounted /dev/sdb1 at /media/emily/4193-B5A2 on behalf of uid 1000

---

### Post by EmilyRose on 2013-02-12
Ok, just read through the bug report, sounds right... is there a way to install an older linux kernel w/o re-installing?

---

### Post by SeijiSensei on 2013-02-12
When you see the GRUB screen at boot, do you see a reference to "previous Linux kernels"?  Take a look in there and have it run the (n-1)th kernel.  If you don't see the GRUB menu at all, hold down the Shift key while booting.

If everything is fine with the older kernel, come back, and we'll work out how to make it default.

---

### Post by matt_symes on 2013-02-12
Hi

Interesting bug report that is obviously affecting a number of people.

@Emily. I also have an ideapad; a Lenovo S206 and i am not seeing this problem.

If you need other kernels then look here.

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

At the moment i am running 3.8....rc4 with no problems.

```
matthew-S206:/home/matthew % uname -r
3.8.0-030800rc4-generic
matthew-S206:/home/matthew % 
```Kind regards

---

### Post by EmilyRose on 2013-02-14
Yeah, I had no problems up untill a few days ago, on either system. Mine goes into read-only only very occasionally, and so far I have been succesful in unlocking it by simply rebooting and telling it to 'fix' the problems it finds. Once I did have to boot into a live-image and do sudo dpkg-reconfigure -a - and that cleared it up and allowed the above to work. 

However, my husbands' system is not fairing so well. I did a full clean install of 12.10 and it worked fine for a couple days, but as of an hour or so ago, is back locked and none of the above is working :( I'm about to write a blog post about it, in hopes of drawing some additional attention to it... I don't know what else to do besides *another* clean install... however, doing so every couple of days doesn't seem reasonable...

---

### Post by TheFu on 2013-02-14
Perhaps keeping at least 1 system on an LTS release (12.04) would be a good idea?

---

### Post by EmilyRose on 2013-02-14
His was actually still on 11.10 when it started after installing some new updates. I do have an older desktop running Xubuntu that I used when they were both (briefly) down :)

In anycase, I've posted about this on my blog ([http://todoentiempo.wordpress.com/2013/02/14/read-only-filesystem/](http://todoentiempo.wordpress.com/2013/02/14/read-only-filesystem/)) and have gotten a couple of replies already... so I'm hopeful that I'll get it figured out, eventually :)

---

### Post by EmilyRose on 2013-02-15
I'm probably jinxing myself by posting this, but after blogging about it it was suggested that system time might be badly configured. Since running: 

sudo ntpdate time.nist.gov us.pool.ntp.org ntp.ubuntu.com north-america.pool.ntp.org pool.ntp.org && sudo hwclock &#8211;systohc

everythings been fine... So, if anyone else should stumble upon this post at a future date, barring any further updates, give it a shot :p

---

### Post by EmilyRose on 2013-03-05
And... its back.  I know I did a rather large update on Sunday night with it reappearing yesterday once, and this morning I've already had to reset 3x.

---

### Post by matt_symes on 2013-03-05
Hi

Have you tried disabling power management on the drive ?

```
sudo hdparm -B 255 /dev/sda
```

It may chew up your battery a bit but it may also stop the problems you are having (worth a try).

Run the command at startup for a while and if it works, we can look at making it permanent by editing 

```
/etc/hdparm.conf
```

Kind regards

---

### Post by EmilyRose on 2013-03-06
The last time I rebooted I re-ran the instructions for time for the 3rd time (sudo ntpdate time.nist.gov us.pool.ntp.org ntp.ubuntu.com north-america.pool.ntp.org pool.ntp.org && sudo hwclock --systohc) and it hasn't *knock on wood* reoccured since then... This is the most fustrating bug I have encountered on a GNU/Linux system in years. I'm nervous to work on much of anything offline as I don't want to loose work when my harddrive randomly stops saving.

---

### Post by matt_symes on 2013-03-06
Hi

```
sudo ntpdate time.nist.gov us.pool.ntp.org ntp.ubuntu.com  north-america.pool.ntp.org pool.ntp.org && sudo hwclock  --systohc
```

If you believe the above command is helping your system then adapt it and add it as a daily cron job.

BTW:

When the filing system has gone read only, if you run this command does it return a date in the future ?

```
sudo dumpe2fs /dev/sda1 | grep -i "last mount time"
```

Change sda1 as required.

Kind regards

---

### Post by schragge on 2013-03-06
> **matt_symes said:**
> 
If you believe the above command is helping your system then adapt it and add it as a daily cron job.
As it is a laptop I'd rather install [anacron]("http://manpages.ubuntu.com/manpages/precise/en/man8/anacron.8.html"). But if it is (semi-)permanently connected to Internet, then [ntp]("http://manpages.ubuntu.com/manpages/precise/man8/ntpd.8.html") daemon will do better job than ntpdate.
BTW, you can put the time servers into */etc/default/ntpdate*, and use [ntpdate-debian]("http://manpages.ubuntu.com/manpages/precise/man8/ntpdate-debian.8.html") instead of ntpdate (it comes together with ntpdate in the same package).

---

