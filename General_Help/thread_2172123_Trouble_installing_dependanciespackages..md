---
title: "Trouble installing dependancies/packages."
date: 2013-09-03
forum: General Help
---

### Post by Karasawa7 on 2013-09-03
I need to Install the following dependencies: 

[LIST]
[*] [FONT=monospace][libtxc_dxtn]("https://www.archlinux.org/packages/?name=libtxc_dxtn")[/FONT] 
[*] [FONT=monospace][lib32-libtxc_dxtn]("https://www.archlinux.org/packages/?name=lib32-libtxc_dxtn")[/FONT] 


I assumed I could just do ```
sudo apt-get install libtxc_dxtn
```

However I get ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libtxc_dxtn

```


Am I doing something wrong? Or? 

I need to install these, because a game I want to play renders textures  black, and the two dependencies are said to remedy it. I use Ubuntu  12.04 
[/LIST]

---

### Post by kingsuk-d on 2013-09-03
I think the package you mentioned is not available in Ubuntu repo. I think its available from 3rd party ( xorg-edgers ) repository. 
You can check the link [http://www.ubuntuupdates.org/ppa/xorg-edgers?dist=precise](http://www.ubuntuupdates.org/ppa/xorg-edgers?dist=precise)

and install the PPA as mentioned in the link. Then try installing it as you did earlier.  I am not sure if it will resolve your problem

---

### Post by Karasawa7 on 2013-09-03
Installed the 3rd party thing no problem, but got the same thing as before.

I'm a little new to Ubuntu, which probably limits my capability to explain things. Thank you for the quick response though.

---

### Post by Karasawa7 on 2013-09-03
However, the package I need "libtxc_dxtn" is there, on the link you gave me
Huh..

---

### Post by Karasawa7 on 2013-09-03
The package was an umbrella, containing multiple (two, specifically) packages.
Opted to install each package in it separately, installed just fine. Let me see if it fixed my game issue. (even though this thread was initially about installing the packages themselves, which I've done. I'll mark this as solved)

---

### Post by oldos2er on 2013-09-03
You can use *apt-cache search <search terms>* to find the exact package name you need. I ran ```
apt-cache search libtxc dxtn
``` which produced ```
libtxc-dxtn-s2tc-dev - Development files for the S2TC library
libtxc-dxtn-s2tc0 - Texture compression library for Mesa
libtxc-dxtn-s2tc-bin - S2TC texture compression and conversion tools
``` Just FYI.

---

