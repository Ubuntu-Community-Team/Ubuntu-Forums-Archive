---
title: "ubuntu on a older system?"
date: 2023-06-23
forum: General Help
---

### Post by josephchrzempiec on 2023-06-23
Hello, I have a older system that has a odler linux that crashed and no logner working. The drive is still good but I can not find a linux that is supported on there. The drive is a 120Mb that has a Fat12 file system. When I plug it into my Pc it shows up as a floppy drive. I'm wondering If there is a older ubuntu even a server version that can work on the older system. It's a P2 200mhz processor with 120Mb of memory. does nayone know If there is any older ubuntu that will work on this drive?

Joseph

---

### Post by Rubi1200 on 2023-06-23
Hi,

Older Ubuntu versions would not be supported with updates of any kind, so I do not recommend this.

However, there are a few lightweight options out there:
[https://itsfoss.com/super-lightweight-distros/](https://itsfoss.com/super-lightweight-distros/)

I run Bodhi Linux on an old 1GB RAM netbook but have not tried with the limited RAM you have.

Some of the options in the link I posted will likely work though, especially something like Puppy.

---

### Post by guiverc on 2023-06-23
The *last* OS I recall running on a pentium II (even III) was Ubuntu 10.04 LTS or the 2010-April release (*from memory; if not it was 8.04 but I'm sure it was 10.04)*.  It may *not* have been the last that ran, but later non-LTS would reach EOL before 10.04 did & newer LTS releases required (i686/p4) or later as I recall.

As you're talking about something really old, you should only use it off-line.


Debian still supports *i386* (*i686 anyway* *in technical terms but ISOs are still labelled i386. but pII/III was i586 from memory*) but I can't recall what release of Debian supported PII/III (*too long ago sorry*), but it would be releases of the similar vintage.

(*I actually have an old system from that era on this desk alas AMD not intel.. it was kept as I liked the old nokia box as a white-noise generator when on standby; being rack mount its fan was always running**; at worst that box is where my release details are coming from but I'm sure it was 10.04 that my pII & pIII last ran*)

---

### Post by josephchrzempiec on 2023-06-23
Hello all, Thank you for the update. This system is for offline. The problem is this drive can only support fat12. I wish I can find a OS that can supoort it. I have tried to format the drive with fat16 and fat 32 it will not take and error out. Fat12 it can support.

---

### Post by qyot27 on 2023-06-23
> **guiverc said:**
> The *last* OS I recall running on a pentium II (even III) was Ubuntu 10.04 LTS or the 2010-April release (*from memory; if not it was 8.04 but I'm sure it was 10.04)*.  It may *not* have been the last that ran, but later non-LTS would reach EOL before 10.04 did & newer LTS releases required (i686/p4) or later as I recall.

As you're talking about something really old, you should only use it off-line.


Debian still supports *i386* (*i686 anyway* *in technical terms but ISOs are still labelled i386. but pII/III was i586 from memory*) but I can't recall what release of Debian supported PII/III (*too long ago sorry*), but it would be releases of the similar vintage.

(*I actually have an old system from that era on this desk alas AMD not intel.. it was kept as I liked the old nokia box as a white-noise generator when on standby; being rack mount its fan was always running**; at worst that box is where my release details are coming from but I'm sure it was 10.04 that my pII & pIII last ran*)

[The original Pentium is i586, Pentium Pro and higher were i686.](https://gcc.gnu.org/onlinedocs/gcc/x86-Options.html)  At least that's how GCC divvies it up.  I wouldn't be surprised if some use 'i686' to mean 'has SSE', which was introduced in the Pentium-III.

I have a Celeron 2 (Coppermine-128, so a stripped-down Pentium-III) machine that was my main setup until ~September 2015.  It was perfectly capable of running current Ubuntu (at the time, 15.04), so long as you were in LXDE or a similarly lightweight desktop environment.  Unity was too much for even the GeForce 6200 I have in there, to say nothing of the onboard graphics.

The last Lubuntu image offered for 32-bit is 18.04.5.  I can't remember exactly when 32-bit ISOs were dropped, but if Xubuntu is any indication, 18.10 was probably the last one.  The last GNOME-based Ubuntu to offer 32-bit was 17.04, but Server 17.10 still had a 32-bit ISO.

---

### Post by guiverc on 2023-06-23
> **qyot27 said:**
> [The original Pentium is i586, Pentium Pro and higher were i686.]("https://gcc.gnu.org/onlinedocs/gcc/x86-Options.html")  At least that's how GCC divvies it up.  I wouldn't be surprised if some use 'i686' to mean 'has SSE', which was introduced in the Pentium-III.

...

The last Lubuntu image offered for 32-bit is 18.04.5.  I can't remember exactly when 32-bit ISOs were dropped, but if Xubuntu is any indication, 18.10 was probably the last one.  The last GNOME-based Ubuntu to offer 32-bit was 17.04, but Server 17.10 still had a 32-bit ISO.

**Thanks**, I was writing purely from 'memory', which is *vague* on some details.. I do agree & recall reading at least one package that used the *i686* and SSE; a browser from memory - though wouldn't reliably recall which.

The last Lubuntu *i386* ISO we released was [18.04.5]("https://fridge.ubuntu.com/2020/08/14/ubuntu-18-04-5-lts-released/") (*it was the last i386 ISOs for any flavors; only [netboot 18.04.6]("http://archive.ubuntu.com/ubuntu/dists/bionic-updates/main/installer-i386/current/images/netboot/") was later that I recall; as all flavors were EOL by 18.04.6, and Ubuntu Desktop didn't include i386 at 18.04*;* I'm on the Lubuntu team thus why I recall this, though back then I split time equally between Lubuntu & Xubuntu*).

I never re-used my Lubuntu *[disco*] 19.04 *i386* thumb-drive, nor Xubuntu 19.04 *i386* thumb-drives, so even if I don't have the ISO files anymore, I have those (*in theory anyway; I see the Lubuntu thumb-drive, but can't see Xubuntu's green in my pile; but as not re-used I've only got to find it*).

Lubuntu's official *sunsetting i386* blog is [here]("https://lubuntu.me/sunsetting-i386/"), with Xubuntu doing the same during the same December month.... *disco* was still in ALPHA at the time, thus what I have wasn't an *officially released* product, but if the *alpha* ISOs were used for any installs, upgrades of packages would continue [until 19.04 reached EOL]("https://fridge.ubuntu.com/2020/01/23/ubuntu-19-04-disco-dingo-end-of-life-reached-on-january-23-2020/") with Ubuntu only disabling the *i386* builds in the *eoan* cycle (*pre-release actually or ~late beta, it was kept on for disco due to ISOs having been released during alpha stage*).  

My last pentium 4 box (*now recycled; it was i386 only*) had 19.04 & 19.10 installs on it.. the *eoan* install being used to perform a *verification-done* on a SRU fix too (*packages hadn't been disabled obviously then; though it was getting close as SRUs are required only on freezes/beta*).

I didn't use that pentium 4 box for any GNOME (3) testing, not even Unity 7 testing beyond 16.04 (*technically it may have run, but it felt more of a crawl*).. but yeah it ran *lighter* LXDE (GTK2), Xfce (GTK2/3), MATE (GTK2/3), LXQt (Qt5) etc fine.

---

### Post by SeijiSensei on 2023-06-24
128M is way too small for any modern Linux. The system I'm writing this on is using about 3 GB of memory.

---

### Post by SeijiSensei on 2023-06-24
> **josephchrzempiec said:**
> It's a P2 200mhz processor with 128Mb of memory. does nayone know If there is any older ubuntu that will work on this drive?

128M is way too small for any modern Linux. The system I'm writing this on is using about 3 GB of my 8 GB of memory.

---

### Post by josephchrzempiec on 2023-06-24
I'm okay with a older linux. This is a offline system as long as I can figure how which linux can run on this old drive.

---

### Post by guiverc on 2023-06-25
I still have a device from 1990s, pentium (mmx) with machine having a max'd out 64MB of RAM if I recall correctly (ie. pre-pentium-M) which had a windows system installed (*95 or 98; I can't recall*) that was *loaned* to me & thus I never erased the original OS/formatting... the original OS boots up if the system is turned on.

However I have a Puppy (Wary/5.3) install on that non-native file-system (*I can't recall what it is, maybe NTFS if not a FAT*) stored as a file, that is *triggered* by inserting & booting a *yellow 3.5" floppy* that starts linux & passes control to the system that I have stored on the original file-system meaning I can boot & use a GNU/Linux system to do what I wanted the box for.

( *the box was ancient when I was loaned/given it; but it was old enough to have a DB9/DB25 **serial port that allowed me to leave it in place & connect up to my then used cisco router using a cable I already had spare.. being laptop it used little space & was only ever going to be used locally.  It does exactly what I need of it, and I only had a single file to delete (& floppy to remove) if the original owner ever wanted it back *)

We can do almost anything, but is it worth it?  I'm aware that Ubuntu could (*early releases*) be installed as I installed Puppy Linux (Wary 5.3), but I'd not know how to do it today, and the effort that made the tools to do it were just abandoned I suspect.

---

### Post by yancek on 2023-06-25
>  The drive is a 120Mb 

If that is the case actually, the first iso of the first release of Ubuntu in 2004 was 4 times the size of your hard drive, over 500MB.  There is no way you would be able to install any version of Ubuntu.  You could not even put the iso on it as your drive is not large enough.  Some derivatives might be smaller but I doubt it.  Do you know the actual, accurate age of a drivthe computer/drive?  From the 1990's.  The only Linux systems I am aware of that would fit on a drive that small are Slitaz (80MB+) or Tiny Core 20MB+.

Ubuntu is unlikely to work if your computer is really old, the first release of Ubuntu being in October, 2004.  You might look at the 2 oldest, still existent Linux distributions to see if you can find an older version.  These would be Slackware and Debian.

---

### Post by josephchrzempiec on 2023-07-16
Hello all, Sorry I have been away in the hosptial and I'm still looking for a linux to run on floppy. Because of the file format I don't think ubuntu is the right choice. Sense I need a fat12 format the drive can only do. I'm not sure what to do next or to look into. I might need to figure out a way to get a drive that will fit in there and replace it with a larger drive and better file format. I'll post an update if anything happens. Thank you

---

### Post by Holger_Gehrke on 2023-07-16
Are you sure about that FAT12 limit ? I never heard about a hard drive that imposed any kind of limit on the file system put on it. And FAT12 means that it uses a File Allocation Table with 12 bits per entry so a maximum of 4096 clusters. That would make each cluster 60 sectors in size if you had the whole drive in one partition, and that's not allowed - the maximum cluster size is 4096 bytes. FAT12 really was meant for floppies.

Holger

---

### Post by MAFoElffen on 2023-07-17
120mb...
> 
ubuntu core, with an image size of 260mb, is the smallest ubuntu linux release to date.


---

