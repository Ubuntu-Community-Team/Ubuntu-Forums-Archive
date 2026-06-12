---
title: "Resolution Problems - Rest. drivers but wont change"
date: 2008-03-05
forum: General Help
---

### Post by grimdeath on 2008-03-05
I had issues with my resolution keeping me from running Ubuntu after my first install. It would stop working after I logged in, I was able to resolve this issue by reconfiguring my x which brought up a "low graphics mode" option and set my resolution to 800x600...after finally getting in I installed the nvidia restricted driver and restarted and was able to change my screen resolution using system > preferences > screen resolution.

Everything was working great last night but when i turned it on this morning I was met with it running at 800x600 again with the restricted driver still set on and the resolution list showing up but not letting me change to them...it would let me click a new resolution and then just nothing would happen, no change.

I went back into reconfirgure x again today and disabled the lower resolutions leaving like 1024x768 as the lowest resolution and 1600x1200 as the highest....well after another restart it seemed to be working, so i turned off and went to work..

Got home this evening and turned back on to discover it running at 1600x1200 resolution and not allowing me to change it again. *pulls out hair* This is usable but makes things a bit too small on my 19" monitor, the 14x10 setting looked really nice when i had it working...what the heck keeps messing up my settings?!

I have tried this command listed on another thread:
```
nvidia-settings
```

This brings up the nvidia controls and I can choose another resolution in the drop down box but when I click apply I get this message:
[http://img177.imageshack.us/my.php?image=ss1eu5.png](http://img177.imageshack.us/my.php?image=ss1eu5.png)
(its a screenshot of a screenshot as my original was not loading to IS properly)

and when i set the refresh rate to something besides automatic i get:
[http://img510.imageshack.us/my.php?image=screenshotqa0.png](http://img510.imageshack.us/my.php?image=screenshotqa0.png)
(sorry dunno why this is sized small, it views full size until loaded to imageshack)

I went back in to get another picture of what happens when I do try to follow these instructions but the resolution change actually WORKED when I hit apply, however the save to X still gives this:
[http://img187.imageshack.us/img187/536/screenshotgw3.png](http://img187.imageshack.us/img187/536/screenshotgw3.png)

Weird issues just while trying to take some dang pictures...wtf!

As for what I might have installed yesterday to cause problems, im not really certain as I was updating a lot of things, compiz fusion seems to jump out as a possible culprit but I would like to be able to keep and use it unless this is going to be a continued issue.

*edit*
im sorry I forgot my system specs:

AMD X2 4200 CPU
EVGA (rebranded Jetway) NF4 SLI edition Motherboard
EVGA 7800gt gpu
2 gb ram
300gb Sata drive (windows)
80gb IDE drive (Ubuntu)

Ive restarted after posting this and the resolution seems to be sticking *crosses fingers* Id still love advice to figure out what the deal is/was.

---

### Post by grimdeath on 2008-03-06
no one?

---

### Post by grimdeath on 2008-03-06
checked again at lunch, same issue it switched back to 1600x1200, used the nvidia settings window to reset back to 1280x1024 and seemed to switch ok...still dunno why this setting wont "stick".

---

### Post by Therion on 2008-03-06
> **grimdeath said:**
> I went back into reconfirgure x again today and disabled the lower resolutions leaving like 1024x768 as the lowest resolution and 1600x1200 as the highest....well after another restart it seemed to be working, so i turned off and went to work..

Got home this evening and turned back on to discover it running at 1600x1200 resolution and not allowing me to change it again. *pulls out hair* This is usable but makes things a bit too small on my 19" monitor...
Go back into/edit xorg.conf and accept all the current settings until you get to the screen where you can choose your resolutions.

Choose whatever you want, but bear in mind that the HIGHEST resolution you choose here will be the new DEFAULT resolution (meaning it should *stick*). 

Save, Exit, Ctrl+Alt+Backspace and see if that solves the problem.

---

### Post by grimdeath on 2008-03-06
thank you, good to know ill give it a try this evening. that sounds like exactly what it is doing. I figured it would default to the smallest resolution instead of largest!

---

### Post by grimdeath on 2008-03-06
well to avoid creating another thread, perhaps I can just tag another issue on here that has to do with resolution.

Ive had two games, Tremulous and ET:Quake Wars that mess up when the resolution is set "too high". In both games when this happens I lose mouse control in the games, the windows show around the edges rather then full screen and occasionally the window blinks to full screen then back to windowed. Tremulous was a pain to get working again, keyboard controls still worked so after much tinkering was able to get in the game, create a server and edit the options to fix it. On ETQW I have not been able to figure out how to fix it as the keyboard buttons dont allow me to get into the options....im looking into a way to set back to default.

The resolutions I was trying for both was 1280x1024, Tremulous worked at 1024x768 but I have not gotten to fix ETQW yet of course to know if that will work for it as well...my main question is what is causing this and is there any fix? I have looked all over the forum and google with no solution.

Here's a screenshot with the mouse stuck in the middle:
[http://img228.imageshack.us/img228/1380/screenshotcf2.png](http://img228.imageshack.us/img228/1380/screenshotcf2.png)

*edit*
problem solved, thanks google, your too kind ;)

> Disabling compiz fixed this for me. Supposedly there is a fix wherein you leave compiz disabled, and go to:
System -> Preferences -> Advanced Desktop Effects Settings -> General Options (Under 'General') and untick 'Unredirect Fullscreen Windows'.

I haven't tried playing with this setting disabled so I can't say if it works or not.

Please post back here with your results if you do try it!

works like a charm!

---

