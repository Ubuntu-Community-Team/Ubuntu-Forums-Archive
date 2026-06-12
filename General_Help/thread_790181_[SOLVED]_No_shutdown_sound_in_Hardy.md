---
title: "[SOLVED] No shutdown sound in Hardy"
date: 2008-05-11
forum: General Help
---

### Post by BigSilly on 2008-05-11
I used to have one in Gutsy, but I'm not getting a shutdown sound in Gnome Hardy. What should I do? If I select to play it in the sounds menu, it plays fine, but when I logout I get nothing.

Thanks all. :)

---

### Post by pjalegria on 2008-05-11
Same....

---

### Post by wpshooter on 2008-05-11
> **BigSilly said:**
> I used to have one in Gutsy, but I'm not getting a shutdown sound in Gnome Hardy. What should I do? If I select to play it in the sounds menu, it plays fine, but when I logout I get nothing.

Thanks all. :)

Hmmmmmmmmmmmmm !!!

Me thinks you have discovered yet another bug in this O/S.

Mine does not work even under Gutsy.

I generally do not use these types of sounds.  I turn them off by saying NO FILE in the sounds section.  But it is like you say, when I go in to sounds and assign a sound to the logout function, it will play in sounds but will not actually occur when I do a logout.

Do you want to report this as a bug or would you like me to ?

Thanks.

---

### Post by wpshooter on 2008-05-11
I reported this as a bug.

---

### Post by BigSilly on 2008-05-11
> **wpshooter said:**
> I reported this as a bug.

Sorry yeah. That's excellent thanks! 

I remember having this issue in Gutsy, and installing Esound fixed it. But I don't really want to do that here. I think it's probably that Pulseaudio is shutting down before the system does, hence the lack of sound. I'm sure they'll fix it...

Thanks again for putting a bug report in. I've never done that myself, so I'm glad you did it! Do you have a link to it?

---

### Post by wpshooter on 2008-05-11
[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

---

### Post by nick_h on 2008-05-11
> I remember having this issue in Gutsy, and installing Esound fixed it.
Yes, with Gutsy I installed the *esound* package to get it working.
I'm not sure if it the correct approach in Hardy though.

---

### Post by ebe326 on 2008-05-11
This is the way I fixed it. It's not really the right way to do it but so far it's working.

[http://ubuntuforums.org/showthread.php?t=789858](http://ubuntuforums.org/showthread.php?t=789858)

david

---

### Post by BigSilly on 2008-05-17
Hey thanks for this. I just spotted your reply today, and have done this and so far it's working great. 

Thanks again. :)

---

### Post by conscious on 2008-05-17
Link to the bug report (already closed):
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/229245](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/229245)

The workaround with installing esound still works.

---

### Post by BigSilly on 2008-05-19
Problem is, when you go to install esound from Synaptic, it tells you it wants to remove Ubuntu-desktop! So really, you can't install esound in Hardy safely. It looks that way to me anyway.

The workaround that ebe326 provided will do for now, but it's not ideal, and especially disappointing when you consider Ubuntu has been doing this for a while.

Oh well.

---

