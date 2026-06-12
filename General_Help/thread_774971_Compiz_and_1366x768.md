---
title: "Compiz and 1366x768"
date: 2008-04-29
forum: General Help
---

### Post by malayaleeking on 2008-04-29
Recently upgraded my Gutsy install to Hardy when my XP side of the box crapped out on me.  I remember being able to use the nvidia drivers in Gutsy and use the desktop effects, but was unable to do it at 1366x768, my native 32 inch LCD TV resolution.

I was surprised when the bundled drivers supported my 1366x768 in Hardy but alas no desktop effect support.  I've tried EnvyNG and it either 1) doesnt get to 1366x768 with desktop effects (lower works) or 2) when forced (xorg.conf) to 1366x768 no desktop effects.

Has anyone been able to get their HDTV and nvidia drivers working @ 1366x768 with the desktop effects?  I've searched and searched but nothing has worked yet.

TIA

Synopsis:
> gutsy to heron, gained 1366x768 (HH) but lost desktop effects (GG)
> 32 inch LCD TV connected with a FX 5200
> can't get 1366x768 and Desktop Effects to work with GG...ever, even using every EnvyNG driver their is

---

### Post by Zorael on 2008-04-29
So now you're on Hardy, right? Right.

What does your **/etc/X11/xorg.conf** file look like? The Hardy version of X does a whole lot more auto-detecting than the Gutsy does, so perhaps it'd solve itself if we let it recreate the file completely.

---

### Post by orthrus7 on 2008-08-28
I'd suggest checking the detected resolutions in the nvidia settings when you have it set to an independent x screen for the next closest one down from 1366x768, or lookup/contact the manufacturer for the true resolution. 1366x768 is often just a standard averaged out while the video card is secretly running the display at it's real hidden resolution. That's why when trying to manually configure to that it fails as 1366x768 is often just what is reported, or used as the label for anything remotely close to that.     

I did struggle getting my HDTV resolution manually setup for days and nights on end with the nvidia drivers on a couple of cards. My 8800 would default to 1366x768  for my HDTV when twin view and or auto detect mode was enabled. The other card I could never enable it , not listed in the nvidia settings as a choice and then when manually entering it in the xorg.config it would default back to 1024x768. After days of struggling with it I disabled the EID mode check and crudely forced it to really out put a resolution of 1366x768 and guess what my display said (blue background with the words "NOT SUPPORTED"):confused:

How ever then I chose 1280x768 as this was the next closest wide screeen resolution down that I could choose manually in the nvidia setting dialog. It worked though it seemed cut off the screen which had made me assume for the longest time that it was lower than the TV's correct max resolution,  until I noticed that the TV's input status was displaying "1366x768 @ 60hz". I Went to the TV's menu and adjusted the horizontal position and size to center the picture  and bang perfect. Ah ha 1366x768  was never in fact the real resolution and so to spite being glad to have it working, much sleep deprived swearing ensued. :mad:

So the fact is that, though the manual for the HDTV and the detailed tech specs as well as it's on screen input dialog and the nvidia drivers under certain circumstances would all say 1366x768, this simply was not technically true. Each HDTV display varies and seems to have a slightly different resolution that they all average out to the standard of 1366x768 so as not to confuse the doe eye'd consumer. It may say everywhere that it is 1366 and the device may print 1366 on the input status window but this is just for your benefit. What it should say is x resolution which is as close as your going to get to 1366x768 so let's just call it that and don't take it back to the store all P.O'd thinking you got ripped off because all the TV's are like this. When configuring the display manually for anything what so ever though you may need to know the actual,non-rounded, possibly undisclosed, real display resolution for that specific model which the manufacture just averages out to 1366x768. In my case it was no where, I mean no where, what so ever, evident. Turns out even the nvidia driver when I was not having to manually set the resolution would just say close enough, and tell me here it is 1366x768 as printed on the box the TV came in. 

Perhaps if you test and find the real resolution and then try that (it's likely close to 1366 but slightly less) and then configure for that it may work.:popcorn:

---

