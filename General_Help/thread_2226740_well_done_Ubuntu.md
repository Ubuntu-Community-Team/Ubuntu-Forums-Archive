---
title: "well done Ubuntu"
date: 2014-05-28
forum: General Help
---

### Post by Pedroski55 on 2014-05-28
I have been having trouble with Ubu. Whenever I switched on the wireless, the system immediately crashed. Yesterday, an update installed a new kernel:

pedro@pedro-bedro:~$ uname -a
Linux pedro-bedro 3.5.0-51-generic #76~precise1-Ubuntu SMP Fri May 16 16:52:52 UTC 2014 i686 athlon i386 GNU/Linux
pedro@pedro-bedro:~$ 

I tried it for a day before I wrote this.
Now I can switch on the wireless without the system crashing! I don't know what you did Ubuntu, but it worked! Well done!

Now, if you could just fix the segfaults: May 28 06:22:09 pedro-bedro kernel: [   73.380479] unity-panel-ser[1939]: segfault at 322 ip b6ce9a9e sp bfc988fc error 6 in libc-2.15.so[b6baa000+1a4000]

Thank you!

---

### Post by Kleenux on 2014-05-29
> **Pedroski55 said:**
> Whenever I switched on the wireless, the system immediately crashed. Yesterday, an update installed a new kernel:(...) Now I can switch on the wireless without the system crashing!
You mean, you expect an OS to deliver something that is so out of the ordinary: a decent wifi? and it did? Bravo Ubuntu ;-)
Seriously, having some video playing or specific driver issue, ok... but, network? network *has to* work. 
Network Manager always had issues (technical, and also ergonomics wise), and many people prefer the manual (interfaces) management.
You may also install 'wicd' and uninstall Network Manager if it gives problems (and if you don't need vpn etc...). (see also below)  

> **Pedroski55 said:**
> if you could just fix the segfaults
You are still using 12.04! The new 14.04 is LTS and you may want to upgrade! Many things are likely to work better, and wifi is one of them.

---

### Post by Pedroski55 on 2014-05-29
12.04 is LTS They said 5 years. I run 3 OSs on this laptop, so I can see if the machine has a problem. Wifi works fine under Fedora and Windows, so this is an issue specific to Ubuntu. Fedora uses nm, just like Ubu.

2 or 3 years ago or more maybe, with Fedora 17, any time I unplugged the ethernet cable, that crashed the machine. I now always keep at least 2 distros on my machine. One of them will work!

---

### Post by stalkingwolf on 2014-05-29
wifi can be a can of worms.  it has more to do with the adapter than the os. broadcom and intel have always been a pita.  I have one usb adapter i have never been able to get working .  then one day after a fresh install it just worked.  The same with the internal on an older compaq.  I have a netgear that still doesnt work. sometimes additional drivers will fix it.

---

