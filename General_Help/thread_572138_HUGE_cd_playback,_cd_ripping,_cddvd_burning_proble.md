---
title: "HUGE cd playback, cd ripping, cd/dvd burning problem, please help me!"
date: 2007-10-10
forum: General Help
---

### Post by Axx83 on 2007-10-10
Hello everyone! I have a big issue, I've had it since I installed ubuntu but now I found out it's bigger than it seemed. I can't burn cd/dvds on my comp, cd playback is bad and scratchy and when I rip the music I get the same noises...and I think it's ALL related, let me explain.

My Comp is composed by:
Gigabyte GA-K8N51GMF-9-RH motherboard
[http://www.giga-byte.co.uk/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=2294&ProductName=GA-K8N51GMF-9-RH](http://www.giga-byte.co.uk/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=2294&ProductName=GA-K8N51GMF-9-RH")
Athlon64 processor, 1 gig or ram and an Nvidia 7300gs as video card.
cd/dvd burner is HL-DT-ST DVDRAM GSA-4160B on primary master which means dev/hda

mp3 playback is fine, my audio has no problem, i can even record with my mic (very rare on linux), video playback is perfect with both totem mplayer vlc and whatever.

As I said cd playback sucks, I get a lot of scratches at the start of a song and the same noises if I try to fast forward to a certain spot, of course if I rip the audio cd the mp3 or ogg that come out have the same identical scratches, weird.

Ok so let's check dma and this stuff:
me@mex:~$ sudo hdparm /dev/hda
Password:

/dev/hda:
 IO_support   =  1 (32-bit)
 unmaskirq    =  1 (on)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

it seems I have dma on at boot.

At the same time I can't burn a cd or dvd, or cd-rw or dvd-rw, I can't blank em either. I used gnomebaker, brasero, k3b, same result the operation sometimes starts and then it makes an error and I have to trash another cd, sometimes it doesn't even start. I tried with different supports.

I installed a gutsy 64bit beta the other day and the burning and playback/rip problem is the SAME, identical.

On windows, double boot, cd playback and burning with Nero is flawless, very curious is that with a live of slackware I used sometime ago cd/dvd burning went VERY fine...

Does someone have the same problem, please help me...I LOVE ubuntu and I wanna keep using it.

---

### Post by Axx83 on 2007-10-10
I post another response from hdparm, just in case:

me@mex:~$ sudo hdparm -i /dev/hda

/dev/hda:

 Model=HL-DT-ST DVDRAM GSA-4160B, FwRev=A306, SerialNo=K7H4AB91621
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-2 ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5

 * signifies the current active mode

me@mex:~$ sudo hdparm -I /dev/hda

/dev/hda:

ATAPI CD-ROM, with removable media
        Model Number:       HL-DT-ST DVDRAM GSA-4160B               
        Serial Number:      K7H4AB91621         
        Firmware Revision:  A306    
Standards:
        Likely used CD-ROM ATAPI-1
Configuration:
        DRQ response: 50us.
        Packet size: 12 bytes
Capabilities:
        LBA, IORDY(can be disabled)
        DMA: mdma0 mdma1 mdma2 udma0 udma1 udma2 udma3 *udma4 
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4 
             Cycle time: no flow control=120ns  IORDY flow control=120ns
HW reset results:
        CBLID- below Vih
        Device num = 0

---

