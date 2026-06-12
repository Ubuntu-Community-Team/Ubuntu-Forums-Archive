---
title: "Change tty resolution Ubuntu server"
date: 2014-08-21
forum: General Help
---

### Post by Cool_Javelin on 2014-08-21
Hi all:

I am running 12.04.2 LTS on a headless server, and have a few programs I automatically start in separate TTY consoles.

I would like to change the resolution of each console AFTER the GRUB boot loader has launched the kernel. I don't care what the resolution is during the GRUB loader, only after the kernel is loaded and running.

In one console, for example, I want 132 x 50, in another, I want the default 80x25, etc.

I have multiple automatic logon's to TTY2, TTY3, TTY4, etc using /etc/init/ttyn.conf. Then, in my home directory, I added lines to my .bashrc file to run various programs in each console.

I would like to issue a command to dynamically change the TTY resolution from 80x25, to, say 132x50 (or something)

Is there a way to do that after it is booted?

I do not have x installed, and this is a server.

Oh, if someone can help me understand, I see resolution is stated a lot in pixels (1042x768, or 640x480, etc...) vs characters (80x24, or 132x50.) Are these synonimous? Do I have to pick a pixel resolution that is some multiple of the character size? (for example, 80x24 characters, 80 characters wide times 8 pixels per character is 640 pixels, 24 lines tall times 20 pixels per line is 480 lines,) this math doesn't seem to compute. Knowledge?

Thanks, Mark.

---

