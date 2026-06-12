---
title: "Problems with HDD unrelated to SATA cable."
date: 2020-08-24
forum: General Help
---

### Post by diridibindy on 2020-08-24
These are the logs when booting the system. Sometimes after a system reboot, the Ubuntu boot thing disappears from BIOS/UEFI.

[These are the results from a full drive check for corrupted blocks]("https://imgur.com/a/vGFPQUE")

[And this is my previous thread about this issue of mine]("https://www.reddit.com/r/linuxquestions/comments/hjc9ph/some_kind_of_atahdd_problem_unrelated_to_sata/fwlvqqd/") 

```
blk_update_request: I/O error, dev sda, sector 614673024 op 0x0:(READ) flags 0x80700 phys_seg 33 prio class 0
ata2.00: status: { DRDY }
ata2.00: cmd 60/00:f0:80:2a:a3/08:00:24:00:00/40 tag 30 ncq dma 1048576 in
res 40/00:f0:80:2a:a3/00:00:24:00:00/40 Emask 0x10 (ATA bus error)
ata2.00: failed command: READ FPDMA QUEUED
ata2.00: status: { DRDY }
ata2.00: cmd 61/10:88:30:5f:1d/04:00:3a:00:00/40 tag 17 ncq dma 532480 out
res 40/00:f0:80:2a:a3/00:00:24:00:00/40 Emask 0x10 (ATA bus error)
ata2.00: failed command: WRITE FPDMA QUEUED
ata2.00: status: { DRDY }
ata2.00: cmd 61/b8:18:48:45:f0/02:00:29:00:00/40 tag 3 ncq dma 356352 out
res 40/00:f0:80:2a:a3/00:00:24:00:00/40 Emask 0x10 (ATA bus error)
ata2.00: failed command: WRITE FPDMA QUEUED
ata2.00: status: { DRDY }
ata2.00: cmd 61/48:10:00:40:f0/05:00:29:00:00/40 tag 2 ncq dma 692224 out
res 40/00:f0:80:2a:a3/00:00:24:00:00/40 Emask 0x10 (ATA bus error)
ata2.00: failed command: WRITE FPDMA QUEUED
ata2.00: status: { DRDY }
ata2.00: cmd 61/08:08:d0:65:95/00:00:4d:00:00/40 tag 1 ncq dma 4096 out
res 40/00:f0:80:2a:a3/00:00:24:00:00/40 Emask 0x10 (ATA bus error)
ata2.00: failed command: WRITE FPDMA QUEUED
ata2.00: status: { DRDY }
ata2.00: cmd 61/a8:00:58:dd:f0/02:00:29:00:00/40 tag 0 ncq dma 348160 out
res 40/00:f0:80:2a:a3/00:00:24:00:00/40 Emask 0x10 (ATA bus error)
ata2.00: failed command: WRITE FPDMA QUEUED
ata2: SError: { Handshk }
ata2.00: irq_stat 0x08000000, interface fatal error
ata2.00: exception Emask 0x10 SAct 0x4002000f SErr 0x400000 action 0x6 frozen
```

I would like to know if this is fixable, or if the problem will go away after swapping out the HDD.

---

### Post by TheFu on 2020-08-24
Any SMART data?

---

### Post by dragonfly41 on 2020-08-25
OP has burned a lot of energy in trying to crack this problem. Even to changing motherboard.

Following logs for debugging is difficult and I look for patterns or snippets of the log to try searches for related threads.

