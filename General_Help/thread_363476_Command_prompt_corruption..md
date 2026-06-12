---
title: "Command prompt corruption."
date: 2007-02-17
forum: General Help
---

### Post by ykhun on 2007-02-17
Rig:
Distro: Ubuntu 6.10 Edgy
Mobo: Asus P5B Deluxe
GFX: GeForce 7300

Problem:
The command prompt become corrupted after a day. It works for a day after each restart and subsequently it gets worst and worst. All the characters are just messed up and not readable. But when a key is pressed, u see a mess of pixels painted on screen. I could ssh into the machine and everything is fine. All the services running on the machine are good. Just the command prompt corruption on the monitor plugged into the box.

Pretty sure its not the monitor since i'd tested with a few and they all have the same problem. I think it could be the gfx card. But i'm not even using any 3D acceleration etc. I'm just using it for the prompt.

Any1 had the same problems or something close to it and how did you fix it?

Thanks!

---

### Post by Muzik83 on 2007-02-17
The only time I have seen this happen is when I accidentally cat a binary file.

Have you tried the "reset" command to reset your terminal?  You could also try using another shell, ubuntu comes which bash and sh

---

### Post by ykhun on 2007-02-19
> **Muzik83 said:**
> The only time I have seen this happen is when I accidentally cat a binary file.

Have you tried the "reset" command to reset your terminal?  You could also try using another shell, ubuntu comes which bash and sh

Yeah, tried "reset". Didn't work. The text is still as corrupted as ever. The shell change didn't work too.. :(

---

### Post by llamakc on 2007-02-19
Share a screenshot with us, and let us know which locale you use, and let us know if you have the same issue when using at TTY (ctrl-alt-F2 and login to test).

---

### Post by ykhun on 2007-02-23
Trust me, the camera wasn't shaky when this pic was taken.

[IMG]http://www.uploadyourimages.com/img/639497pict3482.png[/IMG]

---

### Post by llamakc on 2007-02-23
Is that in a TTY or a fullsized Terminal (PTY)? Are you passing any specific vga="???" commands at boot time?

---

### Post by ykhun on 2007-02-24
Fullsize terminal. The vga= setting in GRUB was nothing initially and it was corrupted after a day. The image shows the one where i set it to vga 1024x768 but same thing happened, it gets corrupted after a day. :(

---

