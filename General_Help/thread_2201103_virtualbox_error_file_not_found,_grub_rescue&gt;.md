---
title: "virtualbox error: file not found, grub rescue&gt;"
date: 2014-01-22
forum: General Help
---

### Post by carlos_lopez2 on 2014-01-22
Hello all, long time reader, first time poster. 

My problem is with regards to an error when trying to move a virtual machine from one host OS to another host OS. 

I dualboot Windows 8 and Ubuntu 12.04 if that helps. 

The situation is that my boss wants to implement a software that can be distributed to customers through virtual machines. 

I tested the software on my Ubuntu OS and through a virtual machine (also running Ubunu 12.04) that is running on my host machine.

The software worked fine and so I went through the procedure to clone the vm and implemented it on a virtualbox in my windows OS and that worked fine too. 

Now I want to take the clones and implement them on another PC, I made 32 and 64 bit .vdi disks versions of Ubuntu 12.04 and tried implementing the 32bit guest OS on a 32-bit Windows XP host.

The resultant output when I tried to start the virtual machine is in the title of the thread. The only thing I did differently is that when I tried creating the clone guest on the Windows XP host is that it forced me to use a system base memory of 256MB as opposed to 1024MB that I did in my own PC. I'm guessing this has something to do with the fact that virtualbox cannot find my file but I am not certain. 

Would anyone be able to point me in the right direction to solving this issue? Any and all help is greatly appreciated, thanks.

---

### Post by Habitual on 2014-01-22
Export the VM to .ova and send that out.

---

### Post by carlos_lopez2 on 2014-01-22
Could you go a little deeper than that, please? You mean export the .vdi as .ova instead? Thanks!

---

### Post by Habitual on 2014-01-23
[https://www.virtualbox.org/manual/ch01.html#ovf](https://www.virtualbox.org/manual/ch01.html#ovf) explains it best.

Have fun.

---

