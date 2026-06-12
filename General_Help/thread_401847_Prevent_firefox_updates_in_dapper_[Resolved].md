---
title: "Prevent firefox updates in dapper? [Resolved]"
date: 2007-04-05
forum: General Help
---

### Post by crispy_420 on 2007-04-05
I finally went through with it and manually updated firefox in dapper to version 2.0. And it works fine for me. 

My question is with updates. Synaptic wants to "update" my version of dapper to what it thinks is the newest official version. But with 2.0, updates are taken care of within the browser and not via apt. I have a good feeling not to dare to update and I have not. But how do I tell it I don't care if there is a new version and stop the update notices? Is that possible?

---

### Post by Spr0k3t on 2007-04-05
One thing you can do is to remove Firefox from Synaptic and download the separate installer from  GetFirefox.com.  Then handle the updates through Firefox and not worry about Synaptic.  Just an idea is all.

---

### Post by crispy_420 on 2007-04-05
If I do that it wants to remove some major peices of Ubuntu. It trys to remove: gnome-core, ubuntu-desktop, etc.

Any more ideas?

---

### Post by Spr0k3t on 2007-04-06
Off the top of my head, that's about as much as I can think of.  Only other option might be to upgrade to feisty.  Although, you may be able to step back to the revision Dapper is wanting to use and install Firefox on the side... just a thought.

---

### Post by foxmulder881 on 2007-04-06
Just don't install the Firefox update when prompted. ie. Untick it.

---

### Post by aysiu on 2007-04-06
Go to Synaptic

Search for Firefox

Then go to Package > Lock Version

More details [here](http://ubuntuforums.org/showthread.php?p=2076216#post2076216)

---

### Post by wislon on 2007-04-06
aysiu : I've tried this myself on a couple of occasions, for a couple of things, and it doesn't appear to work for me. I click the 'lock version' menu item, and nothing happens. Is there supposed to be an indicator of some sort? Also, if I do this, do I just need to lock the firefox, or do I need to lock all the associated stuff with it (like the gnome support etc. they put with it).

TIA :)

wislon.

---

### Post by crispy_420 on 2007-04-06
Looks that may have solved it but will have to wait and see. I'll post back in a few days or sooner if updates come up. I'd love to upgrade to feisty but I spent way too much setting up and everything works the way I want it to (ati drivers, logitech mouse, etc.).

---

### Post by aysiu on 2007-04-06
I've never actually tried it (I have no problems updating the Ubuntu Firefox even though I use the Mozilla one). Please report back if locking actually prevents updates to Ubuntu's Firefox.

---

### Post by crispy_420 on 2007-04-06
OK I locked it and it is no longer telling me there is an update. Exactly what I wanted to do. So it appears to be a fix, but I'll come back if it comes back. I don't see that happening though.

Thanks guys...

---

