---
title: "USB Problems"
date: 2006-11-05
forum: General Help
---

### Post by squid890 on 2006-11-05
I recently installed a clean edgy system on a new hd (after using edgy testing/dapper for a while), and after doing all the updates, everything was fine, even after reboot. But last evening, before going to bed, I was playing around with my new system and I tried to use the hibernate/suspend, and that was fine as well. Before going to bed, I hibernated the system. Since then, though, all my usb is not working and I'm getting an error -110 in dmesg. 
Specifically, it says:

usb 1-1: device descriptor read/64, error -110

and the 1-1 changes depending on which port is being used. I've tried different devices, ports, even a seperate hub plugged directly into the motherboard, and each brings up the same error. The system boots fine, and everything else works, except any usb devices. These are vital because I use a USB sound card and printer. 

I've also tried booting an older edgy system, without all the latest updates (on my older hd) and a different kernel, each producing the same results. Oh, and I've tried the liveCD directly, which came up the same. None of this was happening before last evening though. I think it may have something to do with the suspend/hibernate. I've also reset the BIOS back to defaults, just to make sure that's not the problem

Any help?

Thanks,
Conor

---

### Post by squid890 on 2006-11-05
Sorry to reply to myself, but since posting I've tried a memory test as well, and it has come up with nothing. I thought there might be a problem in the RAM since the problems began occuring after a suspend and hibernate.

Edit:

After considering the idea of it being a problem with the RAM, I took out the RAM card that I had, booted up the computer, and obviously it didn't boot because it was missing RAM, but then I shut it down, put the card back in, and it booted correctly, and FINALLY the USB is working again! Hope this helps anyone else who experiences this problem.

---

### Post by tadtoll on 2006-11-09
I am having problems on edgy with my USB as well. At first it came and went from one boot to another, and now it does not come up at all. I am going to try booting with a live Dapper CD to see what happens. I also have problems with suspend and hibernate not working on Edgy (suspend was working fine on Dapper). If I don't see the USB using the live Dapper CD, I'll give the RAM pull a try. Thanks for reposting with the update.

---

### Post by karthikp on 2006-11-28
I believe I'm having the same problem. You don't need to remove the RAM. It looks like all USB devices just stop working when the comp wakes up.

For the record, my comp's a Dell Inspiron 9300 running Kubuntu Edgy.

I can still use the onboard keyboard and touchpad when the comp resumes. To get the USB ports to work, I have to reboot. lsusb gives no output and more or less hangs the terminal. The virtual terminals don't respond (blank screens).

Suspend used to work flawlessly on Dapper. BTW, Just how to I enable USB devices from the command line?:confused:

---

