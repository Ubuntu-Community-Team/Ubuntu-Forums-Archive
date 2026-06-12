---
title: "how do you undo updates from update manager"
date: 2007-03-03
forum: General Help
---

### Post by Panhead Bill on 2007-03-03
I've just updated edgy per the update manager.  It had "borked" my mythtv backend.  Is there a way to undo the updates?

---

### Post by solar george on 2007-03-04
No. You'd have to reinstall the previous version.

---

### Post by Panhead Bill on 2007-03-04
Is there a list stored somewhere on my drive that lists the latest changes or updates?  (and where is the list?)

---

### Post by x1a4 on 2007-03-04
> **Panhead Bill said:**
> Is there a list stored somewhere on my drive that lists the latest changes or updates?  (and where is the list?)

As far as I know you have to keep track of installations yourself.  Whenever I install something, I use Synaptic to save the state of all my packages first.  This way, if things go awry, I can roll back to the previous state in no time at all.  If you haven't created an image of what packages you have installed, you have to reinstall/remove things by knowing exactly what package you installed/updated.

---

### Post by Panhead Bill on 2007-03-05
That is what I was afraid of.  Oh well, back to debugging.

---

### Post by skew on 2007-03-11
I'm having the same problems as you. Did you find a better solution than that which has been offered so far?  

  I think It's terrible that this should be so difficult an issue to fix. 
Adding an undo feature to the Update manager should be an obvious addition!

---

### Post by Panhead Bill on 2007-03-21
Not yet.  The search for functionality continues . . .

---

### Post by hikaricore on 2007-03-21
You could start by checking the contents of /var/cache/apt/archives/ and comparing it with the dependancies of mythtv via synaptic.

```
ls -la /var/cache/apt/archives/
```

 Check the dates on the files compared to when you started having problems and narrow it down.  With this and the dependancies I mentioned earlier.  :)  It may narrow down your search.

---

### Post by beardiggin on 2007-06-07
Hope this isn't too late.  I have found that the Synaptic Package Manager keeps a history of packages you have installed.

When you start Synaptic Package Manager, click on file in the menu and then click history.  I am using Feisty Fawn 7.04 and It has a list of all the updates that have come through update-manager.

cheers

---

