---
title: "Can't download mplayer codecs package, possible Firefox problem?"
date: 2004-11-11
forum: General Help
---

### Post by Monika on 2004-11-11
I cannot connect to any of the mirrors listed here:
[http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html)
when I try to download the "essential codecs" package (all of the other three packages I can download).

I get a message saying "The link could not be saved. The web page might have been removed or had its name changed.". And when I ok it, sometimes firefox hangs.

If this mystery cannot be solved, then what can I do to totem-xine for it to be able to play *.rm, *.rmm, *.ogg (it only plays the sound), *.wmv (some play, some don't - the ones that don't, change their icons to *.asf when clicked)

I could do with a program that would have a firefox plugin to watch trailers and such, but that's not an immediate priority, wheras I have lots of files of that type which I really want to have access to and I really like Ubuntu (in general it's so much nicer than Windows :) ), but it's one of those things that I do a lot of and if I can't do it, I'll be booting windows...
And I don't want to be booting windows :D So...

---

### Post by AndersAA on 2004-11-11
Don't be so quick to blame firefox/ubuntu, it's just mplayers server's having problems ;)

just checked now, none of those links works right now.

give em a bit of time and I'm sure it'll be up and running again (or take the filename and search for it in filemirrors.com)

---

### Post by Monika on 2004-11-11
Sorry, I should have added that I had those same problem (and only with that one file) a few weeks before on SuSE linux (I also used Firefox). Also, I've been trying from Ubuntu yesterday a few times, and quite a few times today.
And it's only that one codec package that is a problem for me.
And on top of it Firefox hangs sometimes when this happens which made it more fishy for me.

---

### Post by fng on 2004-11-11
An alternative solution is adding marillat's repositories to the sources list.

Computer -> System COnfiguration -> Synaptic
Synaptics starts up
Settings -> repositories
click on the new button

Fill in the fields like this :
binary (deb)
URL : [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/)
Distributions : testing
Sections : main

Click on the ok button
Click on the big reload button in the lupper left corner
Search for the mplayer package for your specifique architecture (mplayer-386, mplayer-686, mplayer-k7, ..)
Install it!!

---

