---
title: "Totally Fubared Timidity"
date: 2013-05-11
forum: General Help
---

### Post by pcflight on 2013-05-11
Ok so I've been fighting with Dosbox and Ultima Underworld to get the audio to work.  Part of what I did was installed timidity using apt-get.  I got it working right for one game.  Anyhow I ended up for some moment of insanity removed timidity using apt-get remove.  I went to reinstall it and now it is not coming on at startup.  I've tried uninstalling and reinstalling again after removing the timidity folder out of /etc.  The package is there but it is not coming up and handing out ports to assing midi devices (I've checked though pmidi -l).  Anyone have an idea on how I can reinstall Timidity and get it to either reconfig itsself?

Also on a side note, anyone know the best way to get midi's working in Ultima 4 on Dosbox?

I am running Xubuntu 12.04 as well.

---

### Post by pcflight on 2013-05-11
And Fixed it, 

I had to use apt-get purge timidity to clear out everything and redo the files in init.d.
Next since I blew out the config file that came with it for sounds, I downloaded the pack from [http://www.fbriere.net/debian/pool/misc/squeeze-amd64/eawpatches_12-1~fbriere.5_all.deb](http://www.fbriere.net/debian/pool/misc/squeeze-amd64/eawpatches_12-1~fbriere.5_all.deb) as indicated in the Ubuntu howto.  After changing the config file file to point to them, I was able to get it to start at boot.  Now just need to get Dosbox and it to play nicely.

---

