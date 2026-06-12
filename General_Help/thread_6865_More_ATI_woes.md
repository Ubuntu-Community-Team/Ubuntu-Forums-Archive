---
title: "More ATI woes"
date: 2004-12-02
forum: General Help
---

### Post by froogle on 2004-12-02
Hi all, 

First up, I need to add a disclaimer. I'm not a total noob, but it is quite some time since I've done anything in anger with Linux, especially a Debian based distro like Ubuntu. That said I love the principles behind Ubuntu and I would dearly like to resolve this problem so I don't start distro jumping to find one where I can solve it. Anyways, on with the problem. 

I've got a Dell Inspiron 9100 with the ATI Mobility Radeon 9800 with 256 meg on board. The machine has a widescreen panel which optimally runs at 1680x1050. 

I've got Ubuntu installed and working great with the Vesa driver, but naturally everything looks stretched and nasty, so I wanted to get fglrx working. I did an apt-get on fglrx-driver form the standard sources, changed my driver name to fglrx and I get to the familiar black screen that others have seen. 

I then tried to use the fglrx driver from people.ubuntu.com/~daniels - same problem. I tried modifying using the option UseInternalAGPGART = no deal, same problem. 

I went to ATI's site and found their RPM of the latest drivers. This one explcititly says that my card is supported. However, I can't install it or do anything much with it really. I downloaded it, used alien to convert it to a .deb and then tried dpkg -i. however, I can't then go ahead and build from the sources since I get all sorts of errors about missing kernel headers etc etc. Bear in mind that this is the very first thing I've tried after doing a clean re-install. 

SO.... what packages do I need to get, and what specifically do I need to do with them in order to be able to build the latest ati drivers from their site? 

Any help on this would be really appreciated. I'm so keen to see ubuntu running in full widescreen high res sexy glory. 

Cheers, 

Pete

---

### Post by daniels on 2004-12-02
If you don't care about 3D acceleration, the standard 'radeon' driver will work just fine for you.

---

### Post by froogle on 2004-12-02
Thanks for that Daniel. I'm not actually too keen on getting the acceleration working at this point (later it would be nice), I just want to get the right resolution running. I'm guessing though that the true fglrx drivers will also support the power save features of the Mobility Radeon 9800, but again I can probably live without them. 

So now, sorry to be so lame, but how do I get the standard radeon driver onto my machine to try it out? Is it as simple as apt-get install radeon?

---

### Post by emperor on 2004-12-02
Are you using XFree86 or Xorg? The ati "fglrx" driver should work with XFree86 but will not work with Xorg 6.8 or above.  
 
 The default radeon driver in XFree86 or Xorg should already be installed.  For XFree86, it is defined as "ati" in XFree86Config-4.  Each driver has it's own parameters and options, so you will need to check the associated man page. Optionally, you could run the "debian" XFree86 Configuration program. There should be some info in the debian documention concerning this.  Anyone with experience in running the config program should comment further.

---

### Post by froogle on 2004-12-02
Awesome - thanks for that. It's XFree (I don't know how to get Xorg working/installed in ubunutu yet, nor whether there is any value in doing it). 

I had done some digging around with google after that last post and kinda got the idea that it was going to be simply a question of specifying ati instead of fglrx and seeing what happens. 

I'll try that as soon as the boss stops looking at my screen, and I can get out of Windows for a few minutes.

---

### Post by froogle on 2004-12-02
Well, using the default radeon driver (ati) in XF86Config really makes the problem worse. X doesn't even start up now and I get a no such device found. 

The thing I think I really want to do here is actually build the most recent drivers that ATI have on their site, which kinda takes me back to the original question...

What apt-get installs etc do I need to run to get the everything in place so that I can build those drivers? 

Any pointers?

---

