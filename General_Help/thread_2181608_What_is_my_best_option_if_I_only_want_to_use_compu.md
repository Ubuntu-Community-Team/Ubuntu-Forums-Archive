---
title: "What is my best option if I only want to use computer for hosting a Minecraft server?"
date: 2013-10-18
forum: General Help
---

### Post by mcortt on 2013-10-18
I have a small pc with the following specs:
AMD E-350 (1.6GHz Dual-Core 64bit)
3GB Memory
Ubuntu 13.10 64-bit 

I am wanting to do two things and two things only. 
1) Host a private Minecraft server - This entails running a Java Archive file.
2) Access another Linux server - Just to input some basic terminal commands.

I would like a bare bones linux distribution with nothing more than the necessary components.
The only programs I will ever use on it are JAVA and VIM.

I currently have GRUB_CMDLINE_LINUX_DEFAULT = "quiet splash text"
Is this sufficiently basic enough so as to minimize resource use by the OS?

---

### Post by oldos2er on 2013-10-18
Moved to General Help.

---

### Post by ian-weisser on 2013-10-18
Since merely running the server does not require a GUI, I use the server version of Ubuntu to host mine.

Do be careful to set up the minecraft server it's own user to keep it secure. Don't run it as root nor you.

Don't forget to learn Upstart, too. You can write a fast Upstart job to launch the server at startup, to back it up at regular intervals, to (more complicated) pause it if nobody is connected, and to stop it automatically when the system shuts down.

---

### Post by mcortt on 2013-10-19
Thanks for the advice!

---

