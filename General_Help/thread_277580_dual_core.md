---
title: "dual core"
date: 2006-10-14
forum: General Help
---

### Post by linuxnoob40 on 2006-10-14
ok aftre my m/b had a melt down i decided it was time to go dual core so the question here is how do i utilize this in linux as its only showing one core ?

---

### Post by MetalMusicAddict on 2006-10-14
If its a AMD and you use Dapper, just use the K7 kernel. If its Intel I think the 686 will do. They both (to my knowlege) have SMP enabled.

If on Edgy use the -generic kernel.

---

### Post by hinne on 2006-10-14
I've never done this before (since I don't have a dual core machine) but you need a dual core kernel. Search for kernel-image and choose the one that ends with 686-smp (for intel core duo) and k-something-smp for AMD. You might also want to investigate whether you should be on the 64 bit version, since most dual core processors have 64 bit capabilities?

---

### Post by linuxnoob40 on 2006-10-14
thanx and yes this does have the 64 bit processer but 64 bit ubuntu is very unhappy with my machine have tried 3 times unsuccesful install and said to heck with it and stuck with 32 bit

---

### Post by Chayak on 2006-10-14
Yes, getting an SMP kernel is the key.  I'm running a dual/dual core workstation now and it sees all of the cores.

---

### Post by linuxnoob40 on 2006-10-14
ok i installed that smp kernel and when i select it upon reboot it says "kernel panic something" i forget  (i have a bad memory) what is that all about?

---

### Post by MetalMusicAddict on 2006-10-15
Are you doing a 64bit install? Can you give us some system specs?

---

### Post by linuxnoob40 on 2006-10-15
Amd Athlon 64 x2 4200 (running 32 bit ubuntu), 1 gig ram, 200 gig sata hd dunno what else you would want for info so let em know if you need something more


exact error msg i get is
kernel panic: vfs :unable to mount root fs on 08:02

this is where the system will hang and i have to reboot and use the other kernel

---

