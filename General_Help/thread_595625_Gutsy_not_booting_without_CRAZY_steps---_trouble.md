---
title: "Gutsy not booting without CRAZY steps--- trouble"
date: 2007-10-28
forum: General Help
---

### Post by mike_302 on 2007-10-28
I installed gutsy today after wiping my feisty partition (all of my linux OS's here are 64-bit). When I get to the Grub, I select the gutsy OS, it qucikly does its little line at the bottom (the one about keymapping or something???) no errors, and then the screen goes black... No boot screen. The loading light appears to be flashing fairly rapidly after 5 seconds, as if it were loading something, but nothing will happen... period. You could wait 5 minutes it wouldnt change. HERE'S THE CATCH!
If i wait about 30 seocnds, then hit ctrl+alt+f1 (and only f1, not f7) it brigns up a few lines of command, all beginning with "kinit" but the only one I could read and remember was "kinit: no resume image, doing normal boot" then gutsy loads... and everything is fine and dandy from there on out. But CLEARLY you guys can see that this is not what it should be doing. Can anyone troubleshoot this (assume I'm a linux newb cuase in reality that s what I am... although I know my way around Windows pretty well, but thats not going to do much here)

Thanks in advance!

---

### Post by computer doc on 2007-10-29
Forget the 64 bit stuff.  Download Gutsy 32 and set-up to FORLONGS BLOG, before you do anything else  and follow it to the tee.  You`ll be very happy.  Good Luck.:lolflag  You`ll love it.

---

### Post by #Reistlehr- on 2007-10-29
> **computer doc said:**
> Forget the 64 bit stuff.  Download Gutsy 32

Not the best advice, no offense. Perhaps his systems don't support 32-bit os's. Like my laptop, the 32-bit version is so unstable, i get a kernel panic everytime the mouse moves, which forces the usage of a 64-bit os. 

mike: try adding: noapic to your boot line when you boot from grub, and see if that helps. also, you might want to check, /etc/usplash and check the resolution to make usre it supports that of your monitor.

---

### Post by CubeXombi on 2007-10-29
You can fix the issue quickly by just editing your boot menu

sudo nano /boot.grub/menu.lst 

# or you can use gedit
and delete the "splash" option from your kernel line.

Mine looks like:


title		Ubuntu 7.10,
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro quiet
initrd		/boot/initrd.img-2.6.22-14-generic



Just as a heads up though you will get to see all the fun ugly text as your machine starts up.

---

### Post by mike_302 on 2007-10-29
Well, before I delete the grub image all together, I'd like to try checking the resolution like you say and also adding that noapic line but the only thing is: I am not 100% sure of where to add that. Do I hit c at the GRUB to open a command line orrr... What? Do I add it while in Ubuntu? If you could point that much out to me, that would be great. Thanks! (remember, consider me a fair bit of a newb with linux)

---

### Post by mike_302 on 2007-10-30
Bumping this. I had answers before so I know people can suggest stuff for my problem. All I'm looking for now is to know HOW  to add the noapic line to my boot and HOW to check the resolution. PLEASE?

---

