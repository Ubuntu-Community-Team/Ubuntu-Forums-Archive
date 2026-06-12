---
title: "Visual effects"
date: 2008-04-05
forum: General Help
---

### Post by Voorhees1979 on 2008-04-05
Hi there

When I first installed Ubuntu I was using the graphics driver that came with the newest 7.10 version and I could enable the Extra effects. I thought I would be smart and follow the "How to install ATI driver" from this site. After I installed those drivers I can no longer use the extra effects or the normal effects im stuck on the low effects. The card in question is an ATI 9200. It worked perfect before I decided to install the ATI drivers, is there away to get the driver back that was installed when Ubuntu first ran?

I would just reinstall, but after getting the system running everything I need, which was hard for a noob like me, I dont really want to reinstall. Its setup perfect apart from the graphics side.

Many thanks and thanks for any replies

Voorhees

---

### Post by domace on 2008-04-05
What guide did you use to install the driver, please give me the url?

---

### Post by Voorhees1979 on 2008-04-05
Hi

Thanks for the reply it was from here:
[http://ubuntuforums.org/showthread.php?t=515573](http://ubuntuforums.org/showthread.php?t=515573)

Im guessing my card wasnt supported in that guide, but when I first did the leap from windows to linux I thought it was a good idea.

Apart from that Ubuntu has been the greatest system I have ever used.

---

### Post by domace on 2008-04-05
I see you...have to remove the drivers you installed(you know how to right? and re-enable your onboard video card and use that to reinstall the video card agin, you dow know what envy is right?), hold on did you say that your video card was working before

---

### Post by domace on 2008-04-05
are you using a separate video card then from the one your pc came with?

---

### Post by twright on 2008-04-05
envy can automatically install the newest ati drivers for you:)

---

### Post by Voorhees1979 on 2008-04-05
Its not an onboard card, it was working perfect before i tried to install the ATI drivers. i have no idea how to get rid of them and go back to the Ubuntu drivers :(

Thanks for any help

---

### Post by domace on 2008-04-05
ya  just remove the drivers use the video card your pc came with still leaving the pci one connected and install envy, you will have to change the computers default video device back i assume you know that, I learned this the hard way...3 Ubuntu re installations in 1 day

---

### Post by twright on 2008-04-05
download envy from [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) and select 'uninstall ati drivers', that should do the trick :)

---

### Post by Voorhees1979 on 2008-04-05
Hi again

I ran with envy -t

uninstalled ati drivers, but am still unable to run enhanced effects :(

Wish I never chose to install those ATI drivers now, was fine until then

---

### Post by mrmiserable on 2008-04-05
a better guide is this 

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

also i think to reinstall original configuration 

open terminal and

sudo dpkg-reconfigure -phigh xserver-xorg

this should set it up like your first setup was

hope this helps

edit dont forget to reboot

---

### Post by domace on 2008-04-05
if you installed the ati driver and its running fine maybe it has to be configured with compiz, i recently fixed my driver too, have patience for ubuntu and it will for you...trust me
this is the best os if you have spare time and patience

---

