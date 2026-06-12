---
title: "Upgrade from Festy to Hardy: compiz dead"
date: 2008-04-26
forum: General Help
---

### Post by Nevermore on 2008-04-26
Hi everyone i upgraded just today from festy to hardy
First of all, the fglrx module was not correctly upgraded, so i manually hunt it, delete, and reinstall restricted drivers..
Then i got the infamous mesa problem, reinstalling libmesa did the trick
Then compiz refused to start, had to edit /usr/bin/compiz by setting the correct path..
still compiz refuses to load, checked again /usr/bin/compiz but my card is not blacklisted (radeon 9800 pro with fglrx)
I tried to start compiz via cli using the cheat SKIP_CHECKS="yes"
but it loops..

here is part of the loop:
```

Detected PCI ID for VGA: 01:00.0 0300: 1002:4e48 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:4e48 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Checking for Xgl: not present. 

```

How can i fix it??? is very annoying! btw compiz doesn't work of course..
Trying to enable from theme-manager gives back an error
and a nice xorg process that eats up 90% CPU..
then is needed to restart X to get back to normal..

too bad, i never had a smooth upgrade so far..

---

