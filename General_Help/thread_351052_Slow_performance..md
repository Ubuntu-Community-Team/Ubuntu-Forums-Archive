---
title: "Slow performance."
date: 2007-02-01
forum: General Help
---

### Post by kenerly on 2007-02-01
I just installed 6.10 dual boot with xp pro. It is slower than my xp pro. What can I do to fix this.

---

### Post by drfalkor on 2007-02-01
Have you had this problem before ? you mean that gnome feels like sirup ?

---

### Post by kenerly on 2007-02-01
> **drfalkor said:**
> you mean that gnome feels like sirup ?

Correct


> **drfalkor said:**
> Have you had this problem before ? 

Installed Linux yesterday. Works fine, no errors just slow. Xp is twice as fast and I'm trying to get away from windows.

---

### Post by conradcliff on 2007-02-03
I recently installed ubuntu on an old p3 550 with 256. It had a crapped up install of 98 on it and I had hoped ubuntu would give it some new life but no go. I switched over to XFCE but still no dice. It's slow as molasses, any ideas?

---

### Post by allwin on 2007-02-03
> **conradcliff said:**
> I recently installed ubuntu on an old p3 550 with 256. It had a crapped up install of 98 on it and I had hoped ubuntu would give it some new life but no go. I switched over to XFCE but still no dice. It's slow as molasses, any ideas?

Did you do "sudo hdparm -iI /dev/hda" to see if you have DMA turned on, also 32 bit access and a decent UDMA mode?

