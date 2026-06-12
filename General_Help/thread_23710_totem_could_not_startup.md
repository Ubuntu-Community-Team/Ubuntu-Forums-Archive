---
title: "totem could not startup"
date: 2005-04-03
forum: General Help
---

### Post by lee_connell on 2005-04-03
resource busy or unavailable.  what is causing this error.  it was working and now its not yes i did install some packages not related to totem.  what can i do to debug this?

totem --debug doesn't report anything.  I've tried rebooting with dvd already in and same problem.  this was an issue previously during the whole haory dev release.  Seemed to be fixed the first time i used totem and then i added some packages like libs and other apps, rebooted. This is all within a time period of a day so i'm just listing this here it may not even be related.

btw: gxine does work :)

---

### Post by Zwack on 2005-04-03
I have the same issue.  I'll see if I find anything to fix and report back here.


...  Well, looking at the debugging info I get this...

arm10@toxic:~ $ totem --gst-debug-level=2
ERROR (0x80820a0 - 309045:56:30.809755000)     xvimagesink( 7911) xvimagesink.c(739):gst_xvimagesink_get_xv_support:<xvimagesink0> No port available

More as I find it...

Z.

---

### Post by Zwack on 2005-04-03
OK it looks like it's something to do with the XVideo extension.  xvinfo shows no adapters present.  Now all I need to do is work out how to either tell it to ignore the xvideo extension or get that working...  :cry: 

Z.

---

### Post by Zwack on 2005-04-04
Greetings Lee,

What kind of graphics card are you using, and what driver are you using with it?

I've tracked my problem down (and the news isn't good)...

Basically, if I turn off DRI in my /etc/X11/xorg.conf then I can run totem.  But glxgears gives me around 80 fps.  If I leave DRI on then I cannot run totem but glxgears gives me around 700fps.  

I'm using the ATI fglrx driver.  So it looks like you have a choice to make.  Good GL performance, or run totem-gstreamer.  I'll probably switch to totem-xine myself.

If you're not using this driver then you have a different problem I'm afraid.

I wish that there was a driver that gave me both...  :-(   Still at least I know why...  :) 

Z.

---

### Post by lee_connell on 2005-04-04
Agh Zwack,

good debugging man.  That would be the problem for me too :|  I did just add fglrx to my xorg.conf file.  So XVideo is a totem-gstreamer extension which is not working properly?

Are you going to file a bug on this?

Thanks alot for your input!!!  Atleast we know what the problem is :)

Also, my system finally froze up again last night so i will be looking into the renderaccel issue ( [http://ubuntuforums.org/showthread.php?t=23670](http://ubuntuforums.org/showthread.php?t=23670) ) and see if that also fixes my problem. :)

thanks again,

Lee

---

### Post by aggyb on 2005-06-13
If you can't get XV to work and your using the ATI binary driver try adding this to your xorg.conf file in the device section:

        Option          "VideoOverlay"          "on"
        Option          "OpenGLOverlay"       "off"

Fixed the problem for me  :) 

Now if only they'd release the driver for BSD too. Ah well.

---

