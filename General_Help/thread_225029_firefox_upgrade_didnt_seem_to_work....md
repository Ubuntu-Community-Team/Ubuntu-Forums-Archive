---
title: "firefox upgrade didnt seem to work..."
date: 2006-07-28
forum: General Help
---

### Post by Polygon on 2006-07-28
i just got back from a trip and when ubuntu told me about an upgrade, it just let it run. one of the updates was firefox 1.5.0.5.

after i let it install, it told me i had to restart firefox, which i did. 

when i went to help>about after the upgrade, it still said i had version 1.5.0.4. i went back to synaptic and it said that my version was 1.5.0.5 installed....

i had to gksudo firefox and do the upgrade from help>check for updates to make it update... but im wondering why it didnt upgrade when i ran update-manager?

---

### Post by SonicTempest on 2006-07-29
I'm having a related issue, in that no matter how many times I do sudo apt-get update, I can't get the new version of Firefox. As a result I'm still stuck on version 1.5.0.3.

---

### Post by Polygon on 2006-07-29
you could just do a "gksudo firefox" in terminal, then go to help > check for updates and it will update itself.

---

### Post by SonicTempest on 2006-07-29
gksudo didn't work, but I found out what the problem was - I didn't have the appropriate repositories enabled. -_-

---

### Post by aysiu on 2006-07-29
There was someone in another thread who didn't get it because the security repositories were commented out. Make sure you have the right repositories enabled.

If you're not sure, you may want to take at my list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Polygon on 2006-07-29
well im saying that i DID get it, and it installed, but when i restarted firefox it still was at version 1.5.0.4 and not 1.5.0.5, its like it never even installed.

---

### Post by grsnow on 2006-07-30
I am having the exact same problem. I received the Firefox 1.5.0.5 update, via the update manager, but in "Help -> About Mozilla Firefox" it still says that I have version 1.5.0.4.

Any fixes or suggestions out there???

Gary

---

### Post by DoktorSeven on 2006-07-30
Are you sure Firefox isn't running somewhere, like the download manager window isn't open or something?  All instances of it have to be closed before it'll run the new one.

Worst case, see if it's running in **ps aux | grep firefox** and kill it (**killall firefox-bin**).

---

### Post by grsnow on 2006-07-30
I've even re-started the computer, its still running the old 1.5.0.4 version.

Any ideas out there???

Gary

---

### Post by grsnow on 2006-08-01
Another Ubuntu Update was pushed out today (actually alot of them). Forefox was one of them (again it was 1.5.0.5), and still after the update when I launch Firefox I still only have 1.5.0.4. Whats up with that? Also, why did Update Mamager think that I needed to update it? If I look in Synaptic, it says that 1.5.0.5 is installed already.

Still looking for any advice...

Thanks...

Gary

---

