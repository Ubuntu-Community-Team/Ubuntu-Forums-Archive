---
title: "ati + xgl = some problems..."
date: 2007-05-07
forum: General Help
---

### Post by FA22RaptorF22 on 2007-05-07
Two problems:

ok.  Im running:  AMD 64 cpu, ATi Xpress 200m gpu, Ubuntu Feisty, Xgl, and compiz/beryl.
Machine= hp zv6170us lappy...

1.
I have just done another clean install with the fglrx driver, xgl and beryl.  All that works fine....but say when i run vmware, i get nothing in the guest window unless i log into just a plain gnome session.  I really need to run vmware in the xgl enviroment.  Any suggestions?  Also the many bugs in xgl such as the black/white pixelated startup screen, cannot log out, etc...really bug me.  Any help with these would be great. 

2.
I can only seem to install the fglrx drivers.  If i try to follow many guides to install ati's driver, i only get mesa3d out of the fglrxinfo command.  I heard that everything works better under ati's driver from their site opposed to the fglrx one.  What do you think?  I know i should just get nvidia and use aiglx...but any help would be appreciated, thanks.

---

### Post by Tenchi on 2007-05-09
I had the same problem, every time I tried to check my version of FGRLX I kept getting mesa driver information.
When I went to my blacklist the only thing in there was .. you guessed it FGRLX, you have to comment out or delete it in the blacklist for it to work.

Hope this helps

---

### Post by FA22RaptorF22 on 2007-05-10
so that will fix me installing ati's driver package?  I mean i can use the restricted driver manager fglrx driver perfectly, but that fixes it the ati way?  And that will fix my video problems as well?

thanks.

---

### Post by RavanH on 2007-05-11
You might find some answers here (second methode): [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

But I have to ask you: you have compiz working? with desktop-effects like shade and the cube?!? However did you do that??? But with mesa and not fgrlx, is that right?

I've got Feisty AMD64 on a laptop with ATI Radeon Xpress 200M and never got any desktop-effects working :( so REEEEALY intrested in how you did get that part working for you...

EDIT:
Oh, and by the way, would you be interested in signing the online petition for better ATI/AMD Radeon XPRESS 200M Linux Drivers on [http://www.petitiononline.com/x200MLin/petition.html](http://www.petitiononline.com/x200MLin/petition.html) ?

---

### Post by FA22RaptorF22 on 2007-05-12
ok.  To get beryl/compiz working in feisty on that card, i installed the proprietary restricted fglrx drivers, and installed xgl.  Then logging into an xgl session i installed the desktop effects.

Now, that works....but with those common xgl errors.  Now when i install the drivers with the exact proceedure you specified, i can only get mesa drivers....i just dont understand it.\

And i will sign that...

thanks for the help...

---

### Post by RavanH on 2007-05-12
Since my previous post, I found that the proprietary ATI drivers are not made for X.org 7.2 which comes with Feisty. So you might consider downgrading X.org to 7.1 as described on [http://ubuntuforums.org/showthread.php?t=432554](http://ubuntuforums.org/showthread.php?t=432554) (but using the latest drivers, not the legacy one!)

I followed that path and found that it indeed works a bit better now... Suspend works again and I'm sure that with some effort, Hibernation will be up-to-par soon :) Also, the ATI Catalist Control Center is active now. But still no desktop effects. 

Had to re-install the xorg-synaptic driver, though... Mouse cursor was all over the place ;)

---

### Post by FA22RaptorF22 on 2007-05-13
Well, desktop effects / beryl work perfectly in xgl under the restricted drivers.  No other drivers seem to work.  Let me know if you figure anything else out.

---

