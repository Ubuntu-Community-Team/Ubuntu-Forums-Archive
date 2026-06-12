---
title: "GTK+ Install Help"
date: 2007-07-06
forum: General Help
---

### Post by iSecks on 2007-07-06
Hey, recently i was trying to install Ophcrack, but it needed GTK+, so i got it and tried to install it, and i was missing stuff. i got the stuff i was missing, and installed it all. then i go back to install gtk and i get this error when i ./configure
```
Package libpng12 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libpng12.pc'
to the PKG_CONFIG_PATH environment variable
Package 'libpng12', required by 'cairo', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

and i cant figure out how to get it to see libpng [its there, i remember specifically installing it when i was installing cairo.

Any help would be greatly appreciated.
Thanks in advanced.

---

### Post by djchandler on 2007-07-06
> **iSecks said:**
> Hey, recently i was trying to install Ophcrack, but it needed GTK+, so i got it and tried to install it, and i was missing stuff. i got the stuff i was missing, and installed it all. then i go back to install gtk and i get this error when i ./configure
```
Package libpng12 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libpng12.pc'
to the PKG_CONFIG_PATH environment variable
Package 'libpng12', required by 'cairo', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BASE_DEPENDENCIES_CFLAGS
and BASE_DEPENDENCIES_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

and i cant figure out how to get it to see libpng [its there, i remember specifically installing it when i was installing cairo.

Any help would be greatly appreciated.
Thanks in advanced.

Has X been disabled by this? I would try re-installing Cairo if this was my problem, but I've never used it. It just seems to be a logical conclusion, as well as an easy fix. Then use synaptic to re-install gtk+ and let it resolve the dependencies.

Maybe at least I'll get another bean for this.

DJ

---

### Post by iSecks on 2007-07-06
hmm, i tried to install cairo again and i get another libpng error, but i see it in synaptic as installed.... 
```
checking for cairo's PNG backend... 
configure: WARNING: Could not find libpng in the pkg-config search path
checking whether cairo's PNG backend could be enabled... no
configure: error: requested PNG backend could not be enabled

```

---

### Post by djchandler on 2007-07-07
> **iSecks said:**
> hmm, i tried to install cairo again and i get another libpng error, but i see it in synaptic as installed.... 
```
checking for cairo's PNG backend... 
configure: WARNING: Could not find libpng in the pkg-config search path
checking whether cairo's PNG backend could be enabled... no
configure: error: requested PNG backend could not be enabled

```

So you are getting to the GUI. I am not sure how you check to see what window manager is running. Have you tried running the application this was necessary for?

D. J.

PS Are you trying to crack Windows passwords for IT support reasons?

---

### Post by BLTicklemonster on 2007-11-28
Shoot, I'm trying to get cairo because kiba dock suggests I have it, and I get the same error. Is there anything to do to fix this?

---

