---
title: "LiveCD Problems."
date: 2005-08-29
forum: General Help
---

### Post by loudambiance on 2005-08-29
At the risk of sounding like everyone else. I am having problems with the LiveCD. I've ran many different livecd's on my laptop and such. But when i boot Ubuntu on my pc even with debug options and such. I get this far:

loading /install/vmlinuz.............
loading /instal/initrd.gz............
ready...

then i get  a curser that blinks and it will not respond to alt+ctrl+del or any key combination. My system setup is as follows:

Amd xp +3000
2gb ddr 333
2 x 120gb hdd's
1 x dvd-rw
agp radeon x800pro

any suggestions would be greatly appreciated. I ran a second live cd (can't remember which one) and got a very similar problem, so I don't think it's ubuntu unique problem. But any help would be great.

~Daniel

---

### Post by weekend warrior on 2005-08-30
Things to try...

Check the MD5SUMS of the ISO

Lower the speed of the burn process

Change burning application

Use a different/new CD for burn

Check boot options for anything related to your laptop/pc


HTH

---

### Post by loudambiance on 2005-08-30
I've checked the cd, It is a real ubuntu cd, not a personally burned copy. It worked wonderfully on my gateway laptop. As far as the boot options, I've tried every one that is listed when you go through the f keys, and I still haven't figured anything out.

---

### Post by Mormy on 2005-09-01
At the boot menu try to write:

live vga=771


;-) 

Bye

---

