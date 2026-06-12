---
title: "Graphic equaliser for 12.04 non-Geek wanted"
date: 2014-01-14
forum: General Help
---

### Post by Richard_York on 2014-01-14
I have Ubuntu 12.04, since leaving Windows last October, and the sort of speakers which want to boost the bass on everything. One of the few things I still haven't found on Ubuntu is a workable graphic equaliser, so I can reduce the bass to enjoyable levels.
I can't find one in the Software Centre, and I don't want a complex mixer set-up for multiple inputs, just a useful level of treble-bass control. 

I see from earlier posts there have been issues with these in the past. I see a lot of "Doesn't work" "Makes it all crash" "Breaks my sound system" comments, which don't inspire confidence either!
I also see that I can't understand much of what's written, as it quickly leaps into acronyms and techie language!

Please can you recommend a simple, workable graphic equaliser? 

Thanks,
Richard

---

### Post by tgalati4 on 2014-01-14
Install *audacious* and play with it for awhile.  I don't know of a system-wide EQ, without some programming.  I would break out the soldering iron, some resistors and capacitors and make a passive filter to handle those bad bass waves.

---

### Post by theller on 2014-01-14
If you are looking for an equilizer for music, I use Clementine <[http://www.clementine-player.org/downloads](http://www.clementine-player.org/downloads)>. It is a crossplatform music player and under the tools menu there is an equilizer.

---

### Post by Frogs Hair on 2014-01-14
I have been using the pulse eq since 9.10 . I find the rock setting a good starting point . [http://www.webupd8.org/2013/10/system-wide-pulseaudio-equalizer.html](http://www.webupd8.org/2013/10/system-wide-pulseaudio-equalizer.html)

---

### Post by Richard_York on 2014-01-14
Thanks for these replies.

> **Frogs Hair said:**
> I have been using the pulse eq since 9.10 . I find the rock setting a good starting point . [http://www.webupd8.org/2013/10/system-wide-pulseaudio-equalizer.html](http://www.webupd8.org/2013/10/system-wide-pulseaudio-equalizer.html)
  I tried installing as instructions on the page. I confess I don't know what most of them mean, but faithfully copied them into the terminal :-)
Got as far as step 4 when it returned with 
"E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed."

I don't understand much of this either, but it's clear it's not going any further.

Any words of advice would be welcome!

Thanks,
Richard

---

### Post by Frogs Hair on 2014-01-14
The first three commands should be run one by one pressing enter after each . The first adds the software repository, the second updates the package system, and the last installs the equalizer. Then search for it in dash to enable it and there are presets available as I wrote Rock is good starting point. . The other commands are only to be used if you encounter problems as described on the web page.

---

### Post by ant2 on 2014-01-14
I noticed the Equaliser in Frogs Hair's post is no longer being developed and whilst stumbling around found this post [http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html](http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html) which helps with enabling Pulseaudio's built in equaliser.

I can't claim to have tried this myself but I thought you may be interested in having a read through.

---

### Post by Frogs Hair on 2014-01-14
> **ant2 said:**
> I noticed the Equaliser in Frogs Hair's post is no longer being developed and whilst stumbling around found this post [http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html](http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html) which helps with enabling Pulseaudio's built in equaliser.

I can't claim to have tried this myself but I thought you may be interested in having a read through.


This  version of the application in  posted link is below  is maintained by Webupd8 for each new Ubuntu version . The variation above is very difficult to work with and I have installed before.

[http://www.webupd8.org/2013/10/system-wide-pulseaudio-equalizer.html](http://www.webupd8.org/2013/10/system-wide-pulseaudio-equalizer.html)

---

### Post by ant2 on 2014-01-14
Thanks for the information Frogs Hair.

I should have read the first two sentences in the link you gave more carefully ;)

---

