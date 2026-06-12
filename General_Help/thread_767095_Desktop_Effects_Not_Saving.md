---
title: "Desktop Effects Not Saving"
date: 2008-04-25
forum: General Help
---

### Post by feedmecereal on 2008-04-25
Whenever I change the settings in Visual Effects, the option of "Extra" is not saved. Each time I go into the box, none of the three options are checked. I do see some effects but they change to the default settings every time I select "Extra." I have noticed a few minor problems after a little while of usage after I customize the settings and before I go back to the Visual Effects preferences.

I just upgraded from 7.10 to 8.04 yesterday.

---

### Post by djrobthaman on 2008-04-25
I'm having the same problem too, but I think it's a mixture between me having compiz 7 (from a third party) installed as well as the upgrade process still not working 100%.

I'm sure there's a way to fix it, but what I'm gonna do is do a clean install of hardy.  That always seems to get a better result than the upgrade.  I have to say though, the upgrade process and end result is much better than previously.

---

### Post by Zorael on 2008-04-25
Upgrades are always iffy. I suggest you completely remove all your compiz packages, disable any foreign repositories, and then reinstall them.

```
$ sudo apt-get autoremove --purge compiz* libcompiz* emerald* libemerald* libdeco*
```

---

### Post by Continuum on 2008-04-25
I have the same problem as feedmecereal and I installed yesterday from a clean install of hardy (among other problems with compiz due to the blacklisting of ATI cards).
Also, once I install compizconfig-settings-manager, the button beside the Extra Visual Effects option does not show up anymore.

---

### Post by Zorael on 2008-04-25
> **Continuum said:**
> Also, once I install compizconfig-settings-manager, the button beside the Extra Visual Effects option does not show up anymore.

Well, with CCSM installed there's little point in using the Desktop Effects thingy. :>

(Run ccsm from a run box, or a terminal.)

---

### Post by feedmecereal on 2008-04-25
I just went into Synaptic and reinstalled the compiz package and the option stays selected now. Other problems that I was having seem to be fixed too. I'll post again to this thread if I start having any problems again.

---

### Post by feedmecereal on 2008-04-26
I'm still having a few minor issues even after I went into Synaptic and removed all the compiz packages, restarted, and then reinstalled them. None of the options in Visual Effects are checked.

---

