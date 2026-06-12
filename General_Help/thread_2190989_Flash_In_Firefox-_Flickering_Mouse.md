---
title: "Flash In Firefox- Flickering Mouse"
date: 2013-11-30
forum: General Help
---

### Post by sasafrass452 on 2013-11-30
I've just installed 13.10 yesterday, & have everything pretty much set up.... But I've noticed that my mouse flickers sometimes, particularly on webpages with flash embeded. I've tried other mice, but with the same result. Is there a setting to prevent this from happening? Thanx!

---

### Post by grier-devon on 2013-11-30
Honestly I am unsure, I know one thing we all need to be careful for watching is when our Flash Plugin goes belly up (no longer supported). Here in the future Chrome may be the only way to have supported flash. The only way I could think to diagnose the situation would be to install Google Chrome and see if you are having the same problem because if your not then we just know that the plugin for Flash for Firefox is getting to old.

As a side note and you might already know this but Chromium would not work for this experiment because Chromium uses the same Flash Plugin as Firefox, must be actual Google Chrome. If you press forward with this test let me know your results and the best of luck to you.

Also just thought of this, go into your software source and make sure all your drivers are installed.

---

### Post by rackit on 2013-11-30
Check your video driver perhaps. I suspect that this may be the culprit. Check your CPU usage too.

---

### Post by sasafrass452 on 2013-11-30
How do I do that? I also notice that my mouse seems to temporarily disappear every so often....

> **rackit said:**
> Check your video driver perhaps. I suspect that this may be the culprit. Check your CPU usage too.

Didn't Adobe already end Linux support? That's what their website says....

> **grier-devon said:**
> Honestly I am unsure, I know one thing we all need to be careful for watching is when our Flash Plugin goes belly up (no longer supported). Here in the future Chrome may be the only way to have supported flash. The only way I could think to diagnose the situation would be to install Google Chrome and see if you are having the same problem because if your not then we just know that the plugin for Flash for Firefox is getting to old.

As a side note and you might already know this but Chromium would not work for this experiment because Chromium uses the same Flash Plugin as Firefox, must be actual Google Chrome. If you press forward with this test let me know your results and the best of luck to you.

Also just thought of this, go into your software source and make sure all your drivers are installed.

---

### Post by rackit on 2013-11-30
Click the gear in the upper right on your desktop, (assuming you are using unity), click "System Settings", click "Additional Drivers". If there are any additional video drivers for your system, they should appear there. If it's not in use, I usually pick the recommended one.

---

### Post by sasafrass452 on 2013-11-30
It says there's none available.

> **rackit said:**
> Click the gear in the upper right on your desktop, (assuming you are using unity), click "System Settings", click "Additional Drivers". If there are any additional video drivers for your system, they should appear there. If it's not in use, I usually pick the recommended one.

---

### Post by grier-devon on 2013-11-30
> **sasafrass452 said:**
> Didn't Adobe already end Linux support? That's what their website says....

Yes, but the last version of Flash they released is still available to Linux users through the distribution, The last version they made is still working for now but I am assuming that by the end of 2014 it will no longer work with websites. We have been through this before in the past and more then likely will be using nswrapper to run the Windows version of Flash or I know there are some open source versions of Flash which will hopefully be usable by the time Adobe Flash ends.

Google maintains there own version of flash and that is why I said for Native Linux Flash support in the future will only be possible through Chrome.

I do agree with checking your video driver first.

What video card/chip are you running?

---

### Post by sasafrass452 on 2013-11-30
Mobile Intel® GM45 Express Chipset x86/MMX/SSE2

> **grier-devon said:**
> I do agree with checking your video driver first.

What video card/chip are you running?

---

### Post by rackit on 2013-11-30
Then a driver from this method won't do you any good, since there isn't one. :) Like grier-devon suggests, check and see if you have the same issues in Chrome.

---

### Post by grier-devon on 2013-11-30
> **sasafrass452 said:**
> Mobile Intel® GM45 Express Chipset x86/MMX/SSE2

What rackit means to say is that with Intel intergrated GPU the drivers are built into the Linux Kernel by default.

I would try Chrome and see if this fixes your problem cause then we know it is just flash showing it's age, but if you use Chrome and the problem presist I am going to continue to do some digging to see if the 3D acceleration needed from Unity may be to intense for the Intel GM4500 chips. Hopefully someone on here can speak more on the topic of graphics performance needed to run Unity as this is not my area but I will see what I can find.

---

### Post by sasafrass452 on 2013-11-30
I just tried Chrome, & the problem is still there. If the 3D acceleration is too much for my chipset to handle, is it possible to turn it off? I have no need for 3D, anyway....

> **grier-devon said:**
> What rackit means to say is that with Intel intergrated GPU the drivers are built into the Linux Kernel by default.

