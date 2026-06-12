---
title: "Ubuntu is unusable!"
date: 2007-07-10
forum: General Help
---

### Post by Nonno Bassotto on 2007-07-10
... of course not.:) I've been a happy Ubuntu user for more than two years. But on my new laptop (HP510) this is almost true.

I experience repeated and frequent (say 5-6 in an hour) freezes. Usually it is a single application which freezes; this can be Firefox as well as Evince as well as Rhythmbox, or Gaim...

When this happens the application is unresponsive for 20 seconds to a couple of minutes; then everything starts working again. When Rhythmbox freezes the audio goes away too. Usually the system remains responsive, although sometimes the freeze started say with Evince, and after some seconds I was not able to move the mouse or anything. In those case I tried to restart X, but nothing happened. Then after a minute the system became responsive again, and X was restarted.

This happens both with battery power and when plugged in, both with Compiz on and off. I tried the low latency kernel, and it is the same story.

I'm really at a loss, since I don't know even what to check. If you have any advice on what to do to obtain at least some useful information, please reply.

---

### Post by topbot on 2007-07-10
hi, I had the same problem with HP 500. Copying and pasting the error log (ata1 something something) to Google revealed that it's a known bug, documented on Launchpad. The problem is the DVD drive, TS-L632D. You need to reflash the firmware to a newer version and the probem wil disappear completely. Feel free to PM me if you need more info.

---

### Post by Nonno Bassotto on 2007-07-10
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/84603) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Thank you for your quick reply. I had a look at Launchpad (see below) and it seems that reflashing the firmware is the solution. For now, though, I'm trying the "don't leave your drive empty" solution.

I'm a bit afraid to upgrade my firmware. I never tried it, and it seems that I need windows to do this, right? Is there any risk to damage the drive?

---

### Post by topbot on 2007-07-11
yes, there is indeed some risk of damaging the drive. however, I reflashed different devices dozens of times and never had any errors. That does not meen it's not going to happen to you, though:-)

Also there is no firmware update made by HP (in my case the latest was HH15, the one that was faulty) and i had to use the generic update C04 and tell Samsung flasher to ignore that the flash model is different. However, it all went smoothly for me.

---

### Post by homogenizer on 2007-08-30
In line with the Toshiba Samsung DVD Drive Problem of the HP 500 notebook with the firmware HH15,  I to had the problems of freezing and the recommended solution is to flash/re-flash the drive.

My immediate solution is to remove the drive.  Using it w/o the drive enables your HP 500 notebook to function smoothly.

I asserted HP Philippines on my problem, well finally they replaced my TSST DVDRW HH15 with a different type of internal drive.  I asserted warranty and asserted to provide me a different drive than the firmware HH15.

They provided me this:

/dev/cdrom:

 Model=Optiarc DVD RW AD-7530A                 , FwRev=EH31    , SerialNo=30644560 1273199Q111
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=yes, tPIO={min:383,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 *mdma2 
 AdvancedPM=no
 Drive conforms to: unknown:  ATA/ATAPI-3 ATA/ATAPI-4 ATA/ATAPI-5 ATA/ATAPI-6 ATA/ATAPI-7

 * signifies the current active mode

Its an Optiarc drive made by SONY NEC.  I waited for 2 months for the solution from HP.

If your HP 500 notebook is still on warranty I suggest you assert to let them replace your drive other than the TSST HH15 firmware.

Im a Proud Ubuntu Fiesty Fawn User.

Kudos to HP!

---

