---
title: "Slow DVD ripping"
date: 2007-07-18
forum: General Help
---

### Post by dustintinsley on 2007-07-18
I am experiencing very slow DVD ripping speeds in Fiesty Fawn.  I have heard that this could be due to to DMA not being enabled, but from what I can tel, my DVD drive has it enabled.  What else could fix this problem?

---

### Post by stchman on 2007-07-18
> **dustintinsley said:**
> I am experiencing very slow DVD ripping speeds in Fiesty Fawn.  I have heard that this could be due to to DMA not being enabled, but from what I can tel, my DVD drive has it enabled.  What else could fix this problem?

What program are you using?  Yes it could be a BIOS setting.

---

### Post by dustintinsley on 2007-07-18
Tried both k9copy and winki the ripper.  Tried convrting the DVD to xvid.  The process takes up to 6 hours for one DVD.

---

### Post by underwater on 2007-07-29
I very much have this same problem.  My dvd drive's speed seems very slow.  The situation is more complicated, however, by it being on my laptop.  You see, I think my drive is IDE (PATA) but that it is attaching to a scsi interface or something weird that dell did internally.

Here is some data that might help someone help me

```

~$ hdparm /dev/scd0

/dev/scd0:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device



```
Also here is my fstab

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=78500afc-54be-414a-bd92-6c2f86a23078 /               ext3    defaults,error
s=remount-ro 0       1
# /dev/sda3
UUID=000c8785-7ad8-416d-b42e-4950692ada96 /home           ext3    defaults
  0       2
# /dev/sda2
UUID=bc30eff2-8821-4d45-8488-846746bfe138 none            swap    sw
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```



Please provide any assistance or ideas that you may have.  Burning dvd's at very low speeds and even reading dvd data disks takes FOREVER!  When I do burn a dvd, I get around 2x, a much lower speed than I used to get with Edgy.

Oh and I'm also running kubuntu 7.04

Thanks in advance

---

### Post by dragonwings on 2007-07-29
im using ubuntu 7.04 fiesty with k9 and kb3 i can do a 6-7 mb disc in 30 minutes
if there is any way i can help give me a command and ill post the result

---

### Post by FluffyElmo on 2007-07-29
Another possibility is that your DVD drive limits ripping speed. Mine (NEC 3500G) came with something called 'riplock' built in which limited DVD ripping to ~2x or so. I installed an unofficial firmware that among other things disabled this 'feature'. My drive is louder but now rips at full speed. It may be something else entirely but it's worth investigating if your drive has a similar feature and if firmwares are available.

---

### Post by underwater on 2007-07-29
For me a bad firmware isn't the problem as I've had much greater speeds in the past with Edgy and Dapper.  Is definitely something with Feisty.

---

### Post by FluffyElmo on 2007-07-29
Missed that part, I'm not sure what it would be. Your fstab entry is identical to mine and your hdparm results are consistent with my SATA hard disk, so I assume it's normal.

---

### Post by underwater on 2007-08-03
That's too bad.  now I'm really curious to know what the problem is.  I used to be able to rip a DVD is very short amount of time and now things are saying times as high as 67 hours which you know is just wrong.  I looked through dmesg and found nothing as well.  Does anyone else have an idea?

k3b burns really slowly too. :(  that is another terrible part to all of this.

---

### Post by WamBamBoozle on 2007-08-05
I could rip dvd's with ease on Dapper Dan. On Feisty this stopped working. It was painfully slow. I was getting frame rates of under half a frame per second.

I decided to throw caution to the wind and install all the multimedia stuff from Automatix. After rebooting, my ripping speed was back to 60 frames per second. Unfortunately, I don't remember what exactly I installed.

---

### Post by lee_connell on 2007-08-12
I have same exact hdparm results and using a DELL that has CD/DVD attached to sata.  /dev/scd0.  I have very very slow rip speeds and copying speeds.  This did work in previous versions for me as well.  I use 7.0.4.

---

### Post by ninja_in_pajamas on 2007-12-26
I'm having the same problem on a Dell using Gutsy.  Using K9 and it is ripping at 1x.

---

