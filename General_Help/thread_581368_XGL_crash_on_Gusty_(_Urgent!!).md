---
title: "XGL crash on Gusty ( Urgent!!)"
date: 2007-10-19
forum: General Help
---

### Post by Meursault_ on 2007-10-19
I've upgraded to gutsy today from 7.04.  Everything was fine, but i wanted to try compiz fusion, and installed xserver-xgl since I have an Ati X600 . Before that, I installed the latest fglrx driver from restricted drivers section. When I started xgl session, everything was so slow, like a slideshow. Then I looked there and learned ati drivers aren't supporting XGL yet. So i uninstalled the fglrx driver and the other driver i installed with envy before upgrading to 7.10 . Now, when i try to open Ubuntu, it gives me an error "Your x driver is not configured correctly " or something like that. Since I can't open it, I can't make the disable file needed to prevent X from opening. I can't connect the internet and do upgrades from the recovery too. What should I do ?

---

### Post by Meursault_ on 2007-10-19
When I choose to see the debug information, it gives an output like that :
************************************************
/etc/gdm/failsafexserver:line 49 Too many arguments
Could not retrieve EDID because get-edid is not installed

************************************************

I think i really messed up with the configuration .  I believe I'm going to download the 7.10 CD and make a clean install if I couldn't find help from here

---

### Post by matigol on 2007-10-19
> **Meursault_ said:**
>  I believe I'm going to download the 7.10 CD and make a clean install if I couldn't find help from here

I think it's the best solution.

Yet, haven"t you a backup of your xorg.conf, it's recommanded to make this before play with...  :)

Good luck !

;)

---

### Post by Meursault_ on 2007-10-19
Interesting thing is , I haven't changed xorg.conf manually despite the composite extension section ( I enabled it). thanks anyway ..

---

### Post by Meursault_ on 2007-10-19
I solved my problem, but xgl runs very slow on every condition and when using aiglx, i get an error like "Couldn't enable window effects" or something like that. (Important thing is error message says nothing about composite extension" )

---

### Post by demauk on 2007-10-19
Hi, Meursault,

I got the same error message from my upgrade. Did you fix it without doing a clean install? What did you do?

Thanks!

---

### Post by strabes on 2007-10-19
fglrx is ATI's pathetic linux driver. It doesn't support aiglx. XGL is really unstable and slow. In my opinion it's not even worth using. ATI is supposedly releasing acceptable drivers in October, but actions speak louder than words.

---

### Post by demauk on 2007-10-19
I forgot to mention I have an nVidia GeForce FX 5700, and was previously using the restricted nvidia drivers.

---

### Post by Jolly-Swagman on 2007-10-19
> **strabes said:**
> fglrx is ATI's pathetic linux driver. It doesn't support aiglx. XGL is really unstable and slow. In my opinion it's not even worth using. ATI is supposedly releasing acceptable drivers in October, but actions speak louder than words.


Yes totally agree ATI has never got it right, and even in Windoze, they are crappy too, and worst of all they dont really care either, after many problems with the wife's computer, and ATI lack of support.

After they get your money they really don't care,

But I threatened them with the Office of fair Trading and sent the Damm card back got a Full Refund and then bought her a Nvidia Geforce and she hasn't had a problem now,

Think I will bei Using them too in my mew rig, ATI not worth the Trouble.


Jolly Swagman

---

