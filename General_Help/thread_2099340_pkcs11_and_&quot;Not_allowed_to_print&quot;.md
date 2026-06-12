---
title: "pkcs11 and &quot;Not allowed to print&quot;"
date: 2012-12-29
forum: General Help
---

### Post by manselton on 2012-12-29
Hi

I'm not sure how I messed up what or even where to rightly ask for help so I am beginning with the General Forum. If I try to print from any application whatsoever, it never reaches the printer. Cups is configured correctly on the localhost:631 interface and shows the printer as idle. If I do

$ lpr -h 

I get 
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-dz2U37/pkcs11: No such file or directory
lpr: Not allowed to print.

I cannot even print as root. I am running Precise under an original Mint13 installation but now with the Openbox desktop.

Thanks in advance for any suggestions
Mo

---

### Post by dino99 on 2012-12-29
[https://help.ubuntu.com/community/Printers](https://help.ubuntu.com/community/Printers)
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)

---

### Post by manselton on 2012-12-29
Thanks for the links Dino99.

I still don't understand but I did 

sudo aptitude reinstall cups
sudo firefox [http://localhost:631/admin](http://localhost:631/admin)

and reinstalled the printer and it all works now.

---