I would try Chrome and see if this fixes your problem cause then we know it is just flash showing it's age, but if you use Chrome and the problem presist I am going to continue to do some digging to see if the 3D acceleration needed from Unity may be to intense for the Intel GM4500 chips. Hopefully someone on here can speak more on the topic of graphics performance needed to run Unity as this is not my area but I will see what I can find.

---

### Post by grier-devon on 2013-11-30
I believe there is unity 2D which can be found where you login, click on the session area. If I may ask how much ram do you have and what kind of CPU do you have?

---

### Post by sasafrass452 on 2013-12-01
I have 3.8 GB of ram & an Intel® Core™2 Duo CPU P8400 @ 2.26GHz × 2 processor. I'll look for the 2D setting & report back here if I still need help....

> **grier-devon said:**
> I believe there is unity 2D which can be found where you login, click on the session area. If I may ask how much ram do you have and what kind of CPU do you have?

I don't see any 2D option.... Can you please be more specific as to where it is?

> **grier-devon said:**
> I believe there is unity 2D which can be found where you login, click on the session area. If I may ask how much ram do you have and what kind of CPU do you have?

---

### Post by grier-devon on 2013-12-02
Interesting, I guess they have discontinued Unity 2D, did not know. You might be best off using Xubuntu or Bodhi Linux since these do not require heavy 3D acceleration.

---

### Post by sasafrass452 on 2013-12-02
I see.... So, is it possible to turn off the 3D acceleration?

> **grier-devon said:**
> Interesting, I guess they have discontinued Unity 2D, did not know. You might be best off using Xubuntu or Bodhi Linux since these do not require heavy 3D acceleration.

---

### Post by grier-devon on 2013-12-02
No, I am sorry about that. I thought it did but I guess the last version of Ubuntu that supported Unity 2D was Ubuntu 12.10, so the only thing left is to try something like Xubuntu, Bodhi or Lubuntu if you want to to use Ubuntu.

---

### Post by sasafrass452 on 2013-12-02
Well, since I'm just beginning to get used to it, I'd rather not change the OS again for a long time. The flickering mouse is a minor annoyance, but one I'll apparently have to put up with unless a different mouse would work better. I'll report back here with the results....

> **grier-devon said:**
> No, I am sorry about that. I thought it did but I guess the last version of Ubuntu that supported Unity 2D was Ubuntu 12.10, so the only thing left is to try something like Xubuntu, Bodhi or Lubuntu if you want to to use Ubuntu.

Ok, here's an update.... A friend of mine suggests it could be driver related, so I installed "pointing devices" & disabled my touchpad, then I installed "3D acceleration" & disabled the 3D acceleration. But I still have a flickering arrow..... Now what?

---

### Post by raptir on 2013-12-02
It really has nothing to do with your touchpad/mouse or the associated drivers. That just affects the movement, it has nothing to do with the appearance of the cursor.

I'm not sure what you mean by saying that you "installed 3d acceleration." The drivers for your graphics card are open source and are installed along with the system. If you're saying you installed a package related to toggling 3D acceleration it's probably not actually related to your graphics card but is instead a package for toggling 3D acceleration in some other application.

The problem is that the integrated graphics that are coupled with the Core 2 Duo processor just can't handle running Compiz, which is the window manager used by Ubuntu. Xubuntu and Lubuntu are much lighter on the GPU and would mostly likely not run into that issue. The OSes are really identical except for the GUI, so it shouldn't be too difficult a switch.

---

### Post by monkeybrain20122 on 2013-12-02
> **raptir said:**
> 
The problem is that the integrated graphics that are coupled with the Core 2 Duo processor just can't handle running Compiz, which is the window manager used by Ubuntu. Xubuntu and Lubuntu are much lighter on the GPU and would mostly likely not run into that issue. The OSes are really identical except for the GUI, so it shouldn't be too difficult a switch.

Are you sure? His specs look fine for Compiz and Unity. I have run it on weaker systems with no problem. OP's problem is not that Unity is sluggish or doesn't start, but flash fickering which has nothing to do with not having high enough specs for Unity as far as I can tell.

It is a myth  from people with ancient hardware that you have to have a quard-core with 16 g of ram to run unity 3d. It runs fine on most mid level machines made in the last 6 or 7 years. It is not like vista or something.

