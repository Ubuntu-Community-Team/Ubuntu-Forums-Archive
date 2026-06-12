---
title: "[SOLVED] Serial Modem volume problem."
date: 2008-01-20
forum: General Help
---

### Post by capt.d on 2008-01-20
I have a Hayes  Accura serial modem that works fine with 7.10. The problem is i need to turn off the extremely  loud speaker. I have tried changing ATDT to ATMODT. Hayes said ATLOMO in an extra string? The first line is ATZ, the second  line is OK-AT-OK "ATDT7484265" I'm not sure where  to  put the ATLMO?
I tried after the phone  number and used quote marks (#) and that did not work. I'm a newbe at linux and may be over looking something. Is there an old file that need to be deleted? I do a reboot and check in the terminal to  see if the change was saved and it was but the modem speaker volume is the same.
Thanks, capt.d:confused:

---

### Post by editrix on 2008-01-20
> **capt.d said:**
> I have tried changing ATDT to ATMODT. Hayes said ATLOMO in an extra string? The first line is ATZ, the second  line is OK-AT-OK "ATDT7484265" I'm not sure where  to  put the ATLMO?

Wow! This sounds complicated. I went to Google Linux and searched "serial modem volume" and found a ton of stuff, but the general consensus seems to be to use a dial program and adjust the volume there.

So, first off, which program are you using? I use KPPP, but I can't check how to configure it for you as long as I'm online :-(

---

### Post by sleepingdragon on 2008-01-20
I had exactly the same problem with a Hayes Accura 56k modem. The only thing I found to get rid of the sound was to use kppp as a dialler. I don't know what it does to kill the sound (I tried all the manual settings to no avail), but it worked well for me and kept stable.

---

### Post by capt.d on 2008-01-20
I  was going to use KPPP but this install is on my old reliable Dell CPX P3 laptop and it is not supported for i-386? :confused:
capt.d

---

### Post by sleepingdragon on 2008-01-22
damn, that's annoying! Try this post - [[COLOR="Red"]click here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=596200&highlight=kppp+i386")

---

### Post by capt.d on 2008-01-23
Thanks Sleeping Dragon, i was able to download and install kppp. I spent all day with it but could not connect. It was probably due to not providing all the information it required. I really like the simple set up of the basic application originally installed by default. I thought i had found the problem when i discovered the MO (sound off) was really M0! (zero) I'll keep trying.
capt.d

---

### Post by sleepingdragon on 2008-01-24
I'm just trying to think of all the little problems I had... 

I seem to remember that the modem's location was */dev/ttyS0*, instead of the /dev/modem that was listed in kppp. 

Ticking the box for "Use Lock File" also helped.

I've also included all the modem settings in the screenshot, see if something is missing there.

---

### Post by capt.d on 2008-01-25
Fixed! Sleeping Dragon, i copied your file and filled in the modem commands. I also had to change to pap/chap and go into the network manual config window and turn off. It seems perfect and no loud modem sounds, i may even try the low setting. Thanks for not giving up.
capt.d

:guitar:

---

### Post by sleepingdragon on 2008-01-28
Nice one! :)

---

