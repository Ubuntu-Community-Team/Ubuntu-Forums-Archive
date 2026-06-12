---
title: "Graphics on intel g965"
date: 2006-10-29
forum: General Help
---

### Post by rene100 on 2006-10-29
Does anybody know how I can get my onboard graphics working in Edgy?  I have an asus p5b-vm with the GMA x3000 onboard graphics.  I'm a newb btw so please keep that in mind when responding.

Thanks for the help

-R

---

### Post by thoughts on 2006-11-03
I just bought an Intel motherboard (DG965WH) that uses this graphics chip.  I'm using Edgy (2.6.17 kernel) and the i810 driver works fine for this chip, for 2D stuff.  3D doesn't work (try glxgears or glxinfo to see) but from what I've read the 2.6.18 kernel may have better support for the 965 chipset so I'm going to try that.

You can run "sudo dpkg-reconfigure xserver-xorg" to change your video driver to i810.

--
Anthony DiSante
Encodable Industries
[http://encodable.com/](http://encodable.com/)

---

### Post by fuma on 2006-11-07
I have also an asus p5b-vm. Does your network driver run
out of the box? How did you make him work?

thanks for your reply

fuma

---

### Post by sir_skiner on 2006-11-24
and? did kernel 2.6.18 solved the problem? it bugs me too...

---

### Post by lompolo on 2006-12-20
Edgy kernel has (now) support for 965 chipset.

---

### Post by kweiner on 2006-12-22
> **lompolo said:**
> Edgy kernel has (now) support for 965 chipset.

How can I tell if I am running the kernel that has support for the 965 chipset?  I am running Edgy on a Dell Dimension 9200c which has the G965 chipset and a GMA X3000 onboard video chip.  I still have not been able to get the proper 1680x1050 resolution to work with my Dell 2007WFP monitor.

---

### Post by epochx on 2007-05-14
I'm also working on a Dell Dimmension E520 with intel G965. For ubuntu Feisty Fawn (aka V 7.04) there are some drivers but they only support 2d. I properly set my screen to 1280 x 1024, but it seems that there's no way to  turn 3d acceleration on now.

PD. Excuse my english XD

---

### Post by sitmex on 2007-06-13
> **epochx said:**
> I'm also working on a Dell Dimmension E520 with intel G965. For ubuntu Feisty Fawn (aka V 7.04) there are some drivers but they only support 2d. I properly set my screen to 1280 x 1024, but it seems that there's no way to  turn 3d acceleration on now.


Hi;

I've installed 7.04 and I screw up my xserver configuration, so I ended with a text screen. I've read that I should set change the video driver to i80, as "THOUGHTS" mention it... but now that I'm stuck, how should I do it..

After install, I didn't have the chance to change root password so I can't perform any sudo commands.

Should I re install?, if so, after doing so, how can I change the driver to i80?



Thanks in advance.

---

### Post by ecoute106 on 2007-08-14
HELP! I have had the board for some time now and for some reason all of a sudden the onboard graphics are not allowing me to change the resolution from 800x600. The only other option it gives me as resolutions for the driver that was installed is 1024x768 i've tried everything uninstalled drivers and it gives a lot of resolution sizes that are usable still however 1024x768 isn't able to be used. When the 1024x768 resolution is used with no drivers, drivers on dvd or the updated drivers the screen continues to be scrambled. Until last week i had been solely using this resolution and out of no where caput.

I've updated to vista prior to reformatting drive and starting a new didn't fix, updated drivers didn't fix, nothing seems to be working so i'm at a loss called intel technical support and offered little help beyond what i consider to be common sense as i've tried everything that i could think of. Anyone have similar issues please help if you can thank you so much

---

### Post by jesusjimenezflores on 2007-10-14
Hi, i was the same problem, i was cannot get 1680/1050 on my flat panel, I have g956 graphics. I install 915Resolution an change some values, try next:


#apt-get install xserver-xorg-video-intel
#apt-get install 915resolution
#gedit /etc/default/915resolution

mode=3c
XRESO=1280
YRESO=800
BIT=32

#reboot

Thats Work so fine to me

Regards

---

