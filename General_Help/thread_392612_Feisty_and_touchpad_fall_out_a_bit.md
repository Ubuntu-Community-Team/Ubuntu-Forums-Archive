---
title: "Feisty and touchpad fall out a bit"
date: 2007-03-24
forum: General Help
---

### Post by floke on 2007-03-24
I've been using Feisty since Herd 4 and following the updates. Tonight there was a biggy and now my touchpad vertical scroll is running a bit laggy. It still works, but it aint what it was. 

I've checked my xorg.conf with my backup copy I made ages ago and the settings are exactly the same. Also same probelm in both Beryl and Metacity, so can rule out Beryl as the cause.

Any bright sparks with ideas?

---

### Post by MetalMusicAddict on 2007-03-24
Im getting the same thing I think. Mine is kinda jumpy. It isnt smooth but works. Like it steps in small increments.

---

### Post by codesplice on 2007-03-24
I've got the same thing going on as well with my fresh install of Beta.  Takes a hell of a lot of scrolling to do any navigating.

---

### Post by floke on 2007-03-25
Phew. Glad to here Iwasn't imagining it, And that I'm not alone.
In the meantime (until it's fixed - do we file a  bug report?) I might try this:

[http://ubuntu-tutorials.com/2006/12/10/tweaking-your-synaptics-touchpad-laptops-ubuntu-6061-610/](http://ubuntu-tutorials.com/2006/12/10/tweaking-your-synaptics-touchpad-laptops-ubuntu-6061-610/)

Or this

[http://ubuntuforums.org/showthread.php?t=314979](http://ubuntuforums.org/showthread.php?t=314979)

---

### Post by floke on 2007-03-25
Bug reported #95887.

[https://bugs.launchpad.net/ubuntu/+bug/95887](https://bugs.launchpad.net/ubuntu/+bug/95887)

---

### Post by zorkerz on 2007-03-25
Wonderful to find others experiencing this. Does anyone have a clue what might have caused this? I think the bug report will be our best bet for finding someone who knows what could have happened.

---

### Post by ceovsenik on 2007-03-25
I'm having the same problem. I'm also seeing the touchpad make Firefox go back and forward.

---

### Post by zorkerz on 2007-03-25
I am also having the back forward with touch pad problem in firefox ceovsenik do you think this might be a similar issue? They started at different times for me. Possibly we should start a new post or bug report?

---

### Post by ceovsenik on 2007-03-25
I'm sure it's a similar issue, but I have no idea how to replicate it.

---

### Post by ceovsenik on 2007-03-25
using apt-get I just got an upgraded 
xserver-xorg-input-synaptics

let's see if it works :)

edit: works great now.

---

### Post by MetalMusicAddict on 2007-03-26
Back to normal. :)

---

### Post by floke on 2007-03-26
Matter solved.

---

### Post by zorkerz on 2007-03-26
ceovsenik if your are still having the back and forward commands set to horizontal scroll in firefox check out this solution. [http://www.ubuntuforums.org/showthread.php?t=364716](http://www.ubuntuforums.org/showthread.php?t=364716)

---

