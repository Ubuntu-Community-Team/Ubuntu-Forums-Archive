---
title: "Vendor Driver Or Restricted Driver"
date: 2007-10-26
forum: General Help
---

### Post by miteshanand1729 on 2007-10-26
I install Gusty.I have ATI Radeon Xpress 200 card.Which is better Vendor driver from Ati which i already download or enable Restricted driver of Ubuntu.I want to use compiz.

---

### Post by Sunforge on 2007-10-26
Your ATI card should work if you're on Feisty or Gutsy you should be able to work with the restricted driver set. I should point out that my main PC is using an older NVIDIA card so I'm no expert on ATI.

You can also try the ENVY scripts which a lot of people round here use, if you want to go for the vendor set:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by miteshanand1729 on 2007-10-26
If i install both then will it creat problem..??????

---

### Post by Sunforge on 2007-10-26
I'd think that the best approach would be to try either the Envy set or the restricted set. I'm no expert on ATI, although I have tried the ubuntu restricted ATI drivers on Gutsy with an old Radeon 9600 to no ill effect. 

One thing I would recommend is that you backup your xorg.conf file so that you can swap it back in should things go awry:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.back

---