### Post by froogle on 2004-12-02
In lieu of getting absolutely nowhere with the driver rebuilding I re-installed (I screwed up some stuff in messing around, I'm sure). 

On the clean install I grabbed daniels drivers and installed them. I ran fglrxconfig and built a nice new XF86COnfig which I then tweaked to make sure my mouse and keyboard would work. 

Well, now I can run X. The black screen I get I can get rid of by hitting the monitor switch button on the notebook. 

THe only problem though is that the damn thing won't run any resolution above 1024x768. Any attempt to set anythng else (1280x1024, or the one I want - 1680x1050) gives me a message in the X log saying Mode not found.


UPDATE: fglrxinfo is telling me that I'm running MESA, not a radeon...???
Update 2: (Sorry to go on and on on this but it's driving me nuts) Dmesg is reporting something strange "[fglrx:firegl_unlock] *ERROR* Process 5390 using kernel context 0

---

### Post by froogle on 2004-12-03
Some progress on this last night, which was interesting. Now, I know some of you already knew how to do this, but a bunch of us didnt, so I really hammered on trying to get the ATI drivers to build under ubuntu, and succeeded. 

I still had fglrxinfo telling me that it was using Mesa instead of the proper ATI Open GL stuff, and since I don't really use openGl for much at all, I don't know why I continued pressing on, but press on I did and actually managed to get the ATI drivers to work at full speed at one point, without Mesa. glxgears running at 3000FPS on a notebook is a sight to behold :)

Alas, this morning, it's gone back to using MESA and I have absolutely no idea why. I still can't get my full 1680x1050 resolution running either, and that's just driving me nuts. 

For those of you wanting to build the ATI drivers, following along with [www.watchland.org/dmcgraw/ati-debian.html](www.watchland.org/dmcgraw/ati-debian.html). Whenever he mentions kernel-source, or kernel-headers, change that to linux-source, or linux-headers and make sure you have modified /etc/apt/sources.list to use the Universe sites. Also do an apt-get install gcc to get the C compiler working properly - for some reason it doesn't on the CD based install (which is just odd in my opinion). 

Following along with that guide above, you should be able to get the drivers to build and install. Getting them to load and work though I'm still working on - as I said it happened once, but it was 2am and I can't fully remember what I did. 

When I've sorted this out, I'll build up a definitive "Using ATI's drivers on Ubunut with XFree" howto. I keep getting an itch to go over and try out xorg, but I really don't want to move to an unstable OS release just to get my video card working.

---

### Post by froogle on 2004-12-03
OK Some more progress. I got the Radeon info showing up consistently with fglrxinfo. 

The problem it seems was with the "restricted modules"?? whatever they are. I already had daniels feed in my /etc/apt/sources.list and did an apt-get dist-upgrade and it downloaded the restrictired modules thing from daniels site. When I rebooted, voila, fglrxinfo showed me as running the ATI gl engine. Great stuff. 

I'm still stuck with this crummy resolution though and no matter what I try I can't seem to fix it. From hunting around on Google pretty much all day today I think I am the only person on the entire planet that has a WXSGA Inspiron 9100 and who has installed Linux on it. Crazy stuff. 

Still, for those of the rest of you looking to get fglrx compiled and installed from the ATI website, follow the guide that I linked to on the previous post, do a dist-upgrade and you'll be all set. Works like a charm. 

I'm still open to offering copious amounts of gratitude in lieu of cash to the person that can fix my resolution issue though.

---

### Post by wallijonn on 2004-12-03
If you did run the XF86Config program, and you did choose the highest resoltuion, the only thing I can think of is[COLOR=Green] /etc/fb/modes[/COLOR].

---

### Post by froogle on 2004-12-03
Yup, did that - no result. 

Over the past 3 days or so I pretty much tried everything. I looked everywhere, tweaked everything, tried everything - no joy. 

So, this evening I thought screw it - I have stuff I need to be doing. I upgraded to Hoary and after a few tense moments where things just weren't uninstalling (fglrx for example), I managed to get xorg working, and now everything is perfect. 

I don't have 3D in any form, but I suspect that's a tweak to the config files, but what I do have is luscious 1680x1050 mode. At last Ubuntu looks like the gorgeous operating system it is, instead of looking like a lame Amiga emulator with everthing all stretched and squooshed. 

So, the moral - if you ahve an Inspiron 9100 running at 1680x1050 resolution from a Radeon Mobility 9800 - get xOrg. 

(I do have blurring on fonts in places though which is odd)

---

### Post by daniels on 2004-12-04
Works in X.Org, eh.  Hm.

It's always great when stuff unbreaks, and it's kind of more accidental than anything else.  Bonus.

---

### Post by Jarde on 2004-12-05
Here's how me and my friend solved it:

Use synaptic and search for restricted modules.

Remove all restricted modules for the 386 platform, reboot
and you are good to go. (at least we where)

---

### Post by flibblesan on 2004-12-17
[QUOTE=froogle]. For those of you wanting to build the ATI drivers, following along with [www.watchland.org/dmcgraw/ati-debian.html](www.watchland.org/dmcgraw/ati-debian.html).[/QUOTE]

They make little sense. There is stuff missing I'm sure. What do I do with the RPM? Where is the fglrx source?

---

