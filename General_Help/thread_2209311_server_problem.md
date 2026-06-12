---
title: "server problem"
date: 2014-03-05
forum: General Help
---

### Post by YBcPttm on 2014-03-05
I've been trying to install the latest ubuntu server which is 13.10 When I tried to install it, after the section where I choose the language I got an error saying something about needing to use a proper operating system for the kernal which is a 64-bit. I'm not home so I can't remember what it said completely. I did downloaded both the 13.10 and the 12.04.4 LTS with the 64-bit version and I still got that error.

---

### Post by amish_otaku on 2014-03-05
Is this a VM (Virtual Machine) if so, are you using Virtualbox, VMWare, or Citrix? If it's Virtualbox you might be having an issue as your base kernel would not be a 64bit kernel and would thusly not be able to properly emulate a correct 64bit OS environment.

---

### Post by YBcPttm on 2014-03-05
It's a normal pc tower that I'm going to connect to via the network cable. I have been able to install Ubuntu before, but now it's giving me this error so I'm not sure how to fix it.

---

### Post by Doug S on 2014-03-05
You should tell us the exact message you got, otherwise it is difficult for us to provide suggestions. While what you have provided is vague, it sounds as though your computer might not be 64 bit and you should try the i386 version.

---

### Post by YBcPttm on 2014-03-07
This is the complete error that the computer tells me.

> 
This kernel requires an x86-64 CPU, but only detected an i686 CPU.
Unable to boot - Please use a kernel appropriate for your CPU.


---

### Post by Doug S on 2014-03-07
Ya, so what I said before applies, you need the 32 bit version, the i386 version.

---

### Post by YBcPttm on 2014-03-07
I've used the 64-bit version on that machine before and it worked. Also I did try to use the 32-bit, but nothing happened it just stayed on the load up screen that show up before you go to the screen where you enter your options.

---

