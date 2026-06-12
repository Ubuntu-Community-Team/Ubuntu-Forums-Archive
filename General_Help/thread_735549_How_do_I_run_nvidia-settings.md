---
title: "How do I run nvidia-settings?"
date: 2008-03-25
forum: General Help
---

### Post by omidomid on 2008-03-25
When I try to run it, it says: 

```
~$ nvidia-settings
The program 'nvidia-settings' can be found in the following packages:
 * nvidia-glx
 * nvidia-settings
 * nvidia-glx-new
Ask your administrator to install one of them
bash: nvidia-settings: command not found

```

and when I try nvidia-glx or nvidia-glx-new, it says command not found.
I'm new to linux and I installed Ubuntu Gutsy like a few weeks ago. I'm trying to configure my graphics card options; what am I doing wrong?

---

### Post by LaRoza on 2008-03-25
> **omidomid said:**
> When I try to run it, it says: 

```
~$ nvidia-settings
The program 'nvidia-settings' can be found in the following packages:
 * nvidia-glx
 * nvidia-settings
 * nvidia-glx-new
Ask your administrator to install one of them
bash: nvidia-settings: command not found

```

and when I try nvidia-glx or nvidia-glx-new, it says command not found.
I'm new to linux and I installed Ubuntu Gutsy like a few weeks ago. I'm trying to configure my graphics card options; what am I doing wrong?

Install the package. It is saying that you don't have it, but it can be installed.

```

sudo aptitude install nvidia-settings

```

---

### Post by omidomid on 2008-03-25
Thanks, worked like a charm!

---

### Post by forrestcupp on 2008-03-25
if you installed nvidia-settings, you may have installed the wrong package.  Evidently, you didn't have the proprietary nvidia drivers installed.  What video card do you have?  If you have a fairly new card, you need nvidia-glx-new which includes nvidia-settings within the package.  It is incompatible with the nvidia-settings package.  So it's possible that the nvidia-settings that you installed isn't changing anything.

What video card do you have, and if you open System->Administration->Restricted Drivers Manager, does it say that your nvidia drivers are enabled?

---

### Post by dcstar on 2008-03-26
> **forrestcupp said:**
> if you installed nvidia-settings, you may have installed the wrong package..
........

If he had the new drivers installed, then the command would have worked, since it didn't work he obviously did not have these drivers installed.

---

### Post by omidomid on 2008-03-26
forrestcupp was definately correct. I have a 8400M GT (Sony vaio vgn-fz190 laptop) and I installed nvidia-settings, but once I rebooted, it wouldn't load my gdm. When I loaded gdm, it loaded the fail-safe Xorg and wouldn't detect my resolution/ card. Soooo, after spending all day today attempting to fix the problem, I finally just reinstalled ubuntu. Did learn a lot though from this experience.

and now I have nvidia-glx-new installed and it's working great! Don't know what was there before this whole thing, but doesn't matter now.

---

### Post by forrestcupp on 2008-03-26
> **dcstar said:**
> If he had the new drivers installed, then the command would have worked, since it didn't work he obviously did not have these drivers installed.

That was my point.  He should have installed nvidia-glx-new instead of nvidia-settings, which goes with the drivers that don't work with his card.

---

