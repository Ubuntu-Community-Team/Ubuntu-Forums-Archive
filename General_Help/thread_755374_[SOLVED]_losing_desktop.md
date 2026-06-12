---
title: "[SOLVED] losing desktop"
date: 2008-04-14
forum: General Help
---

### Post by drmoore1 on 2008-04-14
Ok when, I completely shut off the computer and turn it back on I lose my desktop. But then I delete the files in tmp, restart and I am ok again. Then I turn it off and the process continues. Any ideas?

---

### Post by ago on 2008-04-14
Are you sure you are not in the Live environment (read only)?
If you have a "Install Ubuntu" icon on your desktop you are.

---

### Post by Gen2ly on 2008-04-14
Probably either a deal with gnome-session or the xorg server lock file.  I've seen this at times when X isn't shut down cleanly.  I think that Ubuntu has a /etc/init.d/local.start, yes?  An easy command to enter would be:

```
rm -r /tmp/*
```

Then.. gnome might be able to not hang.

---

### Post by drmoore1 on 2008-04-14
> **ago said:**
> Are you sure you are not in the Live environment (read only)?
If you have a "Install Ubuntu" icon on your desktop you are.

Yea I am sure. Thanks though. 

I will try this code and see if that fixes it. Do I type this into the file or run it in the terminal?

---

### Post by Gen2ly on 2008-04-15
Putting it in /etc/init.d/local.start will have it run automagically at boot.  This if for Gento, it may be different for Ubuntu though

---

### Post by drmoore1 on 2008-04-17
I finally found the command 

```
killall nautilus
nautilus&
```

This seems to have fixed it.

---

