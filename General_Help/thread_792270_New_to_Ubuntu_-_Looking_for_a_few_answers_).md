---
title: "New to Ubuntu - Looking for a few answers :)"
date: 2008-05-12
forum: General Help
---

### Post by JBuRRkE on 2008-05-12
Hi everyone! First post here and I'm hoping to get a few answers :D

So yesterday I installed Ubuntu on my external hdd (160 gb), hoping I could have both Windows & Ubuntu installed in such a way that i simply remove the hdd and reboot to boot up windows.. Well it didnt exactly work like that =/.. When i remove the hdd and attempt to boot from my internal hdd i get an Ubuntu error, which leads me to believe that I've somehow accidentally formatted my internal and installed Ubuntu on that.. Anyways, any ideas on this? 

My next question is about my tablet.. I'm a digital painter, and the main reason i wanted to keep windows was to run PS without the trouble & bug/laggyness of Wine (or whatever).. I've decided to give gimp a shot, but it's a bit impossible without my tablet ><

I've done a bit of research, but the terminal confuses the crap out of me.. So I'm wondering if any of you could help me out here.. My tablet is recognized when I plug it in, but the mouse doesnt move and it makes me go back a page on Firefox when i click.. Soo i dunno :confused:

My tablet : >[LINK]("http://www.geniusnet.com/geniusOnline/online.portal?_nfpb=true&productPortlet_actionOverride=%2Fportlets%2FproductArea%2Fcategory%2FqueryPro&_windowLabel=productPortlet&productPortletproductId=341204&_pageLabel=productPage&test=portlet-action")<

Any help is much appreciated ^^

---

### Post by quibbler on 2008-05-13
> **JBuRRkE said:**
> Hi everyone! First post here and I'm hoping to get a few answers :D

So yesterday I installed Ubuntu on my external hdd (160 gb), hoping I could have both Windows & Ubuntu installed in such a way that i simply remove the hdd and reboot to boot up windows.. Well it didnt exactly work like that =/.. When i remove the hdd and attempt to boot from my internal hdd i get an Ubuntu error, which leads me to believe that I've somehow accidentally formatted my internal and installed Ubuntu on that.. Anyways, any ideas on this? 

My next question is about my tablet.. I'm a digital painter, and the main reason i wanted to keep windows was to run PS without the trouble & bug/laggyness of Wine (or whatever).. I've decided to give gimp a shot, but it's a bit impossible without my tablet ><

I've done a bit of research, but the terminal confuses the crap out of me.. So I'm wondering if any of you could help me out here.. My tablet is recognized when I plug it in, but the mouse doesnt move and it makes me go back a page on Firefox when i click.. Soo i dunno :confused:

My tablet : >[LINK]("http://www.geniusnet.com/geniusOnline/online.portal?_nfpb=true&productPortlet_actionOverride=%2Fportlets%2FproductArea%2Fcategory%2FqueryPro&_windowLabel=productPortlet&productPortletproductId=341204&_pageLabel=productPage&test=portlet-action")<

Any help is much appreciated ^^

keep the external drive connected, then boot
you should get a grub menu where you can choose to
open Ubuntu or Windowns.
use the arrow keys to choose.

Regards quibbler

---

### Post by JBuRRkE on 2008-05-14
> **quibbler said:**
> keep the external drive connected, then boot
you should get a grub menu where you can choose to
open Ubuntu or Windowns.
use the arrow keys to choose.

Regards quibbler

thanks for the reply :D

when i get to that menu, there are many different os's to choose from.. 
there are like four different linux operating systems, and two 
vistas, which both say something about longhorn.. or something

when i click one of the vistas, they load up to some lenovo (my computer model) windows recovery system.. and i dont want to do anything until i know for sure both my os's will be safe =/

you have any idea what this is, or what to do?

---

### Post by talz13 on 2008-05-14
> **JBuRRkE said:**
> thanks for the reply :D

when i get to that menu, there are many different os's to choose from.. 
there are like four different linux operating systems, and two 
vistas, which both say something about longhorn.. or something

when i click one of the vistas, they load up to some lenovo (my computer model) windows recovery system.. and i dont want to do anything until i know for sure both my os's will be safe =/

you have any idea what this is, or what to do?

That is probably a bootable recovery partition that you picked.  Remember which one you picked, then pick the other one next boot and see if it boots your regular vista.

The 4 linux OSes are maybe the memtest, recovery mode, and normal boot?

If you boot into ubuntu, you should be able to edit your menu file at:

/boot/grub/menu.lst

Then you can change the "title" attributes at the end of the file to be something more readable to you (like "Vista Recovery").

---

### Post by drs305 on 2008-05-14
You can also modify some entries in the grub menu list if you have startupmanager installed. You access it via system, administration, startup-manager. You can change how many seconds to show the screen before automatically selecting an option, how many versions of ubuntu to display (as new kernels are released, they are all shown unless you change it),  and whether or not you want to see the entries for memtest and recovery mode (suggest you keep recovery mode option). These choices are under the 'boot options' and 'advanced' tabs.

If you don't see startup-manager, you can install it with:
```
sudo aptitude install startupmanager
```

---

