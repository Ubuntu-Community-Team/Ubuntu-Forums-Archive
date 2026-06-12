---
title: "backup personal data"
date: 2008-03-06
forum: General Help
---

### Post by notesetter on 2008-03-06
Hello,

I'm currently cutting my Linux teeth on a Compaq notebook with Ubuntu Studio 7.10.

Suppose I'd like to do a fresh install of Ubuntu Studio Hardy Heron (when it becomes available) from the DVD. How do I backup all of my personal data like files, email, settings etc. so that I may transfer them to the new install later. Do I need only to copy my home folder? Are there other folders that need to be transferred? Thanks.

Dave

---

### Post by FuturePilot on 2008-03-06
Yes pretty much all you need is your Home folder. Be sure that you get all the hidden dot (.) folders. Press Ctrl+H in your home folder to see all of them. Those are important because they have all your application settings and also most likely your emails if you use a client.

---

### Post by Oldsoldier2003 on 2008-03-06
> **FuturePilot said:**
> Yes pretty much all you need is your Home folder. Be sure that you get all the hidden dot (.) folders. Press Ctrl+H in your home folder to see all of them. Those are important because they have all your application settings and also most likely your emails if you use a client.
Simply copying the home directory can be problematic instead do this:

```
find . -depth -print0 | sudo cpio --null --sparse -pvd </path/to/destination/>
```

A full tutorial is available here: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

edit: I'll also add that as long as you pay attention and make the proper changes to your paths and fstab to reflect your system, this tutorial works flawlessly. I've used it on a couple machines recently.

---

### Post by Het Irv on 2008-03-06
If you want to backup your /home, the Quickstart Program in my sig is a GUI based program that does just that (in case you are not comfortable with CLI).

---

### Post by notesetter on 2008-03-06
Thanks for the tips. I'm learning!!

---

