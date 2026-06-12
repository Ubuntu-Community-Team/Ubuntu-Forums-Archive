---
title: "Libdvdcss Where is it?"
date: 2005-11-01
forum: General Help
---

### Post by joris.brus on 2005-11-01
I can't find Libdvdcss in synaptic, I've tried to find a repository so it would, but most of them are not working or don't have it on there.
I can play a ripped dvd fine but I get a 'source can't be read' error with a "real" dvd.

So far I've figured out Ubuntu64 on my computer can't run flash, windows media 9, or properly use my audio card. This better not become another problem. 

Why is it so hard to get anything to work in 64 bit? even chroot doesn't work for me.

---

### Post by ecobuntu on 2005-11-01
[QUOTE=joris.brus]I can't find Libdvdcss in synaptic, I've tried to find a repository so it would, but most of them are not working or don't have it on there.
I can play a ripped dvd fine but I get a 'source can't be read' error with a "real" dvd.

So far I've figured out Ubuntu64 on my computer can't run flash, windows media 9, or properly use my audio card. This better not become another problem. 

Why is it so hard to get anything to work in 64 bit? even chroot doesn't work for me.[/QUOTE]

To get libdvdcss
1.  Install libdvdread3
2.  'sudo usr/share/doc/libdvdread3/examples/install-css.sh'

To get flash install
flashplayer-mozilla

To get w32codecs and java go this site
[http://tinyurl.com/bpxbf](http://tinyurl.com/bpxbf)
d/l the w32codecs.deb and the java.deb (of your choice)
then at terminal...
sudo dpkg -i *.deb

---

### Post by ecobuntu on 2005-11-01
that command under libdvdread...that script...that will d/l libdvdcss for you and install it.

---

### Post by RAOF on 2005-11-01
With the "build-essential" package installed, you can just run the script hidden away in /usr/share/doc/libdvdread3/examples/install-css.sh.  That will download the sources, build a .deb out of them, and (if you run with sudo) install the deb.

You'll need to have installed these packages first:
[LIST]
[*]fakeroot
[*]build-essential
[*]debhelper
[*]dpkg-dev
[/LIST]

[QUOTE=ecobuntu]To get libdvdcss
1.  Install libdvdread3
2.  'sudo usr/share/doc/libdvdread3/examples/install-css.sh'

To get flash install
flashplayer-mozilla

To get w32codecs and java go this site
[http://tinyurl.com/bpxbf](http://tinyurl.com/bpxbf)
d/l the w32codecs.deb and the java.deb (of your choice)
then at terminal...
sudo dpkg -i *.deb[/QUOTE]
Although, as you've already found, that won't work for installing flash or the win32 codecs on breezy64.  And it's so hard to get proprietry, closed source programs to work in breezy64 because there's pretty much nothing the ubuntu devs can do about it - you're at the mercy of the companies producing the stuff.  So, because Macromedia don't care enough about 64bit linux users, there's no 64bit flash plugin.  And, amazingly enough, Microsoft is not particularly interested in helping you use their non-free, patent encumbered wmv9 video decoder (in a way which probably violates **some** IP law) :rolleyes:

---

### Post by joris.brus on 2005-11-01
Thanks for the post.. but I'm using ubuntu64 as posted

I have libdvdread3 installed, this is the totem error
The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?
Like i said.. it doesn't play storebought dvds

There is no flashplayer mozilla but there is a libflash (gpl flash) which I have installed and never seems to play actual flash content and crashes my browser occasionally

And here's the error for w32codecs

dpkg: error processing w32codecs_20050412-0.0_i386.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 w32codecs_20050412-0.0_i386.deb

Trust me I've tried all the amd64 methods posted on this forum for w32codecs

----------------------
Ubuntu works good other than playing most multimedia formats

---

### Post by RAOF on 2005-11-01
[QUOTE=joris.brus]...I have libdvdread3 installed...[/QUOTE]
But have you run the install-css.sh script?  That (builds, then) installs libdvdcss, which you need to break the (pathetically weak) css encryption on the commercial disc.

[QUOTE=joris.brus]...Ubuntu works good other than playing most multimedia formats[/QUOTE]
After installing the gstreamer0.8-plugins & gstreamer0.8-plugins-multiverse, I've found that totem-gstreamer plays pretty much anything I've thrown at it (except for actually corrupted stuff ;)).  I suppose I just don't encounter much stuff in formats for which there's no open-source decoder.

Incidentally, I wonder if pitfdll (the gstreamer component that can load the windows .dlls for wmv9 playback) could handle 64bit dlls...  If you could scrape out the codec dlls from a copy of Win64, that may work ;)

---

### Post by joris.brus on 2005-11-01
RAOF, I tried you approach as well, thanks. Everything installed ok I think.
The final couple lines:

Any problems?  Interrupt now (control-c) and try to fix
manually, else go on and install (return).
Selecting previously deselected package libdvdcss2.
(Reading database ... 71295 files and directories currently installed.)
Unpacking libdvdcss2 (from .../libdvdcss2_1.2.5-1_amd64.deb) ...
Setting up libdvdcss2 (1.2.5-1) ...

