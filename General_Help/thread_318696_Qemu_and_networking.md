---
title: "Qemu and networking"
date: 2006-12-14
forum: General Help
---

### Post by sikke on 2006-12-14
Hi!

I need help with Qemu and networking. I installed win xp sp2 and started qemu with -net user -net nic as mentioned at [http://ubuntuforums.org/showthread.php?t=39513](http://ubuntuforums.org/showthread.php?t=39513) but it doesn't work. I've also tried number of setups I found from these forums and google.

Cheers

Sikke

---

### Post by rianquinn on 2006-12-20
I have the same sort of problem. I have been working on this for a few days now. I need to create a Qemu Virtual Machine to do some Kernel experiments that require networking. The problem I am having is after hours of playing around I got the Bridge to work, and could talk to the Guest from the Host, but lost internet on the Host. If I turn off the bridging my internet starts working again, but I lose my connection to the guest. 

I also tried VMPlayer but I can't get a single appliance to bootup. Xen doesn't seem to be any better since you still need to setup bridging which is the problem in the first place. 

If anyone can help it would be most appriciated.

Rian

---

### Post by rianquinn on 2006-12-29
Well I gave up. :(

I dual boot Ubuntu and Kubuntu now. Ubuntu is now my Test machine. 

Rian

---

