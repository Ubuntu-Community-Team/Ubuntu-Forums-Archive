---
title: "Unable to play VCD"
date: 2024-05-24
forum: General Help
---

### Post by satimis on 2024-05-24
Hi all,

Just discover unable to play VCD but able to play audio CD

It worked before.  I have ripped VCDs to both .wav and .mp4 files.  The digital files work without problem.

Performed as follows:
Insert VCD and start VLC
Media -> Open Disc
(select) SVCD/VCD
-> Browse
/media/satimis/E0C8B186C8B15C0A
-> Play

No response.

But it works on audio CD

Please help.  Thanks

Regards

---

### Post by ActionParsnip on 2024-05-24
What is the output of:
```

lsb_release -a; uname -a; apt-cache policy vlc

```
Thanks

---

### Post by satimis on 2024-05-24
> **ActionParsnip said:**
> What is the output of:
```

lsb_release -a; uname -a; apt-cache policy vlc

```
Thanks
Hi,

$ lsb_release -a; uname -a; apt-cache policy vlc```

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.4 LTS
Release:	22.04
Codename:	jammy
Linux PC2A 6.5.0-35-generic #35~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Tue May  7 09:00:52 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
vlc:
  Installed: 3.0.16-1build7
  Candidate: 3.0.16-1build7
  Version table:
 *** 3.0.16-1build7 500
        500 http://hk.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
        100 /var/lib/dpkg/status

```
Thanks

Is the disc player having problem?

Regards

---

### Post by Holger_Gehrke on 2024-05-24
I do believe you need to give vlc the device that has the vcd and not the mountpoint. So /media/satimis/and_so_on_and_so_forth is wrong, it should be /dev/cdrom or /dev/sr0 or something like that. VCD is a format that doesn't have a real file system, the video is stored directly in the cd track as mpeg1 without any of the checksums you have for tracks with a filesystem so a sector is 2304 bytes instead of 2048 bytes data + 256 bytes checksums. There is a virtual filesystem your file manager will show you for a vcd and that contains a large file usually with the extension .dat. Opening that pseudo-file in vlc could work, too.

Holger

---

### Post by satimis on 2024-05-24
> **Holger_Gehrke said:**
> I do believe you need to give vlc the device that has the vcd and not the mountpoint. So /media/satimis/and_so_on_and_so_forth is wrong, it should be /dev/cdrom or /dev/sr0 or something like that. VCD is a format that doesn't have a real file system, the video is stored directly in the cd track as mpeg1 without any of the checksums you have for tracks with a filesystem so a sector is 2304 bytes instead of 2048 bytes data + 256 bytes checksums. 
Hi Holger,

Thanks for your advice.

Tried again;

Inserted VCD (it mounts automatically - showing 112412)

Start VLC
Media -> Open Disc
select SVCD/VCD
Disc device [/dev/sr0      ]  #(it is automatically selected)
Entry [0]     #(it is automatically selected)
Audio track [-1]   #(it is automatically selected)
subtrack [-1]   #(it is automatically selected)

-> Play

The picture is not clear

(please see screenshot attached)

Unmounted VCD and tried again with the same result.

I don't know WHY?  About one week before, the DVD writer worked without such a problem.  I was able to rip the VCD to .mp4 and .wav files

Is it the problem coming from the DVD writer or VLC or Ubuntu OS?

> 
There is a virtual filesystem your file manager will show you for a vcd and that contains a large file usually with the extension .dat. Opening that pseudo-file in vlc could work, too.

Could you please explain in more detail, allowing me to perform that test.  Thanks

Regards

---

### Post by Holger_Gehrke on 2024-05-24
Sorry, this took a while, I had to go and find a VCD in my archive to try it myself. It's from 2001, but it still plays. If I allow the disc to automount and open it in Thunar, I get several folders (cdi, ext, mpegav, seg, and vcd). In the folder mpegav there's a file named avseq01.dat of about 550 Megabytes. I remember being able to just open that file in a media player, but that was back in the Windows XP era. When I tried just now, I got an Input/Output error. The disc does play without problems in vlc, so the problem is probably the ... interesting ... structure of a vcd (look it up on Wikipedia, it's worth a read).

The screenshot you posted looks bad, but not unusually bad for vcd. Remember, it has a resolution of 352x240 (288 for PAL) and is compressed to take just 1150 kbit/sec (and that already includes sound ...). A badly compressed disc with a few read errors (remember, no error correction on vcd to have more space) might look like that or even worse. VCD was only ever meant to compete with VHS and be viewed on CRT screens.

Holger

---

### Post by satimis on 2024-05-25
> **Holger_Gehrke said:**
> Sorry, this took a while, I had to go and find a VCD in my archive to try it myself. It's from 2001, but it still plays. If I allow the disc to automount and open it in Thunar, I get several folders (cdi, ext, mpegav, seg, and vcd). In the folder mpegav there's a file named avseq01.dat of about 550 Megabytes. I remember being able to just open that file in a media player, but that was back in the Windows XP era. When I tried just now, I got an Input/Output error. The disc does play without problems in vlc, so the problem is probably the ... interesting ... structure of a vcd (look it up on Wikipedia, it's worth a read).

The screenshot you posted looks bad, but not unusually bad for vcd. Remember, it has a resolution of 352x240 (288 for PAL) and is compressed to take just 1150 kbit/sec (and that already includes sound ...). A badly compressed disc with a few read errors (remember, no error correction on vcd to have more space) might look like that or even worse. VCD was only ever meant to compete with VHS and be viewed on CRT screens.

Hi Holger,

The VCD which I'm using for this test is an old film VCD - The Guns of Navarone.  It consists of 2 discs.  I have already ripped  2 .mp4 files, disc-1.mp4 and disc-2.mp4.  They can be played on SMPlayer with clear picture but NOT on VLC.

This Ubuntu 22.04 PC has problem.  Please read my another thread;

PC power off and starting problem
[https://ubuntuforums.org/showthread.php?t=2497033&highlight=satimis](https://ubuntuforums.org/showthread.php?t=2497033&highlight=satimis)

Now the PC can boot with warnings at booting.  (pls refers to the screenshot attached)

I don't know whether the problem coming from the old VCD or VLC or this PC

I have already planned building an AMD Ryzen 9 12C 24T PC with 64G RAM onboard.  But I need finding time shopping for components.

I'll stop here and come back on the new AMD Ryzen 9 PC after having it built.

**[COLOR="#FF0000"]Re Burner:[/COLOR]**
**What you would recommend me to purchase: Bluray burner of DVD writer for the new PC**?  I don't burn disc frequently.  Thanks

Regards

Edit
===
SMPlayer
can't play disc-1 VCD
able  play disc-2 VCD

---

