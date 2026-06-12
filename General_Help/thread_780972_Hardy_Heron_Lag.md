---
title: "Hardy Heron Lag"
date: 2008-05-03
forum: General Help
---

### Post by raddmadd on 2008-05-03
As the title says.

I tried disabling Compiz, but I still get the lag.  7.10 worked just fine, with the Compiz Effects, too.

It's mostly when I scroll up and down in applications, and it's very noticeable in Firefox (I downloaded Firefox 2, because 3 was really bad.  But 2 still lags, whereas it didn't in 7.10)

Any ideas?

It's mostly Firefox, but why wouldn't it lag in Firefox 2 for 7.10, and lag in 8.03?  The system loads up just as it used to.  Except when I see the usplash screen, the cursor goes back and forth for a second, but not very long.

Anyone ever go to Myspace Profiles, and recognize the lag?  I figured out that it was the CSS transparency scripts.  But if you recognize that lag, that is what I get on every site I go to.  Just not as bad.  This seems like a slight issue, because everything else works out fine (besides that sudo error, but I plan to have a look at the workaround later)

Hardware info:
processor... AMD Athlon(tm) 64 Processor 3700+
graphics card... ATI Radeon XPRESS 200 5954
RAM... 946 (MiB)

---

### Post by grogger13 on 2008-05-03
i get the same stuff, with the scrolling, it used to do that pre-hardy before i enabled the proper drivers, but now i have them installed properly and it doesn't is choppy on alot of different things

---

### Post by LorisMaria on 2008-05-03
> **grogger13 said:**
> i get the same stuff, with the scrolling, it used to do that pre-hardy before i enabled the proper drivers, but now i have them installed properly and it doesn't is choppy on alot of different things

Hi!
What do you mean by proper drivers? I know you're talking pre-hardy, but is there anything I might be able to do regarding drivers? I have the most vanilla upgrade of hardy, and I'm getting the lag issue too. I never had these problems with Gutsy, and I don't even use effects, because my hardware is crappy.

---

### Post by fragos on 2008-05-03
If you have less than 512kb a memory upgrade may be in order. This is particularly true if you onlt have 256kb.

---

### Post by raddmadd on 2008-05-04
Thank you for the replies.

When I log into failsafe Gnome, it works just fine.  How come?  (I removed Compiz, still lags in Gnome.  So it wouldn't be that)  How do I get it to work for when I log into Gnome regularly?

---

### Post by NightwishFan on 2008-05-04
400-500mb is needed to enjoy Hardy. Other than that try a lighter distro like sexy Debian, although you might be in for a rough ride with that if you are newer to Linux.

Show us your:
```
free -m
```
Also if you note something like firefox using too much cpu.

---

### Post by raddmadd on 2008-05-04
> **NightwishFan said:**
> 400-500mb is needed to enjoy Hardy. Other than that try a lighter distro like sexy Debian, although you might be in for a rough ride with that if you are newer to Linux.

Show us your:
```
free -m
```
Also if you note something like firefox using too much cpu.

here ya go:

```

             total       used       free     shared    buffers     cached
Mem:           946        703        242          0         32        344
-/+ buffers/cache:        327        619
Swap:         2768          0       2768

```

If it works fine in failsafe mode, then does that mean a startup script is causing this lag?

---

### Post by MasterNetra on 2008-05-04
You could always migrate to Kubuntu. :) I did and its doing great save for a issue i am having in finding a way to make perm changes to Touchpad settings...for now i have to settle for session lasting changes through synclient... oh well Kubuntu runs nicely. For me anyway.

---

### Post by NightwishFan on 2008-05-04
Your usage is fine, I would assume it may be something of this sort try disabling all the unneeded startup programs and services, and see if that helps any. Also make sure to check the cd you installed with for errors, I have installed with bad cds before and have gotten slow speeds because of it.

+1 For Kubuntu.

---

### Post by raddmadd on 2008-05-04
Thanks for the replies guys.

I did uncheck all the unnecessary services, which is in the system menu.  It didn't do anything.  Does failsafe Gnome prevent any other services from loading up?

I mean, what is the difference between Gnome and failsafe Gnome anyways?  I'm just gonna keep logging into failsafe Gnome haha.

I installed by downloading the files, by the way.  I had 7.10 installed.  

I may look more into KDE.  But I'm used to Gnome and like it.

---

### Post by rumfoord on 2008-05-04
I'm not sure what you mean by lag here, but since installing Hardy I have had jerky video on dvd playback and video streaming (fullscreen; small windows are fine), which I have assumed up to now is related to the video drivers. I have an ATI Radeon Xpress 200 in my Dell Vostro 1000 laptop, and when installing 8.04 it told me that it was using new restricted drivers. I haven't sorted this out yet, and would appreciate any input as the drivers may not be the problem; then again, this could be the same issue you have...
R

---

### Post by hoosiercub on 2008-09-18
I'm very new to Ubuntu and Linux in general as well.. I tried Ubuntu back in the 6.xx release on this laptop with no avail and gave it another shot since I haven't a use for the laptop anymore.. first off.. Hardy Heron is great, I'm very proud of myself for making everything work, shortfall of the problem discussed here in this thread.. full screen video is choppy, including screensavers. 

I'm running 8.04 on a Toshiba A135 Satellite w/ Intel 1.73Ghz, 1GB, ATI Radeon Xpress 200M.. using the restricted drivers and everything works fine.. but the lag is annoying.

Another issue that might be similarly related to this.. I installed 8.04 on an old P4 Celeron desktop, everything worked great, runs smooth and dandy, but I installed Starcraft with Wine and it ran great, but i put off the 125MB update right after you install Hardy Heron, and it ran fine before, but now it runs like crap windowed or fullscreen. Not sure on the specs of the desktop.

---

