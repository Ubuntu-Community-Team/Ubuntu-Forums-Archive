---
title: "Need To Re-Install Firmware - 12.04 (Precise) LTS"
date: 2014-03-31
forum: General Help
---

### Post by Adler on 2014-03-31
Hi All,

I was doing a little Linux-Kernel cleaning, and deleted my Firmware. I am now without my mouse, and WiFi on my main system. It seems I was confusing 3.11, and the kernel that I get with the Terminal *uname -r* command. That Kernel is 3.13. 3.14 is coming soon. I continually up-date my Kernel to the latest. I just got carried away when I did *sudo apt-get* *update, sudo apt-get dist-upgrade*. I then saw 3.11 was to up-date, but deleted that in Synaptic. Then did the Terminal thing again, re-booted, and found my error. Oops!

Presently, I am running the Live CD of 12.04 (Precise) LTS, and have access to my HDD. Everything is good with the Live CD - Mouse, and WiFi function. I need to access Synaptic - on my main system - to install the missing Firmware. Or, some varient to get back to normal.

Thanks in advance for any assistance.

Adler
Wildwood, New Jersey

---

### Post by Impavidus on 2014-03-31
[chroot](https://help.ubuntu.com/community/LiveCdRecovery) (scroll to Update Failure). Use the command line to reinstall what you deleted.

---

### Post by Adler on 2014-03-31
Impavidus,

Thanks for the reply. But, I am not sure what you mean here? I can get to my 128Gb SSD, and am looking to launch Synaptic. I am thinking this is simpler than I assume.

Can you expand what you mean? TIA.

Adler
Wildwood, New Jersey

---

### Post by Mark Phelps on 2014-03-31
Your post is confusing.  For the most part, Firmware is contained WITHIN a device, typically, a chip or chipset. The BIOS, since it's programmable, could be considered a form of firmware.  Other examples are device drivers, typically those by  disk controllers.  But these are not to be confused with drivers that you install with an OS -- those are software that run in kernel space.

While you could REMOVE firmware from a device, you would need a device that flashes the ROM on the device -- although, you could flash the wrong firmware and trash it. So, when you say you removed firmware, that's confusing.

---

### Post by Adler on 2014-03-31
> Your post is confusing.

Mark Phelps,

*ROFLOL.* I am that confused how I could have lost Wifi, and my Mouse Pointer. Sorry, if my post was confusing, and - as you rightfully state - I probably have not accessed *Firmware*. In Synaptic I deleted references to 3.11. 

I tried to cd / to my 128Gb SSD, did an update / dist-upgrade, but that didn't stick to my SSD. Again, I am running the Live CD. I guess I am going to have to better post the question. Or, what I had done, but it was delete references to 3.11 in Synaptic, then - in Terminal - update / dist-upgrade. Strange.

Thanks for your post.

Adler
Wildwood, New Jersey

---

### Post by Adler on 2014-03-31
Gentlemen,

I have worked my way through this, and am back to normal. Unfortunately, I can't really remember the exact path that I took. It was just a matter of trying numerous things between the Live CD, and in Terminal. It would appear I deleted the Wifi, and Mouse Drivers.

Thank you for jumping in here.

*ADMIN: If you would like to delete this post please do so.*

Adler
Wildwood, New Jersey

---

