---
title: "Compiz iz mezzin up my dezktop"
date: 2007-12-19
forum: General Help
---

### Post by uberlube on 2007-12-19
I just upgraded my graphics card from a p.o.s. ATI Radeon Xpress 200 integraded to a Nvidia GeForce 7300 GT 512 MB and I have all the appropriate drivers installed. Now I assumed that if you want to activate compiz to get all the eyecandy that i've been seeing on youtube, all you have to do would be go to the command line and type in; compiz. Well I did that and while its loading it says ;

Checking for Xgl: not present. 
Detected PCI ID for VGA:        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
01:00.0 0300: 10de:0393 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format


Ok so i did get that cube to work once but i wasnt getting all the desktop effects that i checked off in the Advanced Desktop Effects menu. And now either i dont have any window borders at all or their red even though ive set them to be a custom type that look like the borders in a mac. Also when i watch movies in vlc and i go into full screen mode i can still see my desktop along the edges.

---

### Post by approaching on 2007-12-19
you need to install xgl brother. at least that is what the message is saying. take a look around in synaptic, i am sure that you will find something like that.

here is your one stop shop:
sudo apt-get install xserver-xgl

and the page i found it on is even in this forum:
[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

funny thing about linux, and this may sound condescending, but it was a real issue with me, and i totally don't mean it that way, but error messages actaully mean something in linux. if something isn't present, or there was an error thrown on that line, or something of that nature, google whatever it was. i will often just google the error line and out pops whatever i am looking for.

Have Fun!

---

