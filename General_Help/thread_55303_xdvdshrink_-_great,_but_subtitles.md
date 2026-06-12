---
title: "xdvdshrink - great, but: subtitles ?"
date: 2005-08-08
forum: General Help
---

### Post by AlterEgo on 2005-08-08
[http://dvdshrink.sourceforge.net/index.html](http://dvdshrink.sourceforge.net/index.html)

Very nice dvdshrink-alternative  :) 
Installing is easy using the Sourceforge link (no .deb, unfortunately) and the dependencies can easily be installed via apt:
```

    * The transcode package and it's required codecs (ripping etc),
    * the mjpegtools package (re-multiplexing),
    * the mkisofs package (creating ISO images),
    * the subtitleripper package (converting subtitles),
    * the gocr package (for subtitles),
    * the dvd+rw-tools package (burning), and
    * the dvdauthor package (authoring DVDs).

The script also makes calls to 'cat', 'stat' and a few other standard Linux tools. You'll want to make sure that they are in your toolset (coreutils package).

If you want to run the GUI front-end you'll need to have perl and perl-GTK2 installed. 

```.

It works really well, and quite quickly tool.

But: how can I get the subtitles working? 
subtitleripper 0.3.4 is not properly recognised by xdvdshrink, and neither is the version 0.6.14 that is mentioned [ here ](http://ozzzy.dhis.org/DVDShrink.html).

Thanks!

---

### Post by cvmostert on 2006-05-25
I like using linux native programs too, try using lxdvdrip (commandline) but does subtitles as far as I can remember.

Ciao

---

### Post by hanzomon4 on 2007-07-25
dvdshrink -u "number" 

You need to give a number for the subtitle stream, use dvdshrink - I to get the proper information, stream number.

Ex: dvdshrink -u 1

---

### Post by willz06jw on 2007-09-16
> You must edit /usr/bin/xdvdshrink.pl to enable subtitles:

1)sudo gedit /usr/bin/xdvdshrink.pl
2) Go to line 969 and change
if ( qx/subtitle2pgm -h 2>&1/ !~ /-X/ ) {
to this
if ( qx/subtitle2pgm -h 2>&1/ !~ // ) {

I had the same problem and this was the only solution I found.

mcrosmar gave this advice (in 2005).

This worked for me.  I hope this helps. :guitar:
Willz06jw

---

### Post by posterboy on 2007-09-16
I would love to try this out. No idea how to do that. I have been on ubuntu 3 weeks, and EVERYTHING is unfamiliar. :) I came from FC6, where rpms are normal, but how can I get the source code for this onto my ubuntu box? Thanks, Ray

---

### Post by willz06jw on 2007-09-16
Just use Automatix -- thats how you load most things.  It makes Ubuntu rock.

Just go to [www.getautomatix.com](www.getautomatix.com) and follow the directions. (- btw the site is down right now, it will be back in a few hours though I bet.)

Willz06jw

P.S. As far as my other suggestions about subtitles, you enter those at the command prompt after you Automatix the xdvdshrink in.

---

### Post by posterboy on 2007-09-17
Thank you.

---

