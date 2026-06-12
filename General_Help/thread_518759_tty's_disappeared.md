---
title: "tty's disappeared"
date: 2007-08-06
forum: General Help
---

### Post by Tiftof on 2007-08-06
I recently noticed that I don't have any tty's anymore. Switching using ctrl-alt-Fx just gives a blank screen with a blinking cursor. 

Something else that probably is related to this: when booting and a scan of one of my ext3 partition has to take place, then I also only get a blank screen with a blinking cursor during boot.

Hopefully someone can help me.

Thanks

---

### Post by Tiftof on 2007-08-06
Update: Strange thing: I can still give in commands in my tty's. When I type "locate x", I can hear my hd working. But the screen still displays nothing but a blinking cursor

---

### Post by mannheim on 2007-08-06
This has happened to me after a "suspend to RAM" and a resume. In my case, I think it is a video-card/driver issue. (I recently updated to the most recent version of nvidia's driver. Before the update, suspend+resume didn't work at all; not it "works" but with this bug -- invisible ttty's). Sorry this is  just a "me too" post.

---

### Post by Tiftof on 2007-08-06
I seem to have 'solved' it. Booting the kernel with vga=normal parameter brings tty's back. Resolution in tty's is ugly low then. Going to try some other options. Originally my vga parameter was 792.

---

