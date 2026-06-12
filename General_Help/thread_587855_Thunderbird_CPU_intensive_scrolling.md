---
title: "Thunderbird CPU intensive scrolling"
date: 2007-10-23
forum: General Help
---

### Post by jazzgossen on 2007-10-23
I just did a clean 7.10 installation, and I'm using the nv driver with an Asus N6600 graphics card.

Scrolling the message list in Thunderbird is very CPU intensive. The system is very snappy otherwise, and scrolling of the message text in Thunderbird is also fast, but when I scroll the list of mails in my inbox, the CPU load goes up drastically, and the scrolling is very sluggish.

Has anyone else seen this?

---

### Post by 1/0 on 2007-10-23
You should have the proper nvidia driver installed instead of nv. How is scrolling in Firefox?

---

### Post by jazzgossen on 2007-10-23
Firefox is fine. I can't use the nvidia driver in 7.10 because it causes my system to freeze completely (though it has always worked in previous versions of Ubuntu). Strange, huh?

---

### Post by #Reistlehr- on 2007-10-23
Install the drivers via Automatix: [http://getautomatix.com](http://getautomatix.com)

They have i386 and AMD64 deb's and repo's. 

I have seen this also. After reinstalling the nvidia drivers i ran the command:

```

sudo nvidia-xconfig --add-argb-glx-visuals

```

And it seems to have fixed it. It stills slightly spikes the CPU but it scrolls smooth, and no lag is noticable.

---

### Post by 1/0 on 2007-10-23
Automatix is [dangerous]("http://mjg59.livejournal.com/77440.html"). It has several [leaks]("http://mjg59.livejournal.com/77440.html") that I wouldn't want to expose myself to. Just enable the [restricted extras]("http://www.5thwind.com/?p=48") and pick one from there instead. Its working for me with the nvidia-glx-new and nvidia-xconfig.

---

### Post by #Reistlehr- on 2007-10-23
> **1/0 said:**
> Automatix is [dangerous]("http://mjg59.livejournal.com/77440.html"). It has several [leaks]("http://mjg59.livejournal.com/77440.html") that I wouldn't want to expose myself to.

That i did not know. Thanks for the link, and i can't believe i've been exposing myself to this without knowing!!!

---

### Post by jazzgossen on 2007-11-01
I just upgraded to 7.10 on my laptop, where I am using the nvidia driver, and I see the same symptoms there too. Everything is generally very good, but scrolling the message list in Thunderbird is very slow.

---

### Post by Forceflow on 2007-11-15
I'm experiencing the same problem

Ati X1600, Amd 3000XP, using fglrx drivers.

Scrolling in Thunderbird message list and the CPU load hits the roof.

---

### Post by yesterday on 2008-03-11
I am having the same problem with an NVIDIA 7900gs and the latest drivers installed via Envy.  I used the option specified above, but have had no luck.  Has anyone logged this in launchpad?

EDIT:  I would also like to add that it shouldn't be necessary to enable a proprietary driver to have Thunderbird function properly.

---

### Post by ktulu1115 on 2008-05-09
Same issue here, and I'm sure it's not the hardware.  Running nvidia driver, compiz disabled.  No issues in FF at the moment (with scrolling at least).

And yesterday I agree - something is amiss, this should work just fine without a binary driver.

---

