---
title: "How do I disable SCSI emulation?!"
date: 2007-11-18
forum: General Help
---

### Post by poo706 on 2007-11-18
Linux newbie here...  I started with Ubuntu 7.04 and upgraded to 7.10.  I'm trying to use cdrdao (via Arson) to burn an audio CD, but I get a cue sheet variant error every time.  Likewise, ripping and burning DVD's does work, but is much slower than it should be.  I'm using kernel 2.6, but for some reason my DVD RW drive is using SCSI emulation.  It's an IDE drive on secondary slave (hdd), but it's showing up as scd0 in k9copy and k3b.  I've spend a LOT of time looking around for a solution, and it seems to be to use ide-cd instead of ide-scsi and make sure DMA is enabled.  Problem is, I can't figure out what it telling my drive to use scsi emulation.  I have no lilo.conf, and nothing stands out in menu.lst or fstab.  Once Ubuntu boots, I figured out how to load ide-cd using "modprobe ide-cd" and I confirmed it's loaded with "lsmod", but from that point, I don't know to switch the drive from scsi to ide.  Could someone please help me, this is driving me absolutely crazy!

[poo706]

---

### Post by atlfalcons866 on 2007-11-18
i dont think you can without recompiling a kernel.

---

### Post by poo706 on 2007-11-18
Apparently it's possible through either recompiling or with modules.  Obviously, as a newbie, I was trying to avoid recompiling, but if it's a straight forward process and it's my only choice, then so be it.  Can anyone else shed any light on this, and/or point me towards a good recompiling tutorial?

[poo706]

---

### Post by geirha on 2007-11-18
Perhaps adding ide-scsi to the blacklist and reboot would do the trick. ```
echo "blacklist ide-scsi" | sudo tee -a /etc/modprobe.d/blacklist
```

---

### Post by poo706 on 2007-11-19
Interesting idea, I'll try that.  I'm surprised that this issue seems to be pretty rare.  I'm really wondering if I did something to cause this during installation?  Ubuntu 7.04 had the 2.6 kernel, correct?  So there is no reason that by the time 2.6 was around that it should default to ide-scsi when detecting ide drives.

[poo706]

---

### Post by poo706 on 2007-11-19
Blacklisting ide-scsi didn't do anything.  I did discover that when I use "lsmod", it states that the "cdrom" module is using the "sr_mod" module.  So I did a "modprobe -r sr_mod" and "modprobe ide-cd", which changed the cdrom module to use the ide-cd module.  Seems like a step in the right direction, but now I can't get k3b or k9copy to recognize any cd-rom.  Do I need to re-mount somehow?

[poo706]

---

### Post by ezsit on 2007-11-19
> I'm using kernel 2.6, but for some reason my DVD RW drive is using SCSI emulation. It's an IDE drive on secondary slave (hdd), but it's showing up as scd0 in k9copy and k3b.

Linux has relied on SCSI emulation to run IDE cdrom drives since kernel 2.6 since IDE cdrom drives use SCSI protocols transmitted over the IDE bus to work properly. The whole business of EIDE cdrom drives were made possible by the use of SCSI commands sent over the IDE bus, that is what made Enhanced-IDE enhanced. SCSI emulation is necessary because the devices are using SCSI protocols to communicate with the system and Linux needs to treat the device as a SCSI device (that is what EIDE cdrom drives are, SCSI devices connected over IDE ports).

You want SCSI emulation, without it, your drive reverts to a very limited function device operated by obsoleted and unmaintained software.

Also, kernels newer than 2.6.20 treat **ALL** block devices as SCSI devices. All hard drives, flash drives, SATA, PATA, and SCSI are all handled by the SCSI drivers in the kernel. This is done for consistency.

the IDE-CD driver has not been needed since kernel 2.6 was released almost four years ago. I'm surprised it would still work on a modern kernel.

---

### Post by poo706 on 2007-11-19
Ok, I don't know why this worked, but it worked so I'm just going to go with it.  I really liked Arson because I could specify LAME as the MP3 decoder and cdrdao as the burning program.  All my MP3's have been encoded with LAME and I absolutely hate a gap between tracks that should not be there. I was ready to give up on Arson and cdrdao and try K3B and cdrecord.  In that process, I discovered that if I simply open K3B, then close it, Arson and cdrdao will work flawlessly.  I haven't tried any DVD ripping/buring/playing yet, but at least I can burn audio CD's now.  Any idea what the heck is going on here?

[poo706]

---

### Post by mrshirls on 2008-01-13
Hi All,

I am having a similar trouble where my pata hard drive shows up as /dev/sda.  (while installing mythbuntu)  Any thoughts?  I would not care, but it seems that I can not write to the drive.  I have the same results on two different machines with rather old hardware P4 700Mhz and Celeron 400Mhz

Thanks.

---

### Post by geirha on 2008-01-13
If possible, could you paste the error you get when you try to write to it, and also which command/program?

And what does ```
sudo fdisk -l
``` output?

---

