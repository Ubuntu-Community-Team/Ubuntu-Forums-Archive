---
title: "Edgy Eft and Gmail"
date: 2006-11-18
forum: General Help
---

### Post by Godspeed! mux on 2006-11-18
Hey everyone,

I just upgraded to Edgy Eft on my laptop, and everything works well except for when I log into my Gmail account.  When I go to Gmail I enter my username and password, and it redirects me to my mailbox. It loads, and I can see my mailbox for a quick glimpse and then Firefox closes abruptly.

Anyone know why this would be happening, or how I would go about finding the problem/solution?

Any help would be great, since this is a pain to deal with.

---

### Post by prizrak on 2006-11-18
This should be moved to support. 

It is something that is individual to you, I have Edgy and Gmail and have no problem. 
Here is what you should do.
open up your terminal and type in
```
sudo touch /forcefsck
```
Then restart your computer. It has helped me with FF issues before. If that does not work. 
Install Epiphany and use that to go to gmail.

---

### Post by namah on 2006-11-18
You may have a problem with your upgraded Firefox settings.

Try quitting Firefox then

rename ~/.mozilla to ~/.mozillabak

then restart Firefox

If that works then you'll know that the settings in your profile are corrupt. I'd then reinstall any extensions etc afresh. You could copy over your bookmarks from the old directory (.mozillabak) but I'd leave it at that.

hth

---

### Post by Godspeed! mux on 2006-11-20
Hey guys,

Thanks for the advice, but neither method worked.  I renamed ~/.mozilla to ~/.mozillabak and I also tried sudo touch /forcefsck

Both times I restarted my computer and Firefox.  It still shuts down when I open up Gmail.  I was searching through a different forum and it did the same thing.

If anyone has any other suggestions let me know!

---

### Post by Godspeed! mux on 2006-11-21
I solved the problem.

I believe it was Flash (but may have been Java or something else) that was causing the problem.  I had used Automatix previously, but just installed the new version for Edgy, and re-installed Flash and a few other Firefox plugins and all is well.

---

