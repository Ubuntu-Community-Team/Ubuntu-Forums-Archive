---
title: "Screen tearing with Nvidia GT440 + Chrome + Netflix"
date: 2014-10-23
forum: General Help
---

### Post by Roasted on 2014-10-23
Hello friends. My HTPC on 14.04 is running a G620 with an Nvidia GT440. I tried both the open source and proprietary drivers, but same deal. In comparison, XBMC works fine with no issues. It's just Chrome/Netflix that it happens on.

On a hunch, I pulled the GT440 out of the HTPC and just ran with the onboard video. Once I disabled background blur on the dash using the tweak tool, the HTPC performance was much better, so I just kept running with it. Screen tearing in Netflix is now gone using the Intel onboard card.

Anybody else with Nvidia see this?

EDIT - Despite being back on Intel, I'm kind of a curious person, so I put the GT440 back in with expectation to try the edgers PPA since I saw version 343 (or something) was in there, whereas 331 was the latest available in the main repos. Once I tried to install 343, it looked like it wanted 331-updates (which I tried before where I still had tearing). So I thought, cancel this, let's install 331-updates again, reboot, make sure we have tearing, if so, try 343, reboot, and see if tearing exists then. Once I reinstalled 331-updates and rebooted, I couldn't see any screen tearing... I was kind of surprised actually, as I thought for sure I'd see some tearing as I had before. At any rate, it's not appearing as if I have any tearing on the GT440 now, despite not trying the 343 drivers from the edgers PPA. That said, I went back to my original setup, G620 processor with video out, simple setup, works fine, over and done. Despite this, I'm still curious if anybody else has seen anything like this. Anybody seeing screen tearing on Nvidia setups with 14.04? Anybody specifically seeing tearing on Netflix, but not with something like XBMC? Even though things seem fine now, I still find myself curious to ask.

---

### Post by Roasted on 2014-10-24
Still has me wondering... anybody?

---

### Post by trizt4n on 2015-01-18
I am also experiencing strong tearing issues with **chrome + netflix + nvidia**-proprietary-drivers on **Ubuntu 14.10**, despite of a different graphics card model: **GT 750M **in my case.

I didn't yet try the open nvidia drivers or integrated intel graphics - so I can't tell if that helps in this case.

**@Roasted**: Do you recall what made it work for you with the proprietary drivers? Thanks for sharing. ;-)

---

### Post by Roasted on 2015-01-18
I'm not sure, to be honest with you. After reading over my edited post I do recall trying the 331-updates again and it working fine. I don't know if there was an update that fixed it or what. Do you know if sync to vblank is enabled? If I recall that's often been something that users look at to fix screen tearing. It's in the graphic driver control panel with Nvidia's proprietary updates. The screenshot in this link has a quick shot of what that utility looks like. Hope this helps!

[http://askubuntu.com/questions/479352/screen-tearing-only-when-playing-videos-using-geforce-gt-750m](http://askubuntu.com/questions/479352/screen-tearing-only-when-playing-videos-using-geforce-gt-750m)

---

### Post by trizt4n on 2015-01-18
Thanks for your tips. ;-)

I had some serious trouble with "331-updates", so I removed it again.

It seems as if VSync is OFF: If I run glxgears it gives me more than 3000 FPS. With VSync I would expect only 60. (way above my monitors rate. I am also experiencing tearing in Videos:
[https://www.youtube.com/watch?v=22ftfoCSPQI](https://www.youtube.com/watch?v=22ftfoCSPQI). It doesn't matter if I watch it in a browser or download it.

I checked on nvidia-settings as you suggested, however I don't have this "Sync to VBlank" in the OpenGL Settings Screen (kind of strange..?). "Allow Flipping" is also missing, but otherwise it looks the same.

I tried to do it manually (without luck again):
echo "0/SyncToVBlank=1" >> ~/.nvidia-settings-rc
nvidia-settings --load-config-only

Do you know where to enable it?
I also read something about "triple-buffering" which heals the performance penalty usually involved with vsync at the expense of slightly more RAM-usage. It is supposed to be setup in xorg.conf - but this file seems to be reset each time I restart the X server. Is that normal (some auto-configuration magic happening)? Where do I put this setting instead?

I spent quite some time googling for solutions without luck so far.

---

### Post by rob144 on 2015-08-23
> **trizt4n said:**
> Thanks for your tips. ;-)

I had some serious trouble with "331-updates", so I removed it again.

It seems as if VSync is OFF: If I run glxgears it gives me more than 3000 FPS. With VSync I would expect only 60. (way above my monitors rate. I am also experiencing tearing in Videos:
[https://www.youtube.com/watch?v=22ftfoCSPQI](https://www.youtube.com/watch?v=22ftfoCSPQI). It doesn't matter if I watch it in a browser or download it.

I checked on nvidia-settings as you suggested, however I don't have this "Sync to VBlank" in the OpenGL Settings Screen (kind of strange..?). "Allow Flipping" is also missing, but otherwise it looks the same.

I tried to do it manually (without luck again):
echo "0/SyncToVBlank=1" >> ~/.nvidia-settings-rc
nvidia-settings --load-config-only

Do you know where to enable it?
I also read something about "triple-buffering" which heals the performance penalty usually involved with vsync at the expense of slightly more RAM-usage. It is supposed to be setup in xorg.conf - but this file seems to be reset each time I restart the X server. Is that normal (some auto-configuration magic happening)? Where do I put this setting instead?

I spent quite some time googling for solutions without luck so far.

Ready for this???? This is the fix. and it's amazing. Turns out the problem isnt specifically with Chrome, it's Compiz. This took five minutes and ended my constant tail chasing enabling hardware bs flags. Just had install [COLOR=#000305][FONT=Trebuchet MS]CompizConfig Settings Manager[/FONT][/COLOR] , and add the flags he mentions. 

[http://blog.lxgr.net/posts/2015/04/27/chrome-linux-vsync/](http://blog.lxgr.net/posts/2015/04/27/chrome-linux-vsync/)

Problem. Fixed.

---

### Post by trizt4n on 2015-08-23
Hi rob, glad you shared your solution. :-)

I am not running compiz, but 'mutter' (on ubuntu gnome 15.04 with lightdm). And I have tearing regardless of fullscreen or not - and not only in chrome, but also firefox and video players... Still searching for a solution. Anyone else with similar issues?

---

