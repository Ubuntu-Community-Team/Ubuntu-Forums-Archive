---
title: "Why isn't chrome in the 14.04 Software Center?"
date: 2014-10-01
forum: General Help
---

### Post by Tom_Carr on 2014-10-01
I thought chrome was in the software center a few months ago.  Now on one machine, there is only chromium, or another, neither chrome or chromium.  These are both 14.04.

---

### Post by Frogs Hair on 2014-10-01
Chrome is proprietary Google software and therefore not in the software center. Chromium is open source software and should be available in the software center. I can't explain why Chromium would be missing on one machine because it is categorized as provided by Ubuntu. Once Google Chrome has been installed the software source remains on the computer until removed.

---

### Post by Mike_Walsh on 2014-10-01
In all honesty, why would the repository of an operating system that is open-source provide proprietary, or 'closed-source' software? That's why Chromium is in the repos, and Chrome isn't. 

Anyway, Chromium (or the Chromium Project, to give it its full title) is where all the bleeding-edge development work for Chrome is carried out, so.....

I leave you to draw your own conclusions..!

Regards,

Mike.

---

### Post by Tom_Carr on 2014-10-01
But I have Chrome, not Chromium, installed on a 14.04 system set up a few months ago.  At one time it was available in the Software center.

---

### Post by Bucky Ball on 2014-10-01
Did you install via a PPA? Chrome is not in the Software Centre by default. Never has been. Chromium-browser is, as mentioned ... :-k

---

### Post by deadflowr on 2014-10-01
> **Mike_Walsh said:**
> In all honesty, why would the repository of an operating system that is open-source provide proprietary, or 'closed-source' software? 


To be fair, Ubuntu does provide means to install closed-source software.
The restricted and multiverse repositories are for that purpose.
That said, I think the means for chrome to be added would be up to google to see about adding chrome, et al
(note the google repo includes other packages beside chrome)

At this point I don't see google wanting to change the way it set up right now, because it would mean a loss of total control.
Right now, when chrome gets an update, google releases it and we get updates, quick and easy.
If those repos were under Ubuntu dev control, then those quick updates might need to take a moment for the ubuntu devs to vet them.
To google that is probably an unnecessary step, and time killer to get updates out timely.
Probably off and way wrong, but that's my thought on it anyway.

---

### Post by vasa1 on 2014-10-01
> **Mike_Walsh said:**
> In all honesty, why would the repository of an operating system that is open-source provide proprietary, or 'closed-source' software? That's why Chromium is in the repos, and Chrome isn't. ...
The Software center makes it easy to install other *proprietary, or 'closed-source' software* such as Microsoft fonts and the Adobe Flash player, both NPAPI and Pepper versions. I notice there's skype as well. I don't know whether that's Free Software or Open Source 

So why there isn't something to facilitate the installation of Google Chrome is beyond my understanding. Of course, I've never had a problem installing the browser via another browser and it maybe because it's so easy to install Google Chrome that there isn't an "installer" for it in the Software Center.

ninja'ed by df

---

### Post by deadflowr on 2014-10-02
There is an irony(?) to pepperflashplugin-nonfree, as the package actually downloads chrome from google, but only extracts the pepperflash plugin and installs it so that chromium can use it.
So I guess very technically, chrome is already in the repos.
lol

---

### Post by oldos2er on 2014-10-02
> **Mike_Walsh said:**
> In all honesty, why would the repository of an operating system that is open-source provide proprietary, or 'closed-source' software? 

That's what the restricted and multiverse repositories are for, FWIW.

> But I have Chrome, not Chromium, installed on a 14.04 system set up a  few months ago.  At one time it was available in the Software center.

No Google software has ever been included in the default repos because Google won't allow that (that's my understanding of it at least). However if you install Chrome from a downloaded *deb file, it automatically sets up its own repo ([http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/)) which then provides you with automatic updates, and naturally it will then show up in Software Center too.

---

### Post by Mike_Walsh on 2014-10-03
> **deadflowr said:**
> To be fair, Ubuntu does provide means to install closed-source software.
The restricted and multiverse repositories are for that purpose.
That said, I think the means for chrome to be added would be up to google to see about adding chrome, et al
(note the google repo includes other packages beside chrome)

At this point I don't see google wanting to change the way it set up right now, because it would mean a loss of total control.
Right now, when chrome gets an update, google releases it and we get updates, quick and easy.
If those repos were under Ubuntu dev control, then those quick updates might need to take a moment for the ubuntu devs to vet them.
To google that is probably an unnecessary step, and time killer to get updates out timely.
Probably off and way wrong, but that's my thought on it anyway.

Fair point, everybody..!

I was referring to the bog-standard setup, which, obviously, is the easiest way for new users to go about installing things.....since the Linux way of doing things is quite a shock to some newbies.

It's not really until you've got a few months 'under your belt' that you start playing around with ppas, and adding extra stuff. Unless, of course, you're like me; I was Googling, and surfing, and adding all sorts of things to my system as soon as I was sure that I wasn't going to break anything in the process. But then I **have** got 30 some-odd years of computing experience to my credit. In all honesty, having tried pretty much every O/S on the market at some point or another, you quickly realise that although they may differ greatly in appearance, and the way you operate them, under the hood they pretty much all work along standard lines.

I used XP for several years, but I've never got so attached to an O/S that I wouldn't consider migrating. As a consequence, I have a system that is mainly open-source, with a small amount of closed source apps; it works for me, and I don't feel at **all **guilty about it; I don't consider myself to be a 'purist', in the sense that I would only use open-source software.

But the current set-up works well, as you say; and it does give the individual a reasonable amount of control over how they add software to their system.

And vasa does have a point; it **is **incredibly easy to add chrome to your system. There again, as oldos2er points out, Google like to excercise tight control over what they will, and won't, permit.

I didn't know that about the pepperflash installation process, deadflowr!

Regards,

Mike.

---

