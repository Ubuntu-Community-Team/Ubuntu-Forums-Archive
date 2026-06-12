---
title: "[SOLVED] Virtual Windows XP - Will directX and webcams work from the existing partiti"
date: 2007-10-20
forum: General Help
---

### Post by the8thstar on 2007-10-20
Virtual Windows XP - Will directX and webcams work from the existing partition?

In my existing windows partition, everything works fine... like it should. Now, I've read several threads about the possibility of virtualizing this existing partition under Ubuntu with VMWare or VirtualBox.

My questions are: will games work? will I have sound? will the internet work? will my webcam work?

---

### Post by ash1574 on 2007-10-21
Put your fears to rest.  You can do all the following.  It may take a small tinkering to make the webcam work (v-box window, click usb, click whatever comes up to allow usb use) but... i don't see why anything else would fail.

---

### Post by ruibernardo on 2007-10-21
vmware-server only works with USB 1.1, so webcams usually don't work. Virtualbox can use USB 2.0, but I've never tested if a webcam (real time transfers) work on the guest OS. Try it :)

---

### Post by DagMan on 2007-10-21
Mine does not work in virtualbox, it crashes the virtual machine with an exceeded bandwith message from virtualbox afterwards.  Oddly enough though, even though the Linux support for my webcam is still very new and unrefined, making it incompatable with messengers, MSN in wine finds the Linux driver and it looks brilliant in comparison to the native apps running it via the same Linux driver.  Unfortunatly MSN in wine wasn't able to log into MSN.

But not in my case, it didn't work in Virtualbox nor did a DVB card that doesn't yet have a linux driver.

---

### Post by the8thstar on 2007-10-21
Thanks guys for the speedy responses. So, if I understand correctly, it MAY work or it MAY NOT... I wonder why.

I guess I'll try to use VirtualBox because of my webcam (Microsoft VX-6000)... I wonder if there's a how-to somewhere for VirtualBox + existing partition.

---

### Post by UK-Wobbie on 2007-10-21
> **the8thstar said:**
> Virtual Windows XP - Will directX and webcams work from the existing partition?

In my existing windows partition, everything works fine... like it should. Now, I've read several threads about the possibility of virtualizing this existing partition under Ubuntu with VMWare or VirtualBox.

My questions are: will games work? will I have sound? will the internet work? will my webcam work?

will games work? will I have sound? will the internet work? will my webcam work? 

Thats a big yes lol In vbox! :)

---

### Post by the8thstar on 2007-11-25
> Thats a big yes lol In vbox!  

Unfortunately, that proved to be not true. :(

---