I have an old dell p3 550 w/256 and it runs really well.  Another cheap upgrade was, I bought a new video card for it (finding AGP 1x cards is tough, but they are cheap and usually have twice the memory of what's in the old box).  Check Ebay.  That made a bigger difference.  I was even able to run Beryl and scroll Firefox fine after setting color depth to 16.

I think I also set "swappiness" to zero and fiddled with the EXT3 file system options:

[http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed](http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed)

Oh yeah, I profiled the boot sequence.  I don't have a link for that, I imagine a google would turn up something there.

It all added up.  The two biggest were fiddling with HDPARM to set the drives up to max capabilities, followed by the new video card, followed by all the rest.

---

### Post by conradcliff on 2007-02-03
This is what I get...

tower@Employee-Computer:~$ sudo hdparm -iI /dev/hda
Password:

/dev/hda:

 Model=Maxtor 91020U3, FwRev=MA5409S0, SerialNo=C306JJAC
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=57
 BuffType=DualPortCache, BuffSize=2048kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=19941264
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-4 T13 1153D revision 17:  ATA/ATAPI-1 ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5

 * signifies the current active mode


ATA device, with non-removable media
        Model Number:       Maxtor 91020U3                          
        Serial Number:      C306JJAC            
        Firmware Revision:  MA5409S0
Standards:
        Used: ATA/ATAPI-4 T13 1153D revision 17 
        Supported: 5 4 3 & some of 5
Configuration:
        Logical         max     current
        cylinders       16383   16383
        heads           16      16
        sectors/track   63      63
        --
        CHS current addressable sectors:   16514064
        LBA    user addressable sectors:   19941264
        device size with M = 1024*1024:        9736 MBytes
        device size with M = 1000*1000:       10209 MBytes (10 GB)
Capabilities:
        LBA, IORDY(can be disabled)
        bytes avail on r/w long: 57
        Standby timer values: spec'd by Standard, no device specific minimum
        R/W multiple sector transfer: Max = 16  Current = 0
        Advanced power management level: unknown setting (0x0000)
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 *udma4 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=120ns  IORDY flow control=120ns
Commands/features:
        Enabled Supported:
           *    SMART feature set
           *    Power Management feature set
           *    Write cache
           *    Look-ahead
           *    Host Protected Area feature set
           *    WRITE_VERIFY command
           *    WRITE_BUFFER command
           *    READ_BUFFER command
           *    NOP cmd
           *    DOWNLOAD_MICROCODE
                Advanced Power Management feature set
HW reset results:
        CBLID- above Vih
        Device num = 0 determined by the jumper
Checksum: correct
tower@Employee-Computer:~$ 

I'm guessing that DMA is enabled, what does it look like to you?

Also, I have a nvidia geforce4 mx440 pci card in there now but I'm having trouble getting it to work. I have that issue in another thread.

 You have 3D desktop enabled? My amd 64 @2.45 ghz and 512 with a ati9200 has trouble with that. It might just be bugs in pclinuxos though.

---

### Post by allwin on 2007-02-03
> **conradcliff said:**
> This is what I get...

I'm guessing that DMA is enabled, what does it look like to you?

Also, I have a nvidia geforce4 mx440 pci card in there now but I'm having trouble getting it to work. I have that issue in another thread.

 You have 3D desktop enabled? My amd 64 @2.45 ghz and 512 with a ati9200 has trouble with that. It might just be bugs in pclinuxos though.

Tell you what, on the issue of tuning your disk drive, I'll let another "expert" speak:

[http://opensource.apress.com/article/65/command-line-gems-hdparm](http://opensource.apress.com/article/65/command-line-gems-hdparm)

Watch out for the -c3 setting...it killed my system on the spot when I tried that.  YMMV.

For the nvidia card, look up ENVY in google or on this forum.  Can't say for sure your video card is supported.  But if it is, use the 9631 or higher nvidia driver and built in AIGLX support.  IF the card is supported.

I changed my card to an ATI card I found on Ebay because the thing was only supported by the legacy nvidia driver which doesn't work.  Cost me like $23 including shipping from someplace on Ebay.  Good luck with the nvidia card.

I've had my share of troubles with UBUNTU, but Beryl has always been pretty fast for me...when it chooses not to crash, that is.

---

### Post by conradcliff on 2007-02-03
Thanks for the help, I'll look into it.

---

### Post by russo.mic on 2007-02-04
Here is a wild idea, 

Why don't you post some information on the hardware your using?

---

### Post by conradcliff on 2007-02-04
Well I said I was using a p3 550 with 256 and an integrated vid card, I also posted the info about my hd... not sure I appreciate the tone of your comment but if you would like more just point me in the direction to acquire a hardware list from some magic terminal code.

---

### Post by Talon2 on 2007-02-05
> **allwin said:**
> 
I have an old dell p3 550 w/256 and it runs really well.  Another cheap upgrade was, I bought a new video card for it (finding AGP 1x cards is tough, but they are cheap and usually have twice the memory of what's in the old box).

It all added up.  The two biggest were fiddling with HDPARM to set the drives up to max capabilities, followed by the new video card, followed by all the rest.

What AGP 1x video card did you use?

Thanks.

---

### Post by allwin on 2007-02-05
This is the video card that worked for me:

BEST DATA DIAMOND STEALTH AGP 32DDR ( S60AGP )

It's an ATI.  I don't use it for gaming.  I bought it expressly because I wanted to get Beryl running.  It works OK despite the bad rep of ATI cards, with the open "ATI" driver and the appropriate mojo in the xorg.conf file to turn on DRI and composite.  The only thing I had to do was cut down to depth 16, else scrolling in Firefox was excruciatingly slow.

One other fix...GNOME has a setting "reduced resources".  I turned that on also.  You need to launch gconf-editor and find the option and set it.  I don't remember specifically where it was.  Also, the focus plugin had to be turned off as it was making things slow, but not intolerably so.  I decided I didn't need it.

---

### Post by Topsiho on 2007-02-05
> **conradcliff said:**
> .. not sure I appreciate the tone of your comment but if you would like more just point me in the direction to acquire a hardware list from some magic terminal code.

Ha, he did not mean any wrong, it's a good idea to mention your hardware, which indeed you did, that's true.

:)


Topsiho

---

