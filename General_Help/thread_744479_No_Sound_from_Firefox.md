---
title: "No Sound from Firefox"
date: 2008-04-03
forum: General Help
---

### Post by jimbo99 on 2008-04-03
Just the other day I was watching videos form youtube.com and other sites with flash based video.  Yesterday I noticed that I am unable to hear any sound coming from any flash based video viewer used through firefox.  

I have tested my Amarok and my VLC.  They play sound.

Any ideas?

---

### Post by esttorhe on 2008-04-03
[color=darkred][b]AMD64 ?
or any 64 processor runninng on a 64 bits ubuntu distro?

Right?

if thats the case is cause there are no official packages for 64bits ubuntu distros for flash and java as stated on the article im quoting next
you'll need to ndiswrapper both[/b][/color]

[quote="Pánisz Péter start64"]There exists no official flash package available for the 64bit architecture with Ubuntu and Kubuntu. If you click the add plugin button when visiting a page with flash, you are taken to the official Flash site and will soon notice that there are no available 64bit downloads here either. There are some workarounds on ubuntu forums, however, they don't always seem to work and get complicated if you have compiled your own 32bit Firefox.

We have been using both the official 64bit Firefox package from the Kubuntu repositories as well as a modified 32bit version I built quite a while ago to get around some stability issues with the 64bit version. So after about a year without flash support, we finally took the plunge and have built a quick and easy solution. Read on to see how you can add Flash and Java support to your 64bit system in under 1 minute. [Update] At the end of the article, you will see how we can install a 32bit version of Firefox.[/quote]
[Article Source](http://www.start64.com/index.php?option=com_content&task=view&id=1852&Itemid=70)

---

### Post by jimbo99 on 2008-04-03
Thanks for trying but I don't think you read my post.

My post indicated that it was working and then all of the sudden it stopped.  Maybe due to some update that occurred these past few days.

I have 7.10 installed and it has been working.  I've been running ubuntu on this box for almost 2 years.

I can play the youtube videos. There's no sound.  I can play normal music with Amarok.  There is sound.

I'm trying to get a solution for why my firefox just stopped playing sounds.

---

### Post by dlbrando on 2008-04-03
I have the video but I have never had the sound.  What would using ndiswrapper entail, I am already using it to run my wireless

---

### Post by the_analyzer on 2008-04-04
I have the same problem, 
Whats going wrong with this linux?

---

### Post by ed-koala on 2008-04-04
I'm not sure what's happening, but folks, you're in for good news!  The new Hardy release coming has a quick and easy way to get Flash with 64 bit people.   I installed the Beta yesterday and Flash works perfectly.

Don't give up hope, the light is very close to the end of the tunnel.

---

### Post by jimbo99 on 2008-04-04
Mine worked.  Only recently, within the past week or so did I loose sound.  I've had a good stable desktop for 2 years.  I don't techy geeky screw with things.  I just use the damn thing the way anyone would use an OS (any OS, say the Mac or that awful windows).  Linux just works for me, does everything I want.

But something has happened and I can't get sound any longer in firefox, but I get sound in other programs.

---

### Post by esttorhe on 2008-04-06
just upgraded to beta 5 and everything is working fine, now i do have fine flash video and audio also :)

---

### Post by Crafty Kisses on 2008-04-06
Post the following output:
```
lspci
```

---

### Post by jimbo99 on 2008-04-07
Certainly help is nice but this is Ubuntu.  Command line programs to get you output is not really appropriated.  You must think and consider the human being in the equation.  Please find another way to ask for the information.

But again, another person failed to read the postings.  The postings indicated that sound works.  lspci will list the hardware.  Sound works.  So lspci is not important.  This is an issue having nothing to do with lspci, and if it does then something more deep is wrong.

I managed to work out some issues with this.  Though other issues have cropped up as a result.

In Ubuntu 7.10 I installed pulse audio via a guide I found on the web.  That helped clear up some issues but cause others.   In that guide is a reference to the fact that pulse audio and flash have problems in firefox, specifically dealing with audio.  They reference a .deb file that can be downloaded and installed to help correct the problem.  I did this.  Sound now works, but....one issue is that I can now hear sound in youtube videos again, but most of those videos will crash the browser a couple times before i get it to play.

I'm at the point now where I installed beta 5 of Firefox and it also has the same nasty crash issues but it seems less frequent.  I have just installed the flash from adobe.com and will let you know how it pans out.

---

### Post by jimbo99 on 2008-04-07
This is the guide:

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

---

