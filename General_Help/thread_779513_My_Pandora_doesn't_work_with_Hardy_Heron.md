---
title: "My Pandora doesn't work with Hardy Heron"
date: 2008-05-02
forum: General Help
---

### Post by sirius56 on 2008-05-02
Pandora always worked well for me with previous versions of Ubuntu, but
when I upgraded to Hardy Heron, Pandora will not work--and this is on
two different 32-bit systems.   Otherwise, Hardy Heron is flawless for me.

When Pandora loads, I get a large, right pointing arrow with a ring
around it, on my display.  When I click on the arrow, I go to the
"Please wait, Pandora is loading"  page.  Then it just hangs there.  

If I test my Flash Player at  [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)
the test is satisfactory.  So no problem here.

I don't have any firewalls or popup blockers.

Pandora is important to me and I can't find any other reports of the problem.   Possibly because Hardy Heron is new.  

Please let me know if you have any suggestions.

Thank you.


[www.pandora.com](www.pandora.com)

---

### Post by briansmith on 2008-05-03
SOLVED SOLVED SOLVED


I had this same problem... particularly with pandora too!  Luckily it
 is
now SOLVED for me, maybe i can help anyone else with this problem....

It seems to be the flash plug-in that I allowed Firefox to install for
me... I think it was called gnash or something....

1. Open Synaptic...
2. Sear "flash"...
3. Find the few entries with the words gnash in the title, and
 completely remove them...  (gnash, gnash-common, gnash-cyngal, gnash-tools)
4. Wa-laa!
5. If you are still having trouble install, "flashplugin-nonfree"

-- 
Flash stops working in firefox on ubuntu 8.04 
[https://bugs.launchpad.net/bugs/214722](https://bugs.launchpad.net/bugs/214722)

I have been strugling with this for two days and i see other people are to... I am so excited to have finally come up with a solution myself, that i just posted this solution in three places!

---

### Post by sirius56 on 2008-05-03
Brian,  Thank you for the suggestion, but I still have the problem.

I searched for "gnash" but only found Gnash SWF Viewer, but it was unchecked.

As to plugins, I have Shockwave Flash 9.0 r100  installed.

Please let me know if you have any other suggestions.

Thank you.

Richard

---

### Post by jimv on 2008-05-03
Do you have any extensions installed?  (Not plugins)
Try disabling them.

I'm using Hardy and Pandora just popped up for me.  (Kinda cool...never used it before.)

---

### Post by sirius56 on 2008-05-04
> **jimv said:**
> Do you have any extensions installed?  (Not plugins)
Try disabling them.

I'm using Hardy and Pandora just popped up for me.  (Kinda cool...never used it before.)
I found two Installed Extensions:
Javascript Option  1.2.6
Ubuntu Firefox Modification 0.5

I disabled both of those and restarted.  Pandora still did not work.

I reinstalled the two extensions.

Please tell me what your Installed Extensions are.
Thank you.

---

### Post by jimv on 2008-05-04
Are you behind a proxy that filters internet access?

---

### Post by sirius56 on 2008-05-04
> **jimv said:**
> Are you behind a proxy that filters internet access?
I know of no proxy servers or proxy gateways that could be blocking HTTP.

Please note that my Flash Player works with 

[http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

so it should work with Pandora.  I'm surprised that there haven't been more reports of this problem because I run a very plain vanilla Hardy Heron.  It could be that only a small number of Pandora users run Linux.


My Pandora problem only arose when I installed Hardy Heron.

---

### Post by sirius56 on 2008-05-04
Not sure if this matters, but running Firefox in safe mode makes no difference.

Terminal  >>   firefox  -safe-mode

---

### Post by jimv on 2008-05-04
Hrmmm.  There is a newer build of Flash Player available.  You have .100, I'm using .124.

Close Firefox and try this in the terminal:

sudo apt-get remove --purge flashplayer-nonfree
sudo apt-get install flashplayer-nonfree

And if that doesn't work, I'd try creating a new user in Ubuntu, logging in as that user, and testing Pandora.  Perhaps something in your profile got borked during the upgrade process.

---

### Post by sirius56 on 2008-05-13
I noticed that my youtube.com also wasn't working.
I decided to reload

swfdec-0.6-90
swfdec-gnome
swfdec-mozilla

and both Pandora and youtube started to work.

I can't imagine what might have corrupted these files, but reloading solved my problems.

Thank you for your help.

Case closed.

---