Unfortunately I get the same errors trying to play a dvd

---

### Post by RAOF on 2005-11-01
That should have done it, goshdarn it.  Can you try running totem from a terminal, and noting the error messages it spews?

---

### Post by joris.brus on 2005-11-01
Thanks for all your help.. tried gstreamer plugins.. unfotunately that doesn't let me play wmvs yet either. 
Here is the totem error

(totem:18635): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(totem:18635): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:18635): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
** Message: don't know how to handle audio/x-wma, wmaversion=(int)2, bitrate=(int)20008, rate=(int)22050, channels=(int)2, block_align=(int)813, codec_data=(buffer)004400001700b50c0000
** Message: don't know how to handle video/x-wmv, wmvversion=(int)3, framerate=(double)25, width=(int)320, height=(int)240, codec_data=(buffer)4e291a11

---

### Post by joris.brus on 2005-11-01
actually that was totem launching a wmv file.. not sure how to start a dvd from terminal.

---

### Post by joris.brus on 2005-11-01
i launched totem then hit play dvd
root@Thunder:/home/joris# totem

(totem:18697): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(totem:18697): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

----up to here is just launching totem.. the errors following is trying to play dvd

(totem:18697): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Can't open file VIDEO_TS.IFO.
root@Thunder:/home/joris#

---

### Post by RAOF on 2005-11-01
Just launch totem, and go file->play disc.

Sadly, wmv3 (also known as Windows Media 9, I think), won't work.  There's just no open-source decoder for them (currently).

---

### Post by RAOF on 2005-11-01
[QUOTE=joris.brus]...
libdvdread: Using libdvdcss version 1.2.5 for DVD access
libdvdread: Can't open file VIDEO_TS.IFO.
...[/QUOTE]
Ah, ok.  We have, at least, got libdvdcss working.  This should work, and I don't know how to fix it since it doesn't.

As a last resort, you could try playing one of the files on the dvd.  If you browse the dvd, you should find a directory like "video_ts" or something, full of  files named "thingamybob_01.vob" and suchlike.  You could try playing one of those .vob files.  This is in no way a solution, but you might be able to at least play the movie that way.

---

### Post by joris.brus on 2005-11-01
Well.. thanks anyway.. people like you make using ubuntu64 a bit more bareable. 

When opening individual files, I can almost see parts of the dvd if it wasn't covered by big moving green blocks.. ie (scrambled)

---

### Post by RAOF on 2005-11-01
You might want to try VLC or mplayer as alternative players.  One of them might work better for you.  :???:

---

### Post by joris.brus on 2005-11-01
Wow.. Xine works now for another bought DVD, I swear I was trying different players the whole time. Totem still doesn't but I prefer Xine ayway.

The first DVD that I was trying the whole time still says that it's encrypted and due to the country I live in I can / cannot install libdvdcss. 

I'm satisfied with this, So anybody reading this, for future reference.. try the following.


[QUOTE=RAOF]With the "build-essential" package installed, you can just run the script hidden away in /usr/share/doc/libdvdread3/examples/install-css.sh.  That will download the sources, build a .deb out of them, and (if you run with sudo) install the deb.

You'll need to have installed these packages first:
[LIST]
[*]fakeroot
[*]build-essential
[*]debhelper
[*]dpkg-dev
[/LIST]


Although, as you've already found, that won't work for installing flash or the win32 codecs on breezy64.  And it's so hard to get proprietry, closed source programs to work in breezy64 because there's pretty much nothing the ubuntu devs can do about it - you're at the mercy of the companies producing the stuff.  So, because Macromedia don't care enough about 64bit linux users, there's no 64bit flash plugin.  And, amazingly enough, Microsoft is not particularly interested in helping you use their non-free, patent encumbered wmv9 video decoder (in a way which probably violates **some** IP law) :rolleyes:[/QUOTE]

---

### Post by SickTwist on 2005-11-02
Totem uses the gstreamer backend by default in Ubuntu. Gstreamer will be great once it has matured a bit more but it is still a work in progress. However, you can also use the xine backend with Totem if you prefer Totem's interface. Just install the totem-xine package (sudo apt-get install totem-xine).

---

### Post by pjs_flyer on 2005-11-02
Yup - after installing libdvdcss2, totem-gstreamer was still no go, but totem-xine works like a dream (even better once the hdparm thingy is enabled as well!)

---

### Post by ptiboli on 2005-11-13
hey

thanks a lot! I ran the libdvdread3... script and now it works fine for totem as well as gxine.
thanks again

---

### Post by Aphorism on 2005-11-20
Is this EXCEPTIONALLY helpful block that describes the four things you will need to run that install script listed in the wiki?  

By the way, if everyone quits using stupid proprietary codecs, the whole wm9 format issue won't be a problem.  Just quit using it.  Tell everyone to quit using proprietary formats and stick to your guns.


The more people who 'fall back' to horribly closed source patent restricted formats (Read mp3, java, flash, fingerinbumetc) are only supporting clusterf*ck companies like Apple and Microsoft.

---

