---
title: "Screen flickers, or &quot;blinks&quot;, but only when loading graphical stuff"
date: 2008-05-02
forum: General Help
---

### Post by evilmike on 2008-05-02
I've been getting this weird problem lately, ever since upgrading to 8.04. So far everything seems to be working perfectly, except for this one minor annoyance.

Basically, whenever I run a program that has some sort of graphical or video capability, my monitor will blink maybe 5 or 6 times. It happens over a period of about 2 or 3 seconds, and each flash seems to be a black screen (though they are so brief that it is really impossible to tell, and sometimes it looks like there is a line or some sort of colour gradient in there). This happens when I play a video file, when I try to play a game, even when I enter Ubuntu's screen resolution menu. After the flashes stop, things seem to work fine. Interestingly, it doesn't happen with EVERY program (eg it never occurs with firefox playing videos on youtube).

I also get similar flashes to this when initially loading the operating system, and then once again after logging in.

To troubleshoot, I reconfigured xorg.conf by running the command for that. I managed to clean up a very cluttered xorg.conf file, but didn't fix the problem I am having. 

Some info that might be relevant: The video card I have is a Radeon X800. The driver I am using is the open source ATI driver. This is exactly the same as what I had with the previous version of ubuntu. I am using an LCD monitor. This is also unchanged. Native resolution is 1280x1024. Under the screen resolution I have the option to set the refresh rate to 60 or 75 hz. I'm leaving it at 60 since it's the default and doesn't really make a difference for LCDs. Both of these settings have the problem I am describing, anyway.

Also, I am having another weird problem. Whenever I shut down or restart, the "Ubuntu" screen with the loading bar is all messed up. The display is all distorted horizontally, like bad tv reception in the middle of a storm or something. Strangely, the corresponding startup screen does not have any problem like that. This might be because I did something with usplash.conf (it was set to 1024x768, which was wrong, so I changed it to my monitor's resolution and ran the command to update the usplash file.) I'm mentioning this problem because maybe the two issues I am having are related.

Neither of these problems are very severe, but I kind of worry that my monitor is going to break or something. It would be nice if I could at least find out what is causing this.

---

### Post by evilmike on 2008-05-10
Bump

I fixed the shutdown problem I mentioned, but I'm still getting the flickering problem. It especially happens when running games with wine, but some other things cause it too. I would really like to know what's causing this. Thanks.

---

