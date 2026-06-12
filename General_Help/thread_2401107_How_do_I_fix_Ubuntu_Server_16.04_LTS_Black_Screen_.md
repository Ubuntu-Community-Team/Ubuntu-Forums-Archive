---
title: "How do I fix Ubuntu Server 16.04 LTS Black Screen with White Cursor after boot?"
date: 2018-09-13
forum: General Help
---

### Post by djcjf on 2018-09-13
Hi there I have had this problem since install of my headless Ubuntu Server but I was able to get it to boot by holding shift and going to Grub and selecting *Ubuntu. When I would boot this way I get a Ubuntu loading screen with a black background and then I would be taken to my headless login screen. Since I wanted my Ubuntu Server to boot with out me holding shift I went into the Grub config file and set auto boot grub to true to boot grub automatically every start. Now when it boots Ubuntu Server it takes me to a loading screen with a purple background and then boots to a black screen with a blinking white cursor and hangs there. I have already tried searching this forum and Google for help with no luck :( BTW I am running Ubuntu Server on my DELL Dimension 4600 Any Help Is Greatly Appreciated Thanks! :D - djcjf

---

### Post by TheFu on 2018-09-14
Welcome to the forums.

Have you checked the boot logs to see where things are getting stuck?  If it is waiting on a network or disk that will never show up, that needs to be fixed.

---

### Post by djcjf on 2018-09-16
> **TheFu said:**
> Welcome to the forums.

Have you checked the boot logs to see where things are getting stuck?  If it is waiting on a network or disk that will never show up, that needs to be fixed.

That's a good idea where can I find the boot logs?

---

### Post by TheFu on 2018-09-16
/var/logs is the normal place.
There's also the **journalctl** tool.  If you can't boot into the system, use a flash drive with a burned ISO to get booted. Then you'll need to tell journalctl to look at the boot logs for the other disk, not the "live boot" session you are in.  I'm not certain how to do that, but the manpage should have it.

---

