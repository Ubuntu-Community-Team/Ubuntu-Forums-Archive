---
title: "Video card help please?"
date: 2006-07-24
forum: General Help
---

### Post by Spyder on 2006-07-24
I have been told that I need to set up my video card, and I am not sure how so I figured I would ask here, I think I need to set up 'OpenGL Direct Rendering' and '3D Acceleration'

My video card manufacturer is 'Mesa project' so yea.. any help would be appreciated, and if I need to supply more information please tell me and I will put it on here.

---

### Post by stimpsonjcat on 2006-07-24
there's some good info on how to install non-free video drivers in the [Wiki]("https://help.ubuntu.com/community/Video").

---

### Post by Spyder on 2006-07-25
I couldnt find anything in that link that actually helped me :/

---

### Post by twotonz on 2006-07-25
Hallo Spyder,
I think you have missunderstood a few things. "Mesa" is the stuff behind your desktop, not a video card. Please type in the console...
lspci
you should get an output of your pci devices (agp is also listed)

```
0000:03:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)
```

look for something along the lines above, as you can see, I have an nVidia card. I think 70% of users have either nvidia or ati.

Love & Peace
anthony

---

### Post by Spyder on 2006-07-25
thank you twotonz, i did what you said and it came up with.
```
0000:01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741 /760/761 PCI/AGP VGA Display Adapter

```    does that help at all?

---

### Post by LORD_PoLvO on 2006-07-25
spyder,

you will need a dedicated driver for this device which might be able to be found at the manafacturers website i asume your manafacturer is SiS as that is the info you have given so try going to thir website looking for drivers downlaods foir you gfx adapter.


hope it helps

---

### Post by Spyder on 2006-07-25
well, i went to the site then showed it to a friend then found out there are only red hat drivers avaliable. so yea.. any more ideas?

---

### Post by LORD_PoLvO on 2006-07-25
hmm yeah i went there and there are  red hat drivers so yeah i wont say nething about that coz i dont know wether they will work or not but i sugest just doing sumthing like 


SiS] 661/741 /760/761 PCI/AGP VGA Display Adapter linux drivers


or sumthing like that in google and seing what you can come up with maybee.

---

### Post by eXisor on 2006-07-25
As far as I know there is an inbuilt SiS driver that supports DRI. It would help if you pasted the [device] section of your xorg.conf file here so we can see what you're currently using. 

To get to it type : sudo gedit /etc/X11/xorg.conf

If it shows 'vesa', then change that to 'sis' and restart gdm.

---

### Post by eXisor on 2006-07-25
Alternatively, you can just resetup the whole X environment again by using...

```
sudo dpkg-reconfigure xserver-xorg
```

and then choose 'sis' as your video card.

---

### Post by twotonz on 2006-07-25
Hallo again,
 Ermmm, is not sis, normally an onboard graphic solution? Spyder, do you have a laptop by any chance?
 If the only drivers available are as rpm's then perhaps you could use "alien" to convert to deb.
 Do not want to put a damper on all this, but I do not think you are going to have much 3D fun with this chipset, but then, I am far from knowlegable on this subject, so I could just be making an idiot of myself.
 eXisor has given you a good tip, I would defently start there.

 One last thing, do you know how much video-memory you have? You could have a look in Device-manager or info-centre. Let us know how you get on....

Love & Peace
anthony

---

### Post by LORD_PoLvO on 2006-07-26
ahh yes ur using a lapy my friend hmm i would go with eXisor's tip if that fails ill help u on msn with alien kk

---

