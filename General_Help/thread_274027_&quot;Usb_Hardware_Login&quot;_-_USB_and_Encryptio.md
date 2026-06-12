---
title: "&quot;Usb Hardware Login&quot; - USB and Encryption"
date: 2006-10-09
forum: General Help
---

### Post by disabled_20220313 on 2006-10-09
Afternoon,

I was thinking of securing my ubuntu box a bit more than the normal Username and password.

I was hopeing to set up a login where you are requested for a username and password, but the system also searches for a specific GPG/PGP key on a pendrive. 

Without the key on the pen drive login would fail. 

I understand that this is just a bit of paranoia, but I also want to see if I can manage it.

Googling so far has yielded no results for me, maybe I'm searching for the wrong keywords. Any suggestions would be appreciated.

Thanks all!

PS. I understand that loosing the USB drive is likely, so I will have a robust back-up procedure in place.

---

### Post by TuxCrafter on 2006-11-16
Do you had success, I want to build a very secure Linux system group.

I already have smartcards and a PGP key system etcetera.

I use VIA Epia's with hardware encryption units, but doesn't have that working yet. 

I want to login via smartcard (similar to usb) and encrypt everything on the pc the hardware level.

[http://www.via.com.tw/en/initiatives/padlock/hardware.jsp](http://www.via.com.tw/en/initiatives/padlock/hardware.jsp)

---

### Post by DanielH on 2007-02-19
Just stumbled across your post, I don't know if you already solved your problem.

If not, have a look at the pam_usb project ([www.pamusb.org]("http://www.pamusb.org")) , it does exactly what you want.

It's a bit old, but when I played around with it, it worked without problems.

---

### Post by TuxCrafter on 2007-02-19
[https://www.fsfe.org/en/fellows/ph3/krypto_blog/login_via_openpgp_smartcard](https://www.fsfe.org/en/fellows/ph3/krypto_blog/login_via_openpgp_smartcard)

I also found this but can't read it it is not in english

---

