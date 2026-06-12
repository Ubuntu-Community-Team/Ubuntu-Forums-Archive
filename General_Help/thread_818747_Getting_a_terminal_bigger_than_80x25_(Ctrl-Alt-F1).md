---
title: "Getting a terminal bigger than 80x25 (Ctrl-Alt-F1)"
date: 2008-06-04
forum: General Help
---

### Post by badp on 2008-06-04
I have a 1280x800 display and I'd like to take full advantage of it even when I'm using the tty's displays (Ctrl-Alt-Fn).

I've read it involves enabling VGA in Grub, but I'm not sure about how to set it up.

Any help?

PS: While adding tags I've seen "tty watermark"... hell, why not add in that too while I'm at it? :)

---

### Post by zach382 on 2008-06-04
You have the right idea. Just google around. I think it was like vga=775 I dont remember where i found the directions.

---

### Post by Forlong on 2008-06-05
Install Startup-Manager, it's in the repos:
```
sudo apt-get install startupmanager
```
There's an option to configure the resolution at boot time (and thus in the console).

---

