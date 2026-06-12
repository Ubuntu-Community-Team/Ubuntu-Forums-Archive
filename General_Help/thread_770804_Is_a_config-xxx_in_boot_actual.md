---
title: "Is a config-xxx in /boot actual?"
date: 2008-04-27
forum: General Help
---

### Post by klirik on 2008-04-27
Just messing: every manual on kernel compiling said that the most conveinent way to modify your kernel is take an existing config and modify it.

I just installed Hardy with generic kernel. So, I take /boot/config-2.6.24-16-generic, copy it into /usr/src/linux (the place where sources of kernel) and rename into .config

But... this config looks really strange... I've investigated it with xconfig - which options are checked. Kernel debugging is "on" - and so, compiled initrd became huge size because of it. Sound in device drivers is "off" - totally! No alsa, no oss. But - this binary kernel I use actually has sounds! So - may be I just confused, but can somebody explain me - if this generic .config file is actual?

The actual problem I catch with this strange .config - I've downloaded sources of v4l-dvb - since my A16D is not supported by generic kernel. I've called make && make install - and it made all modules _except_ the audio support - exactly because this audio is off in config file.

So - how to do with it? Is any way exists to have and manage _actual_ config - I mean the one which will make the SAME kernel as currently run when you simple compile it with no changes?

---

### Post by rubicon on 2008-04-27
Have you followed the regular guide to compile kernel or 'Ubuntu-way'? ;)

Okay. .config *is* actual *if* you use it.

You see, we got separate packages for kernel, for modules, for restricted modules. If so, why generic kernel need ALSA if it will be in another package? ;) And so on.

About size of initrd &#8212; you should experiment with config. Debugging is enabled by default, for example, so it is ok to disable. Though I don't know *why* it is enabled in generic kernel...

I believe that all questions you ask are reasonable and nothing has went wrong so far :P

---

### Post by klirik on 2008-04-27
yeh, I've found the linux-ubuntu-modules package with practically all the rest sources.

However, here is concrete question: how can I compile the application which depends from ALSA, regarding that the ALSA is switched off in the kernel configuration? I mean - with no kernel recompilation?

More concrete: I need to compile already mentioned v4l-dvb from linuxtv.org. When I do it, it recognizes that the kernel doesn't configured with sounds - and automatically escape compilation of any sound modules. I need saa7134-alsa, but I can't get it with default config.

For the moment I have no idea how to do it. May be by manual compilation together with linux-ubuntu-modules (since this package also includes saa7134-alsa, but it is different and cause SF error being combined with linuxtv's other modules).

---

