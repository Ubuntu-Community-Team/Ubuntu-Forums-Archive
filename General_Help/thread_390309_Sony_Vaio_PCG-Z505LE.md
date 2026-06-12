---
title: "Sony Vaio PCG-Z505LE"
date: 2007-03-21
forum: General Help
---

### Post by Horgrathi on 2007-03-21
I just got handed down a old laptop, a **Sony Vaio PCG-Z505LE**.

I am trying to install Ubuntu via the **External (PCGA-CD51**, yet it seems to not recognize the cdrom. It asking me currently to select what drive I use for the cdrom drive. Which one should i pick?

none, aztcd, cdrom, cdu31a, cm206, gscd, isp16, mcdx, optcd, sbpcd, sjcd, sonycd535
[ Tried sonycd535, it asks for the path then and none work]

---

### Post by neufeldm on 2007-07-16
Hello-
Not sure if you figured this out or gave up entirely, but I've wrestled with similar problems on a Vaio PCG-SR7K booting from a Sony PCMCIA CD drive. I've had some luck getting things to work with xubuntu and the alternate CD installing in text mode. The trick I found was to boot up off the CD and start a text mode install. After getting to the start of the install procedure, i.e. after the system has finished booting into the text installer and finished reading from the CD drive, eject and then reinsert the pcmcia card for the CD. For the SR7K I've got this is enough to kick the regular Linux pcmcia driver into action -- it finds the drive and I can do a text mode install from the CD.  I'm guessing that the BIOS usage of the CD for booting somehow interferes with the pcmcia driver recognizing and taking control of the drive. Hope this helps.

-Mike

---

### Post by anthonyJC on 2008-07-02
Used PCGA-CD51. Last post is correct. BIOS remaps the CARDBUS cd-rom to appear as IDE at /dev/hde instead of /dev/hdc. Bios cannot boot USB devices of type CD or FLASH. The eject and re-insert rids of the BIOS re-mapping. I solved by using distro's that actively search alternative CDROMS (like xubuntu hardy heron, grml.org (feb two thousand and eight )) and purchasing USB-CDROM. Use CARDBUS to boot then when it goes searching swap cd out to your USB CDROM. the ide2=0x180,0x386 used to work on 2.4 kernels but not any more on 2.6. Alternatives to purchasing USB-CDROM is DSL (damn small linux) that still uses 2.4 kernel. Suse 11 doesn't actively search other cdroms.

---

### Post by Tobyb on 2008-07-18
If you can get XP installed, I found that UNetbootin allowed me to easily install PCLixuxOS MiniMe, which I otherwise could not install. It's supposed to work from within Linux as well.

Don't have to do the net boot part, but can simply place the install ISO on your desktop and point UNetbootin at the ISO, and let it do it's magic from there. What a discovery this was!!!!!!!!!! (And it will either wipe out your XP or allow you to do a dual-boot.)

---

