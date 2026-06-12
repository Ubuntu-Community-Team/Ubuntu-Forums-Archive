---
title: "Tried to delete evolution mail, accidentally deleted too much"
date: 2007-11-23
forum: General Help
---

### Post by lazcisco on 2007-11-23
So now, when I try to go in, i just get the blank brown ubuntu screen and nothing else. I have terminal quickset to 'Fn' so I tried hitting that, but I get an error message and I can't open it. I can boot in terminal only mode, but I can't seem to connect to the internet. So,

I would like to know what terminal command will let me mess around with internet connection configurations (choosing wireless networks and such).

And once I have that, I need to know what packages I need to download so that I can use my computer again. If it is easier just to get the files on a flash drive and move them from there to my computer, I can do that, but the other machines I have available are windows machines (I don't know if that matters).

Thanks for any help...

---

### Post by jken146 on 2007-11-23
What did you do exactly?  You say you tried to delete Evolution - how?  What else did you do?

---

### Post by LuxVoodoo on 2007-11-23
I could be wrong on this, so maybe a second opinion is in order, but it sounds to me like the whole ubuntu-desktop package is gone. You might try "sudo apt-get ubuntu-desktop" and see if that bring everything back.  That's what I would do first, but somebody else may have a better idea.

---

### Post by lazcisco on 2007-11-24
> **jken146 said:**
> What did you do exactly?  You say you tried to delete Evolution - how?  What else did you do?

I went in Synaptic Package Manager and Deleted the files associated with Evolution. That's all I did.

I did sudo apt-get install ubuntu-desktop, but it stays at this 0% Connecting to us.archive.ubuntu.com screen forever (and I don't know how to safely abort it). I think I need to figure out how to connect to the internet before getting the package.


Yeah so the install ubuntu-desktop fixed everything, connecting to the internet took me a while to figure out through terminal though.

---

