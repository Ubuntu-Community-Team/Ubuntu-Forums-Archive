---
title: "Ubuntu 8.04 Fonts"
date: 2008-05-01
forum: General Help
---

### Post by rodgerdb on 2008-05-01
No doubt some will hate it, some will love it, just figure I'd share how I setup my Hardy Heron fonts. Outside of this, most everything I just leave as default.

sudo dpkg-reconfigure fontconfig-config

  Font tuning method for screen: Autohinter
  Enable subpixel rendering for screen: Always
  Enable bitmapped fonts by default? No

sudo dpkg-reconfigure fontconfig

sudo ln -sf /etc/fonts/conf.avail/10-autohint.conf /etc/fonts/conf.d/
sudo rm /etc/fonts/conf.d/53-monospace-lcd-filter.conf

System > Preferences > Appearance > Fonts (tab) > Details (button)

  Resolution: 96 DPI
  Smoothing: Subpixel (LCDs)
  Hinting: Slight
  Subpixel Order: RGB

Now logout and the settings should take effect.

---

### Post by rodgerdb on 2008-08-09
Just wanting to throw out an update on my thread here a few months later. Not sure what changed but I no longer use the full changes listed here anymore. I only use the last steps now:

System > Preferences > Appearance > Fonts (tab) > Details (button)

Resolution: 96 DPI
Smoothing: Subpixel (LCDs)
Hinting: Slight
Subpixel Order: RGB

Works great, looks great.

---

### Post by DaymItzJack on 2008-08-10
It's different on every setup/monitor, that's why there is other options to choose from.

---

### Post by rodgerdb on 2008-08-10
So very true. This particular setup I suggest will help with fonts like Inconsolata (specifically the 'slight' hinting).

You make an excellent point though, alot of it comes down to the combination used. Come to think of it, I do have an NVidia now as opposed to an ATI card back then.

---

### Post by Midahed on 2008-08-16
> **rodgerdb said:**
> 

System > Preferences > Appearance > Fonts (tab) > Details (button)

Resolution: 96 DPI
Smoothing: Subpixel (LCDs)
Hinting: Slight
Subpixel Order: RGB

Works great, looks great.
Thanks for that post.

That change, plus the installation of the msttcorefonts package has made my otherwise standard Ubuntu 8.04 Hardy installation look much, much better.

---

### Post by swathipk on 2011-06-27
Thanks it worked.

---

