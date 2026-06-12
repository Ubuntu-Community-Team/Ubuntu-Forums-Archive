---
title: "This one is killing me: CUP-pdf and Firefox (Feisty and v1.2.0 CUPS)"
date: 2007-07-27
forum: General Help
---

### Post by r_l on 2007-07-27
I tried to install Cup-pdf so I can print from Firefox.  According to previous instructions available on the web, I need to somehow modify the config file so it does not run as owner.  Just as what the documentation says:

"CUPS-PDF requires root privileges since it has to modify file ownerships. In recent distributions the "RunAsUser" option in cupsd.conf is set to "Yes" which removes these privileges. Please make sure to set "RunAsUser No" if you want to use CUPS-PDF.


However, it seems that I need to to something different for Feisty and the new version of CUP as described [here]("http://www.physik.uni-wuerzburg.de/~vrbehr/cups-pdf/documentation.shtml")    


*** Starting with version 1.2.0 CUPS implements the "RunAsOption" no longer. In order to ensure CUPS-PDF is running with the required root privileges you have to make 'root' the owner of the cups-pdf backend and set the file permissions of the backend to 0700 (root only)."

Can anyone tell me step by step exactly how to set this scary-sounding "0700 privileges" thing?

Thanks in advance

RL

(This is REALLY frustrating.  The pdf-printing capacity is so basic and should be installed by default for Firefox in gnome, how hard would it be! :(  )

---

