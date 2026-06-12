---
title: "Can not Enable Visual Effects"
date: 2008-04-13
forum: General Help
---

### Post by tiimage on 2008-04-13
I am brand new to ubuntu. I'm trying to enable the visual effects and I can not every time I get an error message saying "can not enable visual effects". How do I fix this. I have 8.04 beta.

Please help!

Thanks...

Tim

---

### Post by sekinto on 2008-04-13
Well I've noticed that installing "xserver-xgl" fixes a lot of problems like these.

And if you want the latest and greatest effects I would recomend installing and configuring the latest Compiz-Fusion if your system can handle it.

---

### Post by tiimage on 2008-04-13
xserver-xgl - I searched for that in add/remove programs and did not find it. How do I download that?

---

### Post by sekinto on 2008-04-13
system>administration>synaptic package manager

Synaptic doesn't hide things from you like Add/Remove programs, and is a little more advanced.

---

### Post by overdrank on 2008-04-13
> **tiimage said:**
> xserver-xgl - I searched for that in add/remove programs and did not find it. How do I download that?

HI and welcome, what is the model of the graphics card? To find this you can use the command```
 lspci
``` in the terminal located under applications, accessories. Look for VGA

---

### Post by tiimage on 2008-04-13
nVidia Corporation GeForce 8400M GS (rev a1)

---

### Post by tiimage on 2008-04-13
I downloaded and installed xserver-xgl. Logged out and back in. But still same problem

---

### Post by sekinto on 2008-04-13
Are you using the Nvidia drivers?

---

### Post by overdrank on 2008-04-13
> **tiimage said:**
> nVidia Corporation GeForce 8400M GS (rev a1)

Hi and I may suggest Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by tiimage on 2008-04-13
I believe so. I downloaded the latest nvidia drivers through add programs

---

### Post by sekinto on 2008-04-13
Well if you used the restricted drivers manager to install it you should already have it configured for you, but if you installed it via Synaptic, Add/Remove, Aptitude, or Apt then you will have to manually configure your xorg.conf file I think.

---

### Post by daniel7860 on 2008-04-14
i have a dell inspiron 9300.
i used ubuntu 7.10 and all the advanced effects worked perfect.
now i updated to 8.04 beta and they dont work and it says i cant enable them.
WHY?

---

### Post by daniel7860 on 2008-04-14
if i install the restricted driver and enable the effects my screen turns white and the only thing i can do is move my mouse

---

### Post by VipeR_11 on 2008-04-14
i have the same problem but i fed up trying to fix it.

unfortunately for me i got ATi graphics card i have run the tests and my card support effects and everything but can't enable them.
I thing was because of the bad ATi drivers.

At the moment i have stopped using ubuntu and waiting for the next version.
As i was trying to fix the problem I created one more problem...! My Screen runs in 60Hz mode only and the signal after some changes and a restart runs at 120Hz!!! So, at the moment i can't see anyhting through my screen :[

I was trying to fix those problems for a month when the 7.10 version 1st came out, i fed up and returned to windowsXP :-[


Anybody knows if the new version will fix the problem with the 60Hz sychronazation?

Please make the new version simplier for the new linux users like me :-[

Any i deas on how to install properly the ATi drivers? (so i can have effects on too)
And any help  how to fix the blanc screen problem? I mean help on how to make ubuntu send 60hz signal so I can see through my screen, cause now ubuntu are running but I haven't got signal on my monitor to do anything.

Edit:
I forgot to say that my card is ATI X1650 Pro

I know there are many threads here about installing drivers i tried everything (everything was mentioned here until january)

Anybody know if there is a driver for my card? cause in the manager says that ATi drivers are for series X1600,X1800 etc but not for the newer models end with 50 like mines X1650

---

### Post by daniel7860 on 2008-04-14
yeah....i am really tired of looking for it too now...I really hope when the non-beta version comess out i will be able to use effects.........10 more days......[-o<

---

### Post by VipeR_11 on 2008-04-15
> **daniel7860 said:**
> yeah....i am really tired of looking for it too now...I really hope when the non-beta version comess out i will be able to use effects.........10 more days......[-o<


I was tired too but i gave it yesterday a last go. I install again ubuntu but this time I used envy (it wasn't out when last time tried to fix the problem). The result?
Everything was looking great it dowload and install the right driver for me but on reboot i lost video signal...!

So i am where I was before :-[

---

### Post by koer9911 on 2008-05-07
> **VipeR_11 said:**
> I was tired too but i gave it yesterday a last go. I install again ubuntu but this time I used envy (it wasn't out when last time tried to fix the problem). The result?
Everything was looking great it dowload and install the right driver for me but on reboot i lost video signal...!

So i am where I was before :-[

I had same problem i installed wrong video driver and at reboot it didn't go to loging screen. But i went to terminal... ctrl+alt f1 then i loged in.. wrote: cd /etc/gdm
     then:  sudo ./failsafeXServer 
     and i changed my video settings and i got it working...
also easyer is: sudo dpkg-reconfigure xserver-xorg

---

