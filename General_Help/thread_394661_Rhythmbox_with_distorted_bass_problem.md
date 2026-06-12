---
title: "Rhythmbox with distorted bass problem"
date: 2007-03-27
forum: General Help
---

### Post by regomodo on 2007-03-27
**_Solved. See last post for solution if you have the same problem._**

I'm having a problem with Rhythmbox.

When i play mp3s with it, my speakers have a distorted, overdriven sound to the bass. I thought it may have been the track but when i play with others (foobar, winamp, wmp, mplayer) the problem doesn't exist.

Is there an equaliser within Rhythmbox as it sounds like the sub25hz slide is jacked right up?

i have had this problem in the past. it was due to the volume mixer (alsa i guess). I cured that by keeping the volume sliders away from 100%. Think that happened with Ark linux. However, that doesn't work in Ubuntu

Any help would be appreciated

Cheers

---

### Post by regomodo on 2007-03-28
Seriously, no one knows whats wrong? 
This is a very annoying problem. Just got used to Rhythmbox and don't want to try something else.

---

### Post by Spr0k3t on 2007-03-28
Have you tried any other music player in Linux outside of Rythmbox?  Removing the OS element from the test will help isolate the issue.

---

### Post by regomodo on 2007-03-28
*"when i play with others (foobar, winamp, wmp, mplayer) the problem doesn't exist."*

---

### Post by Spr0k3t on 2007-03-28
> **regomodo said:**
> *"when i play with others (foobar, winamp, wmp, mplayer) the problem doesn't exist."*

And... what about other LINUX media players?  All of those are windows based.

My bad, I just noticed mplayer... hmm... chalk it up to the wonderful world of Rythmbox?  Have you tried exaile?

---

### Post by regomodo on 2007-03-28
Thats ok. I should have added Amarok to the list but i don't want to use it as it's too bloated for my liking. I'll try exaile. I'm starting to find more songs that do exactly the same thing and it's getting annoying.

I'd much prefer to use Rhythmbox but meh, i'll post what i find.

---

### Post by regomodo on 2007-04-01
Hmm. Tried exaile. Does exactly the same thing. Plus, i don't like the fact that when you double click on an album it doesn't play it instantly. You have to add it to a playlist.

I double checked with other players installed on Ubuntu (VLC, Mplayer and Movieplayer) and there is no problem. Sounds fine.

Sod it. Doesn't matter much. I'm finding myself using XP more and more.

EDIT : grr! Finding more and more songs exhibiting the same problem. My "the Chronic" album has low end distortion although not as bad as it can be. Is this a driver problem?

---

### Post by regomodo on 2007-04-04
Could this be a codec problem?

I used Automatix to install the codecs for audio (among other things). I've checked to see if liblame is installed (it is) but was also wondering if there is a conflict?

I've tried to install foobar2000 in WINE. It installed, wouldn't play any songs despite finding them.

Tried Itunes through WINE but that crapped out after install and blackscreened me.

Anyone? I think this may be the thing that pushes me over the top!

---

### Post by mgmiller on 2007-04-04
Have you tried amarok?  I know it's KDE, but you can install it in Gnome and  it has a 10 band  equalizer.  It will install all the needed KDE dependencies automatically through synaptic or apt-get.  A lot of people swear by this app for their audio libraries.

Here is a link to the features page:
[http://amarok.kde.org/features]("http://amarok.kde.org/features")

Remember, if you want it, use synaptic or apt-get to install it, so all the libraries and dependencies are correctly met.  Do not download and install the version from the amarok website.

---

### Post by regomodo on 2007-04-04
Wow! I forgot what happens when i use Amarok on my computer.

I used synaptic (as always) to install rhythmbox. Ran it and gave it the directory of my mp3s (60GB) using sqlite.

Holymoly! my computer locks up. RAM, swap, and cpu max out. I leave it to it and it appears amarok gets stuck at 71%. t just maxes out everything for ~10minutes then seems to reset everything (RAM, swap, and cpu) and starts all over again. I left it for about 30mins.

Rhythmbox and foobar take ~2minutes to find everything. Needless to say i shall be doing a complete removal. Last week i thought i killed my comp by using Amarok so i reinstalled Ubuntu.

I have a sempron 3100+ oc'd to 2.1GHZ, 2GB of RAM and 500MB of swap. I'm certain there's no problem there.

I did check to see if the distortion is my speakers so i connected my headphones straight to the output jack of the soundcard. Does exactly the same thing. A low end waffle noise in the left ear.

This is weird.

EDIT : btw. I had mentioned i had tried Amarok before but i thought i'd try again as i'm out of ideas and have not gotten a solution so far

---

### Post by regomodo on 2007-04-07
**FIXED**


I haven't pinpointed the root problem but i have solved the problem.

I re-installed Ubuntu Edgy but i did not use **Automatix 2** to install multimedia codecs. I used the Ubuntu Edgy guide to do it instead. So far no problems other than Amarok eating my computer every time i load it. I'm sticking with Rhythmbox

**EDIT**: Most definetly Automatix and its "multimedia codec" install option. Did it on a Xubuntu install and it did exactly the same damn thing. No way to uninstall so reinsall was needed

**EDIT #2**: Found the offending package. _gstreamer0.10-fluendo-mp3_. It's the only codec i installed (that worked) and creates the horible sound. Used Automatix to install the codecs then removed the bad one in synaptic.

**EDIT #3**: I have just discovered _iLinux_ installs the same codec and, once again, the problems appeared again. Removed the crappy codec and all is well

---

### Post by eXcentra on 2007-04-08
Argh! Thanks for find out what was wrong!
I noticed this problem as well and assumed it to be a gstreamer problem (but I never bothered to check it out... since foobar under wine doesn't have that sound problem..)
Thanks. :D

---

### Post by CocoAUS on 2007-04-08
I've been having this problem with VLC for the longest time now.  All the other players work wonderfully, though.  Wonder what the deal is?

---

### Post by regomodo on 2007-04-08
I hadn't noticed it in VLC (i thought it used it's own codec?)

Have you tried removing the codec mentioned above in synaptic?

---

