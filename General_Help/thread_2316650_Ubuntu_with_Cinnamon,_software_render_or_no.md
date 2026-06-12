---
title: "Ubuntu with Cinnamon, software render or no?"
date: 2016-03-09
forum: General Help
---

### Post by Evil Wayz on 2016-03-09
Two questions:  I hate Unity.  So I was using GNome FLashback Metacity for awhile.  Then I found out you can use the Cinnamon desktop with Ubuntu.  Login gives me two options, Cinnamon and Cinnamon (SOftware rendering.)  Which should I choose?  I run Ubuntu 14.04.4 on a computer with a pentium D dual core 3.4 ghz cpu with 8gb of ram. 

THe other question is all my theme settings carried over except my icon settings.  For whatever reason it defaults to mint icons.  The package they came with contained two icon themes, Sanguine and REvenge.  REvenge works in both Cinnamon and Gnome Flashback, but sanguine only work sin GNome for some rason.  IS there a way to force the computer to recognize it using the settings panel, or do I have to individually ad a custom Icon to each action .

---

### Post by mastablasta on 2016-03-10
> **Evil Wayz said:**
> Two questions:  I hate Unity.  So I was using GNome FLashback Metacity for awhile.  Then I found out you can use the Cinnamon desktop with Ubuntu.  Login gives me two options, Cinnamon and Cinnamon (SOftware rendering.)  Which should I choose?  I run Ubuntu 14.04.4 on a computer with a pentium D dual core 3.4 ghz cpu with 8gb of ram. 
.
depends on the GPU really. if you have a descent one then the choice is yours. if you have one that has hardware 3D acceleration partially supported or without support, then use software rendering option.

I don't know about icons. Cinnamon was created by Mint, so this is probably the reason their foot print is seen.

also just use one desktop - keeps it simple and there are less issues or conflicts between them.

---

### Post by Evil Wayz on 2016-03-10
I have an NVidia GeForce 9400 GT with 1gb of memory.  

Should I uninstall the other desktops or just quit flipping between them?

---

### Post by buzzingrobot on 2016-03-10
I'd think I'd avoid software rendering. It's not intended for 2D.  On Mint Cinnamon here, software rendering is very degraded and low resolution, with a large notice telling you to stop using software rendering.

MATE and Xfce work and look per usual without compositing turned on.  Those might be options if Cinnamon doesn't work out.

Out of the box, Mint Cinnamon uses Mint's icons, not Sanguine or Revenge. For system-wide use, icons should be in /usr/share/icons.  Cinnamon's settings panel should pick them up.

Themes for 14.04 should be OK, since they are usually GTK3-version specific these days, and subsequent Ubuntu releases have used later versions.

---

### Post by Evil Wayz on 2016-03-10
It seems faster.  Might be my imagination. 

For whatever reason both those icon sets are in the folder but Cinnamon is only detecting one.

---

