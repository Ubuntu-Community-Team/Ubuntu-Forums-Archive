---
title: "kqemu support not compled in qemu"
date: 2007-09-24
forum: General Help
---

### Post by i23098 on 2007-09-24
Hi,

I've got gutsy on an AMD 64 and installed QEMU from the repos and I also installed kqemu from the repos and the help of module-assist following the instructions on [http://knightlust.blogspot.com/2007/06/qemu-and-kqemu-installation.html]("http://knightlust.blogspot.com/2007/06/qemu-and-kqemu-installation.html").

The problem is that when trying to use -kernel-kqemu option it says is invalid. In QEMU, in monitor mode I've made 'info kqemu' and it gives 'kqemu support: not compiled'.

Why :confused:

Did I do something wrong? How can I get a qemu package with kqemu support compiled?

Regards

---

### Post by i23098 on 2007-10-02
Help [-o<

Did I do something wrong, or no one notices that kqemu isn´t used? :-k

---

### Post by jocko on 2007-10-02
Have you tried loading the kqemu module?
This command should do it:
```
sudo modprobe kqemu
```
If that helps, you may need to add kqemu to your /etc/modules file:
```
gksudo gedit /etc/modules
```
And add "kqemu" (withouth the quotes) to a new line.

---

### Post by i23098 on 2007-10-03
Yes, I've loaded the kqemu module with modprobe. I've also sudo chmod 777 /dev/kqemu.
KQEmu loads correctly, QEmu doesn't use it :( As I said:

> **i23098 said:**
> 
The problem is that when trying to use -kernel-kqemu option it says is invalid. In QEMU, in monitor mode I've made 'info kqemu' and it gives 'kqemu support: not compiled'.


I once had it working from the sources but since it's on repository it's easier to mantain, but only if it works...

---

### Post by i23098 on 2007-10-09
Found the problem :rolleyes: It was my fault...

For some reason qemu command in a 32 bits environment works ok, but on a 64 bits qemu won't work ok :(

To run successfully qemu with kqemu on a 64 bits system it must be run with qemu-system-x86_64 command :mad: Don't understand why it isn't the same command on a 32 and a 64 bits system, but ok. Now it works :KS :)

---

