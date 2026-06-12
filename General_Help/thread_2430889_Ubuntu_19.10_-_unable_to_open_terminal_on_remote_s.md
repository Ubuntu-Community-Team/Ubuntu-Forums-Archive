---
title: "Ubuntu 19.10 - unable to open terminal on remote server"
date: 2019-11-08
forum: General Help
---

### Post by makem2 on 2019-11-08
I have Ubuntu 19.10 installed headless on a Raspberry Pi4, accessing it via ssh and remmina. I am unable to open a terminal instance on the remote screen.

I read that this could be caused by locale settings becoming scrambled during an upgrade. Although my 19.10 is not an upgrade I did find that the settings we incorrect, in fact locale was empty. I corrected everything but still cannot open a remote terminal.

```

makem@ubuntu:~$ localectl
   System Locale: LANG=en_UGB.UTF-8 UTF-8
       VC Keymap: uk
      X11 Layout: gb
makem@ubuntu:~$

```

Pointers to next steps would be appreciated.

It does seem that 19.10 is bleeding edge judging by the number or settings I need help with. If that is true then perhaps it would be wiser to wait a while for those with the knowledge to fix things?

---

### Post by Impavidus on 2019-11-09
I've got no experience with remote desktops. Whenever I login on a remote computer (not very often), I use command line only. Which, considering that you want a terminal, may suffice for you. I'll leave this for the people who have experience with remote desktops.
> **makem2 said:**
> 
It does seem that 19.10 is bleeding edge judging by the number or settings I need help with. If that is true then perhaps it would be wiser to wait a while for those with the knowledge to fix things?That's true. For new users it may be better to stick to LTS releases.

---

### Post by makem2 on 2019-11-09
> **Impavidus said:**
> I've got no experience with remote desktops. Whenever I login on a remote computer (not very often), I use command line only. Which, considering that you want a terminal, may suffice for you. 

Yes, I use the command line, but, I need the command line in the remote instance because the program I use only runs in the terminal 24/7. One of the current problems is, "No terminal".

---

