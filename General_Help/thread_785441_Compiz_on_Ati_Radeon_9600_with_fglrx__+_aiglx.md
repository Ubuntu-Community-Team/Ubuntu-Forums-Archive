---
title: "Compiz on Ati Radeon 9600 with fglrx  + aiglx"
date: 2008-05-07
forum: General Help
---

### Post by lattmau on 2008-05-07
I'm having trouble getting compiz to work on the Ati Radeon 9600 card with fglrx driver + aiglx.  

I installed Ubuntu 8.04 and enabled proprietary drivers and rebooted.  When I try the desktop effects, it says "desktop effects could not be enabled". 

I thought with fglrx driver that comes w/ hardy, aiglx is incorporated and compiz would work out of the box.  What am I missing?

---

### Post by danwood76 on 2008-05-07
Open up the terminal and post the output of this command:
```

fglrxinfo

```

---

### Post by lattmau on 2008-05-07
output: 
> matthew@matthew-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9600/9700 Series
OpenGL version string: 2.1.7412 Release


---