@OP, 
You can try to upgrade your video drivers via [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
But this one can be a bit risky. Make sure you have ppa-purge installed in case of problems.

---

### Post by raptir on 2013-12-03
> **monkeybrain20122 said:**
> Are you sure? His specs look fine for Compiz and Unity. I have run it on weaker systems with no problem. OP's problem is not that Unity is sluggish or doesn't start, but flash fickering which has nothing to do with not having high enough specs for Unity as far as I can tell.

It is a myth  from people with ancient hardware that you have to have a quard-core with 16 g of ram to run unity 3d. It runs fine on most mid level machines made in the last 6 or 7 years. It is not like vista or something.

@OP, 
You can try to upgrade your video drivers via [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
But this one can be a bit risky. Make sure you have ppa-purge installed in case of problems.

Am I sure? No. But I do know that I had a laptop that used the same graphics chipset and I could not run Unity smoothly. The CPU is plenty powerful, but the open GL support of the old Intel GMA is just not there.

---

### Post by sasafrass452 on 2013-12-03
> **raptir said:**
> It really has nothing to do with your touchpad/mouse or the associated drivers. That just affects the movement, it has nothing to do with the appearance of the cursor.

I'm not sure what you mean by saying that you "installed 3d acceleration." The drivers for your graphics card are open source and are installed along with the system. If you're saying you installed a package related to toggling 3D acceleration it's probably not actually related to your graphics card but is instead a package for toggling 3D acceleration in some other application.

The problem is that the integrated graphics that are coupled with the Core 2 Duo processor just can't handle running Compiz, which is the window manager used by Ubuntu. Xubuntu and Lubuntu are much lighter on the GPU and would mostly likely not run into that issue. The OSes are really identical except for the GUI, so it shouldn't be too difficult a switch.
The package I installed is called "3D Acceleration", & yes, it has the option to turn off 3D acceleration. That's all I know. Whether it's for my video card or just one application as you suggest, I don't have a clue.

As for switching to something else like Lubuntu, I'd rather not do that right now. As I said before, I'm just getting used to Ubuntu, & setting up a new OS all over again is hours of work that I don't want to invest in again for a long time.

> **monkeybrain20122 said:**
> Are you sure? His specs look fine for Compiz and Unity. I have run it on weaker systems with no problem. OP's problem is not that Unity is sluggish or doesn't start, but flash fickering which has nothing to do with not having high enough specs for Unity as far as I can tell.

It is a myth  from people with ancient hardware that you have to have a quard-core with 16 g of ram to run unity 3d. It runs fine on most mid level machines made in the last 6 or 7 years. It is not like vista or something.

@OP, 
You can try to upgrade your video drivers via [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
But this one can be a bit risky. Make sure you have ppa-purge installed in case of problems.
If it's risky, I won't attempt it. I'll take the updates through the proper channels as they come to me.

> **raptir said:**
> Am I sure? No. But I do know that I had a laptop that used the same graphics chipset and I could not run Unity smoothly. The CPU is plenty powerful, but the open GL support of the old Intel GMA is just not there.
Open GL? Hmmm.... Is that used by the flash plugin? Could this be the culpret? I've just noticed Lightspark in the software center. I'll give it a try & see what happens....

---

### Post by monkeybrain20122 on 2013-12-03
> **raptir said:**
> Am I sure? No. But I do know that I had a laptop that used the same graphics chipset and I could not run Unity smoothly. The CPU is plenty powerful, but the open GL support of the old Intel GMA is just not there.

But OP didn't say he could not run unity smoothly, only that there are glitches when running flash. Those are different issues, unity doesn't require flash to run. ;)

---

### Post by monkeybrain20122 on 2013-12-03
> **sasafrass452 said:**
> 

If it's risky, I won't attempt it. I'll take the updates through the proper channels as they come to me.

.
There is no "proper channel" to update video driver in Ubuntu except to update your whole system in April. That's why I recoemmended the ppa.

From the sound of it it seems like a video driver problem. Updating video drvers is always a little risky whatever channel it comes from. I have used xorg-edgers for a few years and it has broken my system may be once and ppa-purge fixed the problem in a few minutes (run "sudo ppa-purge ppa:xorg-edgers/ppa" in the terminal then reboot and update) There is also [https://launchpad.net/~oibaf/+archive/graphics-drivers/](https://launchpad.net/~oibaf/+archive/graphics-drivers/), which may be more or less risky (I am using it now, more risky because even more cutting edge and less because doesn't change xorg version and less to update. edgers never break my system to the point that I cannot boot into the desktop, but oibaf did that twice in Precise, had to get into rescue mode or something to purge the ppa)

To be absolutely safe now I always clone my / partition before updating graphic drivers. In case things go really wrong I can restore things to the previous state in 5-10 minutes.

> 
I've just noticed Lightspark in the software center. I'll give it a try & see what happens.


Yes, a safer way would be to try not to use flash at all, but IMO lightspark (and gnash too) is a total waste of time. it may work for a few test videos on Youtube and that's about it and when it does work, it performs even worse than flash. Since there are many (much better) ways to watch Youtube without flash I cannot see the point of it at all, and it doesn't play most videos even on Youtube.

If you use flash just for a few video sites I suggest viewtube, which is a greasemonkey script that allows you to watch flash videos through mplayer or totem on supported sites (Youtube, vimeo, dailymotion and a few more) instead of flash.[http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011) Install the greasemonkey addon for Firefox and restart FF first before you install it. You can also use it in chrome if you have installed the tampermonkey addon from chrome. 

Also in Firefox go to about:config search for gstreamer and change enable media-gstreamer (or something like that) to "true". This allows you to use html5 instead of flash for sites that support it (vimeo. e.g but viewtube would work for that, or soundcloud which is audio rather than video)

After installing viewtube and turning on gstreamer support in FF, go to tools > addons > plugins, find the entry for shockwave flash and change "always actvate" to "ask to activate", that way you can activate flash on demand and only when you really have to use it (so no need to install flashblock any more, that function is now built in)

---

### Post by sasafrass452 on 2013-12-03
> **monkeybrain20122 said:**
> There is no "proper channel" to update video driver in Ubuntu except to update your whole system in April. That's why I recoemmended the ppa.

From the sound of it it seems like a video driver problem. Updating video drvers is always a little risky whatever channel it comes from. I have used xorg-edgers for a few years and it has broken my system may be once and ppa-purge fixed the problem in a few minutes (run "sudo ppa-purge ppa:xorg-edgers/ppa" in the terminal then reboot and update) There is also [https://launchpad.net/~oibaf/+archive/graphics-drivers/](https://launchpad.net/~oibaf/+archive/graphics-drivers/), which may be more or less risky (I am using it now, more risky because even more cutting edge and less because doesn't change xorg version and less to update. edgers never break my system to the point that I cannot boot into the desktop, but oibaf did that twice in Precise, had to get into rescue mode or something to purge the ppa)

To be absolutely safe now I always clone my / partition before updating graphic drivers. In case things go really wrong I can restore things to the previous state in 5-10 minutes.



Yes, a safer way would be to try not to use flash at all, but IMO lightspark (and gnash too) is a total waste of time. it may work for a few test videos on Youtube and that's about it and when it does work, it performs even worse than flash. Since there are many (much better) ways to watch Youtube without flash I cannot see the point of it at all, and it doesn't play most videos even on Youtube.

If you use flash just for a few video sites I suggest viewtube, which is a greasemonkey script that allows you to watch flash videos through mplayer or totem on supported sites (Youtube, vimeo, dailymotion and a few more) instead of flash.[http://userscripts.org/scripts/show/87011](http://userscripts.org/scripts/show/87011) Install the greasemonkey addon for Firefox and restart FF first before you install it. You can also use it in chrome if you have installed the tampermonkey addon from chrome. 

Also in Firefox go to about:config search for gstreamer and change enable media-gstreamer (or something like that) to "true". This allows you to use html5 instead of flash for sites that support it (vimeo. e.g but viewtube would work for that, or soundcloud which is audio rather than video)

After installing viewtube and turning on gstreamer support in FF, go to tools > addons > plugins, find the entry for shockwave flash and change "always actvate" to "ask to activate", that way you can activate flash on demand and only when you really have to use it (so no need to install flashblock any more, that function is now built in)
Well, I tried the greasemonkey script, & it didn't work. I couldn't get a youtube video to play at all. So, if I have to wait until april for the complete upgrade of Ubuntu, then I guess that's the way it'll have to be. I'm just not comfortable with installing the driver myself....

---

### Post by monkeybrain20122 on 2013-12-03
Which script and in what way that it doesn't work? If you are using Viewtube you may need to change the format (mpeg mp4 auto etc). If you only need Youtube smplayer also has a Youtube viewer.

---

### Post by sasafrass452 on 2013-12-03
Yes, it was viewtube. None of those format options worked.

> **monkeybrain20122 said:**
> Which script and in what way that it doesn't work? If you are using Viewtube you may need to change the format (mpeg mp4 auto etc). If you only need Youtube smplayer also has a Youtube viewer.

---

### Post by monkeybrain20122 on 2013-12-03
This may sound stupid, but did you install Ubuntu restricted extras? Does the script work on vimeo or dailymotion? (use "vlc" option for vimeo) Is it up to date?

---

### Post by sasafrass452 on 2013-12-04
I just installed the restricted extras, but I didn't try the script on vimeo or daily motion, since I don't go to those sites.

> **monkeybrain20122 said:**
> This may sound stupid, but did you install Ubuntu restricted extras? Does the script work on vimeo or dailymotion? (use "vlc" option for vimeo) Is it up to date?

I've just upgraded to Ubuntu 14.04, & I'm still having this issue. I even disabled the flash plugin, & my mouse is still flickering. I see this in chrome as well. So, it seems that flash is not the issue as I thought it was. If anyone has any suggestions, I'd greatly appreciate it!

---

