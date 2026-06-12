---
title: "WiFi Card in old computer"
date: 2007-02-28
forum: General Help
---

### Post by bastiegast on 2007-02-28
Today, I spent the whole afternoon trying to help a friend getting wireless internet on his xubuntu box. 
The card is a Sweex wireless lan pci thing (LW052)  with an atheros chipset which I had chosen very carefully for him so it would work right out of the box. Unfortunately it didn't.
The card was in no way recognized by the PC. It was **not in the output of lspci** I spitted through the bios for hours but it was there was no mention of the card in either lspci or dmesg output. 
His computer I believe was a pentium of 300 MHz.
The funny thing is: I tried it later at home where it would **work right out of the box**! We both have edgy eft installed. The only reason I can think of was that his system wasn't updated(156 updates would take quite a while on a 300 MHz system).

I chose not to post this in the Wireless/networking support forum as it is not really driver/settings related. The PC just didn't "see" the card, any idea's?

---

### Post by hardyn on 2007-02-28
bad pci slot?

---

### Post by K.Mandla on 2007-02-28
Is the problem similar to this one?

[http://ubuntuforums.org/showthread.php?t=125334](http://ubuntuforums.org/showthread.php?t=125334)

---

### Post by bastiegast on 2007-02-28
> **hardyn said:**
> bad pci slot?

I tried several pci slots. Im sure the PCI slots were good as other cards(sound card for example) worked in them. The card itself also is not the problem since it worked perfectly at home on my one year old computer.

> **K.Mandla said:**
> Is the problem similar to this one?

[http://ubuntuforums.org/showthread.php?t=125334](http://ubuntuforums.org/showthread.php?t=125334)

Quickly looking over that I'd say no, since I have a PCI card, and that thread is about laptops. The card didn't show up in lshw or lspci -v either btw.

---

### Post by K.Mandla on 2007-02-28
My fault; I misread your post. I thought you were troubleshooting a PCMCIA card. :oops:

---

### Post by bastiegast on 2007-03-01
*BUMP* 
Anyone? I'd really like to have some help on this.

---

