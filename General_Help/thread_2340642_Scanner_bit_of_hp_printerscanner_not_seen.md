---
title: "Scanner bit of hp printer/scanner not seen"
date: 2016-10-20
forum: General Help
---

### Post by glendavee on 2016-10-20
I had a hp Photosmart6520 working fine until I disconnected it a few months ago. I have now reconnected and printer works fine but system can't see scanner. In interim I switched internet provider to BT and I now have a BT homehub. I am using 16.04. I'm thinking that BT has done something but I don't know what. If I try xsane just hangs up. I've reinstalled printer several times. Help please

---

### Post by ajgreeny on 2016-10-20
It may be a simple thing like a change of the IP of the printer as you are now using a different router.

I have the same printer/scanner working fine here in both 14.04 and 16.04.  My printer uses a reserved IP address setup in the router so it is always at the same 192.168.1.35 IP address and that makes it much easier to find and to use on the network.

Try reserving an address in the BT Hub if that's possible, then delete the printer from Printing in your system setup, and finally reinstall it.  You may have to enter the new IP you have just reserved in the printer setup dialogue (I had to do so), and once found it should work fine for you.

---

### Post by glendavee on 2016-10-21
Tried that. Printer installs, but still won't scan. I've set the hub to a fixed IP and, yes, printer is found. Problem is, computer seems to think its only a printer, not a printer/scanner

---

