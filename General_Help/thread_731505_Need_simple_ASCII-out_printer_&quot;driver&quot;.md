---
title: "Need simple ASCII-out printer &quot;driver&quot;"
date: 2008-03-21
forum: General Help
---

### Post by antiigrav on 2008-03-21
Hi

I need to use an old dot-matrix printer. No drivers for it. (Panasonic KX-P1180)

But if I just send text (ASCII) (Maybe even PS) to LPT it works fine.

Is there a driver to do this?

Thanks

---

### Post by Distro Jockey on 2008-03-21
There is a Panasonic KX-P1150 option in CUPS.

If you use a web browser and go to:  localhost:631
then Add a printer on LPT #1 and continue on from there, it may do the job.

---

### Post by antiigrav on 2008-03-21
Thanks but that 1150 doesnt work (note printer is 1180) - just garbage characters.

Sometimes if I try a pritner driver, then turn printer off (to stop endless pages of garbage), then turn it on I get a nice continuous printed series of:

"Mar 22 14:40 Computers kernel: [xxx.xxxxxx] hic_scodata_packet: hci0 SCP packet for unknown connection handle xx"

Its amusing the kernal error default works better than any of the printer drivers...

---

### Post by Distro Jockey on 2008-03-21
Ahh, bummer.
Well, there is also the:  textonly.ppd  file in /usr/share/ppd/cups-included
You could try using that in CUPS where it asks for the Make or a PPD file.

---

### Post by antiigrav on 2008-03-22
Thanks but again didn't work. Discovered the 'Generic' category of drivers and tried them.

I like linux, but this is crazy. This was easy 15 years ago. Why do simple things get harder?

I miss good ol' MS DOS and qbasic's one line print command...

Nothing works... except the kernel error prints fine.

I have to reboot every 2nd failed "hello world" print job because the port is busy.

---

