---
title: "Weird Boot"
date: 2008-04-19
forum: General Help
---

### Post by wkdude18 on 2008-04-19
I have a really annoying problem. My installation works, granted, but every time I have to press ctrl-alt-f1 to open the command line from a blank black screen.

First it goes:

Starting up...
Loading, please wait...
_

and then it phases out into blackness.
So I press ctrl-alt-f1 and open the command line, and then it says

Starting up...
Loading, please wait...
kinit:name_to_dev_tc /dev/disk/by-uuid/ed09cd29-fblc-41bc-990a-abdf0dbdd5d2)=5da5(8,5)
kinit:trying to resume from /dev/disk/by-uuid/ed09cd29-fblc-41bc-990a-abdf0dbdd5d2)
kinit: no resume image, doing normal boot...

And then it does a bunch of checks where it goes loading CD drivers or something [OK] etc. and boots normally. Why doesn't boot "normally" in the first place?

P.S. I'm not sure if I have my l's and 1's right. Please excuse any errors.

---

### Post by ryanhaigh on 2008-04-19
I do not think there is anything wrong other than perhaps the bootsplash failing to show up. What happens if you do not go to the console but just leave the system of the 'black screen'. The messages you see are completely normal the system always looks for a image to resume from and it will only be there if you hibernated/suspended otherwise it will do a normal boot. 

If it is a splash issue press esc when the grub screen comes up, select the first ubuntu line and press e (for edit), then select the second line (the one that starts with kernel and press e again and on the end put vga=791 then press b to boot. If that works we can look at making the change permanently.

---

### Post by wkdude18 on 2008-04-20
It worked, but I forgot how to make a boot change permanent; I'll look that up though. Thanks!:KS

---

### Post by ryanhaigh on 2008-04-20
You will need to add vga=791 to the defoptions line in /boot/grub/menu.lst. I think you will then have to update and install grub but I can't be sure. If you find out would you mind posting back here please.

---

