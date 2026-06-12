---
title: "Can't view any CD or DVD"
date: 2007-11-23
forum: General Help
---

### Post by TV-VCR on 2007-11-23
"Cannot mount volume" "Invalid mount option when attempting to mount the volume 'UDF Volume"

How do I make this go away? It happens with any kind of CD or DVD.

Hmm... under properties > drive >settings, there are 3 options (Mount Point, File System, Mount options) that are all blank. It appears to sees the disk (it's 2.6GB). Should I change something there?

---

### Post by TV-VCR on 2007-11-23
Bump

---

### Post by hikaricore on 2007-11-23
Please allow 24-48 hours before bumping a post, especially the day after a holiday (in some areas) response times of volunteers/forum members will be slower.

---

### Post by TV-VCR on 2007-11-24
Well, 24 hour bump.

---

### Post by TV-VCR on 2007-11-24
I received this PM:
> f you are stuck and are trying to get DVDs or any multimedia file to play here is your guide.

Open up Add/Remove programs from your Application bar.

Go to Sound&Video and Find and Check all of the packages below (easily done by searching for gstreamer)

* "GStreamer ffmpeg video plugin"
* "GStreamer extra plugins"
* "GStreamer plugins for aac, xvid, mpeg2, faad"
* "GStreamer plugins for mms, wavpack, quicktime, musepack"


Then go to Other subsection of Add/Remove and find

* "Ubuntu restricted extras"

Then this you enter in the terminal (by the way the same command can be found at the offical Medibuntu site)

sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list

finally run " sudo apt-get update "

But your also going to need the REAL codecs that will allow you to play DVDs they
can be found here through a program called Automatrix you can find it here.

[http://www.getautomatix.com/wiki/ind...e=Installation](http://www.getautomatix.com/wiki/ind...e=Installation)

The program it installs is borderline illegal act like your living outside
the US so you can install the codes you need. When you run this program.

Finally head back to Add Remove and look for the Kaffiene Player it frankly
plays DVDs better than any other program.

This should get DVDs to finally run for yo

Those plugins were not in the add-remove area and I couldn't find the "restricted areas".

---