Found this .. [https://bbs.archlinux.org/viewtopic.php?id=182098](https://bbs.archlinux.org/viewtopic.php?id=182098)

Read final post in above giving link to a rather complex thread (way, way beyond my ken) .. 

[https://askubuntu.com/questions/145965/how-do-i-target-a-specific-driver-for-libata-kernel-parameter-modding](https://askubuntu.com/questions/145965/how-do-i-target-a-specific-driver-for-libata-kernel-parameter-modding)

...

Now all of the above side research might be a complete red herring.


[P.S.] And [this thread]("https://forums.opensuse.org/showthread.php/509021-SSD-throws-error-quot-WRITE-FPDMA-QUEUED-quot-during-boot") suggests looking into BIOS settibgs.

---

### Post by ActionParsnip on 2020-08-25
If you grab the Ultimate Boot CD you can test your drive using the manufacturers tool to make sure the drive is healthy

---

### Post by diridibindy on 2020-08-25
SMART is perfectly normal, except the number of turn ons/offs is a bit high because of my problems that cause me to force shutdown.

Drive was tested with some Windows Software, it is in the posts reddit link.

As for the threads that you gave me, sadly I went through all of them when this problem appeared. No issues mentioned there relate to mine
ASrock Bios settings don't have a way to change the speed of the controller and frankly, there doesn't seem to be an issue with speed.
On previously mentioned drive test, my HDD got 175Mb/s which is quite fast and what is should roughly be. 

I'm really at loss as to what is happening with it.

I should also mention that the drive was RMAed and tested by the seller. Drive was found to be in a normal state although the testing that they did couldn't probably notice such an issue.

The drive appears to "die" when there is a semi constant stream of data being recovered from it. Such as grabbing cached textures from HDD into the GPU while gaming.

While the system is basically on hold in terms of HDD, HDD doesn't seem to "die".

On windows it was "dying" without me doing anything. I suspect that was because of windows doing a lot of loading and storing action on boot and after boot.


I also must mention that after experiencing said issues on Windows I switched to Linux (that's why I'm even on Linux in the first place, though I like it here)

After the switch there were no issues for a few months and then they began, seemingly out of nowhere. 

Hmm, after the drive "dies" it boots into initframs(or something like that) after typing exit it says that the drive requires a manual fsck on /dev/sda2 which is my main partition. 

Should I dump the things that fsck fixes here?

---

### Post by Yellow Pasque on 2020-08-25
Try booting with "libata.force=noncq"

---

### Post by diridibindy on 2020-08-26
I'm sorry but if you can, please tell me how can I do that and briefly what it does?

---

### Post by Yellow Pasque on 2020-08-26
[https://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter](https://askubuntu.com/questions/19486/how-do-i-add-a-kernel-boot-parameter)

It should disable NCQ, which the error messages refer to. It may be causing the issue (or it may just be a symptom).

---

### Post by diridibindy on 2020-08-26
Will this solution have any downsides?

---

### Post by dragonfly41 on 2020-08-26
> As for the threads that you gave me, sadly I went through all of them  when this problem appeared. No issues mentioned there relate to mine.

I would just like to point to second link in my post #3 earlier which also refers to "libata.force".
I have no idea if it will help .. but perhaps some side research into this might be helpful.

---

### Post by Yellow Pasque on 2020-08-26
> **diridibindy said:**
> Will this solution have any downsides?

It may hurt disk performance. Google NCQ

---

### Post by diridibindy on 2020-08-26
Hmm, well it is just that the issues that lead to libata don't quite match with mine. Though, I have to say. When I applied that supposedly fix I didn't really experience any issues like what I had before. Though it was just one day and night as well be a coincidence.

Imma go check my journalctl log to see if issues were still happening.

Aight. 

So, the issue is still as active as ever

there are about 5-7k of lines like this in my journal. 

I experienced frequent freezes in games, but the drive didn't "die" (I didnt need to fix it with fsck, just had to live with freezes)

I will add on later if the issue with having to fsck the dsck arises. So far so good.

```
Aug 26 20:35:31 roman-desktop kernel: ata2.00: error: { ICRC ABRT }
Aug 26 20:35:31 roman-desktop kernel: ata2.00: status: { DRDY ERR }
Aug 26 20:35:31 roman-desktop kernel: ata2.00: cmd 35/00:a0:68:4c:29/00:00:3a:00:00/e0 tag 20 dma 81920 out
                                               res 51/84:a0:68:4c:29/00:00:3a:00:00/e0 Emask 0x10 (ATA bus error)
Aug 26 20:35:31 roman-desktop kernel: ata2.00: failed command: WRITE DMA EXT
Aug 26 20:35:31 roman-desktop kernel: ata2: SError: { Handshk }
Aug 26 20:35:31 roman-desktop kernel: ata2.00: irq_stat 0x48000001, interface fatal error
Aug 26 20:35:31 roman-desktop kernel: ata2.00: exception Emask 0x10 SAct 0x0 SErr 0x400000 action 0x6 frozen
Aug 26 20:34:16 roman-desktop kernel: ata2.00: error: { ICRC ABRT }
Aug 26 20:34:16 roman-desktop kernel: ata2.00: status: { DRDY ERR }
Aug 26 20:34:16 roman-desktop kernel: ata2.00: cmd 35/00:08:80:a4:5b/00:00:1f:00:00/e0 tag 29 dma 4096 out
                                               res 51/84:08:80:a4:5b/00:00:1f:00:00/e0 Emask 0x10 (ATA bus error)
Aug 26 20:34:16 roman-desktop kernel: ata2.00: failed command: WRITE DMA EXT
Aug 26 20:34:16 roman-desktop kernel: ata2: SError: { Handshk }
Aug 26 20:34:16 roman-desktop kernel: ata2.00: irq_stat 0x48000001, interface fatal error
Aug 26 20:34:16 roman-desktop kernel: ata2.00: exception Emask 0x10 SAct 0x0 SErr 0x400000 action 0x6 frozen
Aug 26 20:34:10 roman-desktop kernel: ata2.00: error: { ICRC ABRT }
Aug 26 20:34:10 roman-desktop kernel: ata2.00: status: { DRDY ERR }
Aug 26 20:34:10 roman-desktop kernel: ata2.00: cmd ca/00:08:58:1b:bc/00:00:00:00:00/e4 tag 6 dma 4096 out

```

After a quick game, the system died again, this time the drive doesn't even get detected in BIOS. While it is still detected in my Live environment.

There is a kernel log in attachments.

The picture is an aftermath of the system dying, file explorer style.

---

### Post by diridibindy on 2020-08-27
After a night in a cold turned off state the drive appears in BIOS again.

---

### Post by Yellow Pasque on 2020-08-27
So you've already tried different SATA cable, different SATA port, and even a different motherboard? Then it seems like you are fighting a bad drive.

There are a couple of other tricks you could try, such as jumpering the drive to force SATA 300 mode or using a Molex power adapter instead of a SATA power adapter if the drive has the appropriate connector (DO NOT connect both power connectors).

---

### Post by diridibindy on 2020-08-28
Yeah, I could try a different drive (well, when I get the money to do that)

It's just that I already RMAed the drive and they said it was fine.

Though I would guess they just didn't do the things that cause the drive to "die", probably just did a quick test, smart test and some file transfers.

Can you tell me what that 300 thing is and how to do it?

Quick edit:

Can somehow, CPU be the problem in this case?

---

### Post by vinchter on 2020-08-28
I ought to likewise make reference to that the drive was RMAed and tried by the vender. Drive was discovered to be in a typical state despite the fact that the testing that they did couldn't presumably notice such an issue. 

 
The drive seems to "bite the dust" when there is a semi consistent stream of information being recouped from it. [[COLOR=#000000][FONT=Calibri]new leaf hair guide[/FONT][/COLOR]]("https://acnlhairguide.net/")

---

### Post by Yellow Pasque on 2020-08-28
> **diridibindy said:**
> Can you tell me what that 300 thing is and how to do it?

[https://support-en.wd.com/app/answers/detail/a_id/1991/kw/jumper#satadesktopjump](https://support-en.wd.com/app/answers/detail/a_id/1991/kw/jumper#satadesktopjump)

---

