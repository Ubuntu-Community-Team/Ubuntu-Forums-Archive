---
title: "Ubuntu 16.04/17.04 screening tearing"
date: 2017-05-15
forum: General Help
---

### Post by olaf.jorgensen on 2017-05-15
A few weeks ago i went from Windows 10 to try out Linux again, games and everything are working Great exept terrible TERRIBLE screen tearing.  I used a week to try to fix it. But in the end i went back to windows. Do anyone have a working guide for it? I read some where that xorg  1.19 would fix it. Well it did not help. Can someone help  me?  Iam  running a laptop with Geforce gtx960m

---

### Post by mc4man on 2017-05-15
I can help you with some info, if you are very self motivated I could point you as how to get tear free in 16.04 (maybe, doesn't always work.
Otherwise, 
1. Yes,  xserver 1.19.x has Prime Synchronization & eliminates tearing while using nvidia drivers
2. Prime Synchronization cannot be enabled for 99.99% of Ubuntu users, apparently Ubuntu (Canonical) could care less so getting this fixed will hinge on happenstance (it was working here on 17.10 UbuntuGnome for me for about a week or so, now it's again not possible
3. There are other distros where Prime Synchronization does work, if inclined do some searching
4. Other than playing some games the Intel iGPU performs as well or sometimes better than nvidia & has no tearing (though you did mention games..

---

### Post by olaf.jorgensen on 2017-05-15
I love Ubuntu but the screen tearing have me moving away from it, i would appreciate the help!

---

### Post by mc4man on 2017-05-16
> **olaf.jorgensen said:**
> I love Ubuntu but the screen tearing have me moving away from it, i would appreciate the help!
1st. let me lay out the theory, what needs to be done & some caveats. If you wish to proceed I'd need to remember or figure out best path to eliminate possible initial issues (generally that is whether to set up while on nvidia or intel & whether to reboot or log out/in on 1st. setup.

Simplistically on optimus hardware  Intel handles the display & if in use nvidia handles the rendering. So most, if not all, tearing can be eliminated by having Intel use SNA & TearFree on the display while nvidia is doing the rendering.
This was a piece of cake in 14.04 however in 15.10 a mesa issue developed  that caused such a setup to boot to an apparent black screen. 
(- actually boot & login were/could be normal, just no visible display. One could login blindly, open a terminal, run commands ect.

So the solution was to let the machine (display) go to sleep, upon waking up all was fine for that session. The default timeout is 300 sec.'s so not a great solution.

When presented with this bug Ubuntu decided to just eliminate SNA for Intel while using nvidia drivers & go to modesetting. This is ok but with modesetting there is no TearFree option possible so eliminating tearing was not possible in 15.10+ thru above method.

Here I've modified 16.04's ubuntu-drivers-common package to use SNA & not modesetting, it is in a personal use ppa. That ppa isn't really suitable to be used by others as it contains specific to me changes to several packages. However one could download & install the ubuntu-drivers-common package itself.

Additionally you'd need to resolve this mesa issue, timeout solution. This is best done by editing the unity-greeeter schema, set it's timeout to like 3 sec & recompile the schema. So once setup you'd boot up, go to the greeter & do nothing for 3+ sec. (- it's quite important not to do anything for those 3+ sec's
Then any mouse or keyboard activity would wake up the screen & after login you'd be tear free or pretty much so. Depending on mesa version there could be very minor tearing in fullscreen video when the cursor is moved. Whether that affect games no idea. Somewhere on the mesa update trail from 11.x to 17.x it was fixed, it now is back in 17.x,  though for me, (videos in fullscreen ),  it's a non issue as no need to move the cursor wildly about.

Screenshot illustrates what all of this causes as seen in in the Xorg0 log. so if inclined I'd retest procedure & lay out specifics.
Note that this is currently on a 755m/Haswell. I do have a 960m/Skylake but it's currently on loan to someone who needs a laptop with win10 so not in position to say if there are issues. If in fact there are any of these changes are relatively easy to revert.

---

