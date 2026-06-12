---
title: "Need help for OpenGL with Intel Graphics"
date: 2017-10-20
forum: General Help
---

### Post by santtomas on 2017-10-20
Hi, I just recently installed Ubuntu in a little old toaster that I like to experiment with. The PC in question is a Sony Vaio model VPCW120AL. Here's the Support page in case you need to look at it (sorry that's in spanish but I couldn't find it in english): 

[https://esupport.sony.com/LA/p/model-home.pl?mdl=VPCW120AL&template_id=2&region_id=2&tab=manuals#/manualsTab](https://esupport.sony.com/LA/p/model-home.pl?mdl=VPCW120AL&template_id=2&region_id=2&tab=manuals#/manualsTab)

The thing is looking up a bit I found that the graphics unit in this computer supports OpenGL version 1.4 for Windows and version 2.1 for Linux respectively. The Graphics unit would be a third generation Intel GMA, more precisely the GMA 950 with the Mobile 945 Family chipset.

I learned about this here:

[https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units](https://en.wikipedia.org/wiki/List_of_Intel_graphics_processing_units)

_What I would like to know is how to install the new drivers needed to upgrade OpenGL into 2.1_

As of the moment I believe I  still have OpenGL version 1.4 as when I introduce "glxinfo | grep "OpenGL version"" in the terminal I'm given the following response: "OpenGL version string: 1.4 Mesa 17.0.7"

Thanks in advance.

---

### Post by GTP-Hank on 2017-10-20
do you have intel-linux-graphic-installer installed?

---

### Post by santtomas on 2017-10-21
Sorry for the delay, I was busy, anyway I tried to do a little more research and found something called "Intel Graphics Update Tool for Linux", more precisely the 2.02 version I believe, the one made for Ubuntu 16.04 which is the OS I have; was that the one you were referring about? Anyway I install and launch it, it update my drivers and all apparently, nothing went wrong as far as I know, but when I write "glxinfo | grep "OpenGL version"" on terminal to know what version of OpenGL I have (is that the correct way to know which version you have? Still not very good at this sorry) I'm still given "OpenGL version string: 1.4 Mesa 17.0.7" Btw thanks a lot for answering.

---

### Post by mc4man on 2017-10-21
While it 'appears'  the 945 chipsets should have version 2.1 support in linux it's not clear if every 945 chip does or to what extent.
For curiosity post this (a bit more expansive..
```
glxinfo | grep OpenGL
```

---

### Post by Yellow Pasque on 2017-10-21
[https://www.phoronix.com/scan.php?page=news_item&px=Mesa-i915-OpenGL-2-Drop](https://www.phoronix.com/scan.php?page=news_item&px=Mesa-i915-OpenGL-2-Drop)

---

### Post by santtomas on 2017-10-22
Ah, nuts. Would you mind telling me how to enable OpenGL 2.1 tough? I mean you can enable it but it won't work with newer games right? At least that's what I got from that article. The game I'm planning to play is fairly old (it's Diablo 2, I'm trying to get Glide to work) so I think it would be fine, right?

---

### Post by mc4man on 2017-10-22
If I'm reading that article correct you could try installing either 14.04.5 image or the 16.04.1 image. Both would use an older mesa.
[http://releases.ubuntu.com/14.04.5/](http://releases.ubuntu.com/14.04.5/)
[http://old-releases.ubuntu.com/releases/16.04.1/](http://old-releases.ubuntu.com/releases/16.04.1/)
(- 14.04.5 may be better for that hardware

---

### Post by Yellow Pasque on 2017-10-23
```
sudo apt-get install driconf
driconf
```

You should see options for ARB_occlusion_query and ARB_fragment_shader. Hopefully, you can force them on, save the changes and log out/in and check glxinfo.

---

### Post by santtomas on 2017-10-24
sorry, to bother you again but looking up a bit on the whole "how to update drivers in Ubuntu" topic I stumble upon this PPA:

[https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

and this tutorial which features this exact PPA as well:

[https://www.youtube.com/watch?v=X-qCK2vYtzo](https://www.youtube.com/watch?v=X-qCK2vYtzo)

Is this what I was looking for? If not could you explain why? I want to at least learn something from this whole experience. If nothing else, could you tell me the differences between installing the PPA like the launchpad page indicates instead of doing it the way the youtube tutorial says so?

Thanks in advance.

---

### Post by mc4man on 2017-10-24
The Oibaf ppa provides slightly newer (git master) mesa. In your case won't matter as you either need the workaround suggested by Temüjin or an_ older_ mesa that hasn't disabled 2.1 for your hardware.

---

### Post by santtomas on 2017-10-24
I see. Well I'm going to give the older images a try I guess. Could you please also tell me the differences between installing the PPA like the launchpad page  indicates and doing it the way the youtube tutorial says so? (I think he uses the Synaptic package manager in case you don't have time to watch the whole video) By the way after I install the older Ubuntu version, should I try to install the PPA? What about the Intel Graphics Update Tool? Thanks a lot for everything.

---

### Post by mc4man on 2017-10-24
If you were to add the ppa then you'd end up back on mesa 17.x where opengl 2.1 apparently has been disabled for your hardware.
Just to make clear - there is absolutely no reason for you to use that ppa unless he reverted the mesa changes ^  which there is no indication they have been.
Did you try the commands  & procedure posted by Temüjin?

---

### Post by santtomas on 2017-10-26
Holy crap that worked! Thanks a lot! I probably shouldn't touch anything now right? I mean no new drivers, nothing...

---

### Post by santtomas on 2017-10-26
thanks a lot, your idea actually worked. Again, thanks.

---

### Post by Yellow Pasque on 2017-10-26
Nvm

---

