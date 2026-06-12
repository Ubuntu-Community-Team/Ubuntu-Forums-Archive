---
title: "Booting into safe graphics mode"
date: 2007-09-21
forum: General Help
---

### Post by bjb.butler on 2007-09-21
I know that when you boot the live cd, you can choose safe mode. But how do you do that once you have installed feisty? When you press esc, it only brings up the option to boot into recovery mode. 

thanks,bj

---

### Post by PmDematagoda on 2007-09-21
You don't get that in Feisty as it doesn't have the bullet-proof X that allows "Safe-mode", but Gutsy has X-server 1.4 with the Bullet-proof X so that should help you. Anyway what's the problem?

---

### Post by gubemton on 2007-10-28
> **PmDematagoda said:**
> You don't get that in Feisty as it doesn't have the bullet-proof X that allows "Safe-mode", but Gutsy has X-server 1.4 with the Bullet-proof X so that should help you.

So, having booted into "safe graphics mode" from the CD and installed ubuntu, how does one initiate this "X-server 1.4 with the Bullet-proof X"?

Or, to revert to the original question, how does one set ubuntu to boot into "safe graphics mode" *after* installation?

(I installed 1.10 after booting from the CD in "safe graphics mode", but the installation now boots in the way that prompted me to select "safe graphics mode" in the first place--i.e.with a screwed video display).

---

### Post by PmDematagoda on 2007-10-28
Could you post the specifications of your PC?

---

### Post by gubemton on 2007-10-28
> **PmDematagoda said:**
> Could you post the specifications of your PC?
Dell Optiplex GXa 
Intel P2-233 CPU
192MB RAM
S3 Savage4 video card
AcerView 34eL monitor
4Gb bootdrive
6Gb second drive

Booting from the CD under "safe graphics mode", System/Admin/Screens & Graphics shows the video driver as "generic Vesa". 
(A second video card is shown (on-board video?) "ati mach 64 utah")

What I want to be able to do is run reconfigure xserver-xorg and set it to use the vesa driver. I've tried this a few times, but so far without success.

---

### Post by PmDematagoda on 2007-10-28
I'm sorry, I don't have much experience concerning S3 cards, perhaps someone who is will come along and help you out.

---

### Post by gubemton on 2007-10-28
> **PmDematagoda said:**
> I'm sorry, I don't have much experience concerning S3 cards, perhaps someone who is will come along and help you out.
OK, thanks :-)

---

