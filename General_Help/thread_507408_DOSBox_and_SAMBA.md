---
title: "DOSBox and SAMBA"
date: 2007-07-22
forum: General Help
---

### Post by prodezigner on 2007-07-22
Is there anyway to get DOSBox to use a SAMBA shared printer (a Brother HL-2070N attached via CAT5 to a HUB to share on an entire network), to print from a DOS based program that only assigns to LPT and SERIAL?

I'm running a little 'travelling vendor' card shop and the software I use is DOS based and I'd like to be able to print reports with it and the only option for printing to USB printers is a Windows only program...

---

### Post by MoLE on 2007-07-23
Wow, that's a complex question!

I'd probably approach it in two stages.

1. Confirm that dosbox is the right environment to run the software, and that it offers LPT emulation - DOSBox is designed for games (which don't usually require printing).  You may have better luck in approaching the problem using say, FreeDOS installed in a vmware virtual machine.

2.  You then have to be able to link the virtual LPT port to the actual printer interface - this will probably require some CUPS wizardry.  Are you sure the printer is accessed by SAMBA in Ubuntu.  I have a 2070n at work, and I access it via IPP protocol (but you need the brother drivers).

Break the problem down into smaller chunks and you may have better luck in the specifics if you ask more specific questions.

---

### Post by prodezigner on 2007-07-23
Hmm, alright... breaking down the question...

First I want to explain my network a bit.

Cable Modem / Voice Terminal to D-Link Wireless G Router. The router goes to one computer in that room itself and two 100' CAT5 cables ran. One to a single computer, the other to a 5-port D-Link hub. The hub is running to two computers and my printer, and is branched off to another 5-port hub which is being ran to two separate ethernet controllers on a Linux shared server on the internal network. The wireless signals is picked up by my laptop and other laptop.

SAMBA picks up my HL-2070N. Prints flawlessly actually, no additional drivers needed other than the Ubuntu HL2060 drivers it comes with.

I've got VirtualBox 1.4 running Windows XP Professional, it picks up the printer just fine also... but the DOS program locks up in WinXP using virtualization. So I resort to another means of running DOS programs.

I've ran DOSbox and it works fine, I just need the ability to print. DOSemu works fine also using FreeDOS... BUT... I don't have a lot of know-how to channel printing and so forth.

Now, I can use my printer via USB... I don't have a problem with it, because my laptop doesn't have a LPT port.

I will ALSO need access to a TXT file from this DOS based program to transfer, if I could have USB functionality inside of the method I use, I can use a thumbdrive for backing up and restoring which... is a plus.

Is that a little more specific or clear as mud?

---

