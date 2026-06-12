---
title: "Help! no screen!"
date: 2007-12-22
forum: General Help
---

### Post by justinclark on 2007-12-22
Alright well another user suggested I use [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon") this tutorial to help install the correct drivers.  Well after making the changes to the xorgconfig file I now have no screen.  Upon turning it on I see the Dell screen, then the Ubuntu loading screen, then it just goes black...nothing.  So here I am at the public library very much regretting ever switching to Ubuntu.  Any suggestions (other than just buying a macbook:))?

---

### Post by torgrot on 2007-12-22
At the black screen try Ctl-Alt-F1..10 which I believe switches you to another terminal session then type to reconfigure your x-server.

```

dpkg-reconfigure xserver-xorg

```

torgrot

---

### Post by justinclark on 2007-12-22
Will that reconfigure the file or just bring me to it so I can reconfigure it?  Because I obviously dont know what Im doing.

---

### Post by torgrot on 2007-12-22
That will run through a text based script asking you for some parameters, i.e. keyboard language etc...  Most of them you can just accept the default for.  It will recreate and reconfigure your xserver.  I know from experience just like yours trying to get the ATI drivers loaded and wound up with all sorts of problems.

torgrot

---

### Post by justinclark on 2007-12-22
Ok, thanks a lot I will try that at home tonight.

---

