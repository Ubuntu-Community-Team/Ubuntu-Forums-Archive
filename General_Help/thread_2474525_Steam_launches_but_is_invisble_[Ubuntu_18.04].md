---
title: "Steam launches but is invisble [Ubuntu 18.04]"
date: 2022-05-01
forum: General Help
---

### Post by AdHoc92 on 2022-05-01
[May also be worth pointing out this is Gallium OS, based on 18.04]

Everything else displays fine, but Steam is just straight up  invisible. I can tell it's on my desktop because it's on my taskbar and  the invisible window gets in the way when clicking on my desktop. I've tried uninstalling and reinstalling, purging everything steam  related, then reinstalling. Installing from the software-center, from  terminal, as a .deb, as a flatpak. Always the same problem.
 
In the console, some things do stand out:
 

It says "steam-libs-amd64:amd64" and "steam-libs-i386:i386" are not available.

  
[If I try to apt-get install the first one, says it can't find that  package. For the second, it says "not available but is referenced by  another package." ]

  
It also says "Xlib:  extension "NV-GLX" missing on display ":0.0"."

  
But after googling, I can't seem to grasp what that indicates. This is driving me nuts.

---

