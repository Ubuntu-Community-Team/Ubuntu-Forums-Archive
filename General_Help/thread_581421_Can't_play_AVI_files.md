---
title: "Can't play AVI files"
date: 2007-10-19
forum: General Help
---

### Post by mindstalk on 2007-10-19
In Feisty, Totem had automatically done something to make itself play AVI files.  I'd also added GStreamer/ffmpeg and /extra, and the Other/Restricted package.  I never did get AVIs playing in Kubuntu or Xubuntu desktop environments though, which I thought was weird.

Now I have Gutsy.  Totem wouldn't play WMA or AVI files.  I added Medibuntu to my repository, installed libdvdcss2 and w32codecs, and added all the other GStreamer packages.  WMA files play now, but AVI still won't.  "You may need plugins" Totem says, with no clue as to how to find such plugins.

---

### Post by mindstalk on 2007-10-19
I *can* play AVI files in mplayer, and was able to even before the last steps, I think.  But mplayer is slow to start up and has a poor interface, I actually liked Totem, and shouldn't it work by now?

xmms doesn't work either.

---

### Post by davidjmayo on 2007-10-19
not a solution to your Totem problem but have you tried vlc which is in add/remove==>multimedia

---

### Post by mindstalk on 2007-10-19
Yeah, I've been getting used to VLC, just now.  It does work.  As you say, still a bug that Totem doesn't, when in Feisty it could make itself work...

Thanks.

---

### Post by strabes on 2007-10-19
sudo aptitude update && sudo aptitude install ubuntu-restricted-extras

---

### Post by mindstalk on 2007-10-19
> **strabes said:**
> sudo aptitude update && sudo aptitude install ubuntu-restricted-extras

I already had ubuntu-restricted-extras installed.  Ran your command anyway, and still get the "Video codec 'XviD' is not handled" response to my AVI.

---

### Post by Neo_Me on 2008-03-25
I also Cant Play AVI Files In Ubuntu 7.10 

.. Here's The Whole Story ( I am bad in english )
I downloaded Xubuntu 7.10 ... bcauz everyone told it was faster .. 

actually  .. it was not faster than my win xp ..( i am using it for 2 / 3 years. )
and all media files were not working in totem .. . i tried VLC .. audio worked .. video was some bizzare blah blah stuff .. ( some lines n stuff ) , 100 % same with mplayer

so after installing some 200 updates ... i unistalled xubuntu and installed ubuntu ,..

and the same thing happened .. i dunno what is the problem ... 

So .. again After Installing some 200+ updates .. im thinking of going back to XP ..

PS : FF crashed once while i was writing this...

Any Help ?

I really Like To try Ubuntu ...

---

### Post by Neo_Me on 2008-03-25
By The Way , It was Ubuntu 7.10 which had the problems .. .

I had no problems with my past install of 7.10 or 7.04 .. i know its some fault on my part ( as it worked 3 months ago ) ,

---

### Post by jessebean on 2008-06-21
I ran `sudo aptitude update && sudo aptitude install ubuntu-restricted-extras` and watched it install 32mb of packages, but still totem will not play avi files except in very slow motion.

---

