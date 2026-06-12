---
title: "curious - transfer from one drive/ssd"
date: 2021-09-27
forum: General Help
---

### Post by jgw on 2021-09-27
I am curious.  I have two ssd's.  One is the main drive in one machine, the other is blank.  Is there a way to transfer everything from the main drive to another ssd so that if something happens to one I can slip the other one in?  Oh, one is s500gb and the other is 1tb  (I deleted the 1tb with: sudo shred -n 1 -vz /dev/sdb)

Thank you....................

---

### Post by mikewhatever on 2021-09-28
Yes, use any HDD cloning software. Here is something to get you started: [https://askubuntu.com/questions/741723/moving-entire-linux-installation-to-another-drive](https://askubuntu.com/questions/741723/moving-entire-linux-installation-to-another-drive).

PS: The shred thing was completely unnecessary. This is something you'd do before, for example, selling a storage device.

---

### Post by HermanAB on 2021-09-28
Note that using shred on a solid state device is not a good idea (various reasons - don't want to get into a long discussion about it now).

There are multiple ways to clone a disk (as simple as using a command like "cat /dev/sda > /dev/sdz").  The main problem is that after copying the thing, the UUID is still different, so when you install the disk, you will have a boot manager problem, unless you rewrite the UUID also.

---

### Post by jgw on 2021-09-28
thanks for the replies!

I used the shred thing to overwrite the ssd as I somehow managed to screw it up whilst messing around.  I was thinking of using it as a main drive in another system. 

I will mark this as solved............

---

### Post by QIII on 2021-09-28
Hold on now!

Shred probably made a mess of your SSD.

I would recommend that you follow the instructions [here]("https://wiki.archlinux.org/title/Solid_state_drive/Memory_cell_clearing") to get it back to a clean (factory reset) state.

---

