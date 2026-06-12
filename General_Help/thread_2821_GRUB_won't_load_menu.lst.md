---
title: "GRUB won't load menu.lst"
date: 2004-10-31
forum: General Help
---

### Post by iminj on 2004-10-31
Most likely a NOOB error ... but my grub menu is gone, and I get a 'grub>' prompt when I boot my system.

I installed grub.conf several days ago, and set it up to edit the menu so that Windows 98 is the default OS to load at the boot. Worked fine, until now. Now, I can't boot into ubuntu or windows.

Here are the details. I have grub/MBR, and Win98 on my primary hard drive, and ubuntu on the secondary drive. I don't know the specific partition numbers, although I simply accepted defaults when I installed ubuntu for a dual-boot / 2 drive system. 

I don't understand the BASH language, and am clueless how to construct the commands to boot the system. Anyone able to help ... OR ... is there a 'rescue' capability built into the ubuntu CD that can help me re-install grub alone without touching the kernel and other files?

thnx, iminj

---

### Post by bvc on 2004-11-01
when you get the 'grub>' (which is the grub shell btw) type;
find menu.lst

what does it say?

I don't know about a rescue, haven't needed one.

---

### Post by iminj on 2004-11-01
grub> find menu.lst .. returns the following:

"Error 15: File not found"

iminj

---

### Post by bvc on 2004-11-01
not good
I'd reinstall the distro unless you have a livecd distro handy to edit files with.

---

### Post by iminj on 2004-11-01
Thanks bvc:

I came to the same conclusion, and reinstalled the distro earlier. I wish I knew what I did to foul up GRUB.

iminj

---

