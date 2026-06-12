---
title: "Xubuntu NetGear"
date: 2007-10-15
forum: General Help
---

### Post by annielouwho on 2007-10-15
Hi!
I am a total Ubuntu Noob.  I installed xubuntu on my daughter's PC.  It is old and was running Win ME.  She only uses it for internet surfing / email.

Everything went ok... but it cannot find her NetGear wireless card.  We have a Netgear wireless router on my PC and the card on her's.  Ok, so I have absolutely NO internet connection on her PC.  I can switch her box out with mine and hook directly to the net if that is going to be the easiest way to go about getting her up and running.

My question for some wise and patient soul...what exactly do I need to do to get her card to work?  I tried to install her card from the CD that came with it, but Xubuntu won't run an .exe?  I guess .exe is a Windows thing that Xubuntu doesn't do?  If anyone can give us some guidance we'd appreciate it.

THANKS!

---

### Post by nonewmsgs on 2007-10-15
welcome.  please open a terminal and type in 

```

lspci

```
the good news for you is i have had good experience with netgear cards.

---

### Post by annielouwho on 2007-10-15
OK, remember - no internet connection!  So I had to copy (with a pen and paper) and I'm retyping here.  Please excuse any typo-s.

00:00.0 Host bridge: Intel Corp 82810 GMCH (rev 03)
00:01.0 VGA compatible controller: Intel Corp 82810 CGH (rev 03)
00:01e.0 PCI Bridge: Intel Corp 82801AA1 (rev 02)
00:00f.0 ISA Bridge: Intel Corp 82801AA (LPC) (rev 02)
00:00f.1 IDE Interface: Intel (rev 02)
00:00f.2 USB Controller: Intel (rev 02)
00:00f.3 SMBUS: Intel (rev 02)
00:00f.5 Multimedia audio AC '97 rev 2
01.08.0 Communication Controller: Conexant Unknown Device 10b4 (rev 89)
01.09.0 Ethernet controller: Marvell Technology Group LTD.  88w8335 [Libertas] 80 2.11b/g wireless (rev 03)

Let me know if I my abbreviations on 00:001e through 00:00f.5 are too vague!  Thanks for your response!  What now?

---

### Post by annielouwho on 2007-10-16
Did I type in the wrong thing?

---

### Post by annielouwho on 2007-10-17
maybe I am invisible and don't realize it?  :)  Come on guys, please,can someone tell me what I need to install to run the wireless card?

---

