---
title: "Sound problem"
date: 2006-10-20
forum: General Help
---

### Post by zoidburg016 on 2006-10-20
for some reason ubuntu wont detect my sound card. It worked in windows. Has anyone else had this problem? If so how can I fix it.

---

### Post by meng on 2006-10-20
Well for a start, could you tell us what sound card you have? If you don't know (one then assumes it is onboard sound), drop to the command line and type
lspci
and post the output here

---

### Post by zoidburg016 on 2006-10-20
It's a old sound blaster sound card, I dont know anything else about it. here's the output
lspci
0000:00:00.0 Host bridge: Intel Corporation 440LX/EX - 82443LX/EX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corporation 440LX/EX - 82443LX/EX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 
02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0f.0 USB Controller: OPTi Inc. 82C861 (rev 10)
0000:00:10.0 Ethernet controller: Intel Corporation 82557/8/9 [Ethernet Pro 100] (rev 05)
0000:01:00.0

---

### Post by meng on 2006-10-20
An old Soundblaster eh? Do you know if it is a PCI card, or is it really old (ISA)? I'll bet that you can get it working, they should be well supported, but I'm not exactly sure how.

---

### Post by kelean on 2006-10-20
I have had that problem with a old sound card.  I had to add the sound card to my /etc/modules file.  First you need to find out what sound card you have   to see if it will work.

---

### Post by zoidburg016 on 2006-10-20
So what do I need to know about it, I don't want to take my computer apart then not figure out what I need to know.

---

### Post by zoidburg016 on 2006-10-20
I checked and it's a sound blaster ct4180 and I think that it's an ISA

---

### Post by meng on 2006-10-20
Try this at the command line:
sudo modprobe sb

(I think your card is also called Vibra16 in some markets. This is a suggestion based on searching Google.)

---

### Post by zoidburg016 on 2006-10-20
> **meng said:**
> Try this at the command line:
sudo modprobe sb

(I think your card is also called Vibra16 in some markets. This is a suggestion based on searching Google.)

That didn't work, I also tries adding sb to /etc/modules and that didn't work.

---

