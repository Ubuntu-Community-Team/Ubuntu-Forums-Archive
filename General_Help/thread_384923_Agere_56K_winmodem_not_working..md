---
title: "Agere 56K winmodem not working."
date: 2007-03-15
forum: General Help
---

### Post by stchman on 2007-03-15
I did an lspci and here is what I got for the modem:

00:0a.0 Communication controller: Agere Systems 56k WinModem (rev 01)

Now is there a fairly simple way to get this modem to work with 6.10?  This modem is pretty old so you figure it would work out of the box.

I have gnome-ppp installed and it says it cannot open modem.  Any help would be appreciated.

Thanks

---

### Post by stchman on 2007-03-15
I figured it out as I needed the restriced module installed 2.6.17-11-386 installed.  Once I installed it the modem was recognized.

---

