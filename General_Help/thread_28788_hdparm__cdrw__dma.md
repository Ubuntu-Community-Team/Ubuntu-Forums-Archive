---
title: "hdparm / cdrw / dma"
date: 2005-04-21
forum: General Help
---

### Post by Bloke on 2005-04-21
Before I get carried away and make unnecessary changes, please have a look at my hdparm output and give suggestions. What I want to do is enable DMA for my cdrw drive. 

---------------------------------------------------------------
username@hostname:~$ sudo hdparm -I /dev/hdc
Password:
/dev/hdc:
ATAPI CD-ROM, with removable media
        Model Number:       Memorex 52MAXX 3252AJ
        Serial Number:
        Firmware Revision:  QWS6
Standards:
        Used: ATAPI for CD-ROMs, SFF-8020i, r2.5
        Supported: CD-ROM ATAPI-2
Configuration:
        DRQ response: 50us.
        Packet size: 12 bytes
Capabilities:
        LBA, IORDY(cannot be disabled)
        DMA: mdma0 mdma1 mdma2 udma0 udma1 *udma2
             Cycle time: min=120ns recommended=120ns
        PIO: pio0 pio1 pio2 pio3 pio4
             Cycle time: no flow control=227ns  IORDY flow control=120ns

username@hostname:~$ sudo hdparm -v /dev/hdc
Password:
/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
---------------------------------------------------------------

It apears to me that "*udma2" is enabled, but "using_dma" is disabled...? I probably have it all wrong.

Thanks

---

### Post by woifi on 2005-04-21
check out the /etc/hdparm.conf - you can easily change the parameters there

---

### Post by Bloke on 2005-04-21
[QUOTE=woifi]check out the /etc/hdparm.conf - you can easily change the parameters there[/QUOTE]
Hmm ... yes I see parameters can 'easily' be changed, but to what and which ones?

Does it matter that my HD is attached to an ATA133 contorler card?

An example of what to change would be helpfull.


Thanks

---

### Post by Bob D. on 2005-04-21
Add the following lines underneath all the text with the hash marks (##):

```
command_line {[indent]hdparm -d1 /dev/hdc
[/indent]}
``` 
Make sure to leave a blank space at the bottom of the page (I was always told to do this and it works, so...)

Save the hdparm.conf file and reboot. Check the DMA setting, it should now be active for HDC.

Bob

---

### Post by merlyn on 2005-04-21
Silly question, but is there a gui front end to hdparm.

---

### Post by clb137 on 2005-04-22
[QUOTE=merlyn]Silly question, but is there a gui front end to hdparm.[/QUOTE]

Not really just type 'sudo gedit' then open etc/hdparm.conf   put something like this
at the bottom of the file then save, restart and all will be fine

/dev/hdc {
	dma = on		   
	interrupt_unmask = on
	io32_support = 0
}

good luck  

clinton bennett

---

### Post by Bloke on 2005-04-22
[QUOTE=Bob D.]Add the following lines underneath all the text with the hash marks (##):

```
command_line {[indent]hdparm -d1 /dev/hdc
[/indent]}
``` 
Make sure to leave a blank space at the bottom of the page (I was always told to do this and it works, so...)

Save the hdparm.conf file and reboot. Check the DMA setting, it should now be active for HDC.

Bob[/QUOTE]
Excellent.

I also found that "-c3" is usefull to enable 32-bit "I/O support". So the command is:

"hdparm -c3 -d1 /dev/hdc"

Note: "-d1" = enable "using_dma" option.


Thanks for everyones help!

---

