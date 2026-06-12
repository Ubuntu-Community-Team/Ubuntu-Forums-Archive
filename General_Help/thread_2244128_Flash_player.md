---
title: "Flash player"
date: 2014-09-13
forum: General Help
---

### Post by sillyboy on 2014-09-13
Hello all,

I just tried to watch a video, and it froze.  Then a message came up that asked if I wanted to send a crash report.  I did.  I right clicked on the video and it reported that I was using AFP v 15.0.0.152.  I checked with Adobe and sure enough, it said I had v 15.0.0.152 installed.  How did this get installed again??

I understand that AFP v 11.2.202.406 is the last supported version.

Question is:  What do I need to view videos (not ones on YouTube, they work) online?   What do I need to get rid of in my Plugins?  Flash Player 11.2.202.406 is in my list of Plugins. 

BTW, the videos on YouTube are AFP 15.0.0.152 and I can watch them.  HELP!  I hope someone can understand this...:confused:

Thanks in advance

---

### Post by deadflowr on 2014-09-13
Which browser?
Firefox or Chrome (or other)?

Chrome comes with version 15.XXX + (+ meaning it'll get an even higher version)
It is built into chrome and updates whenever chrome updates.
Firefox only uses whatever version you can install on Ubuntu, that being 11.2XXX.

---

### Post by sillyboy on 2014-09-14
Hi deadflowr,

I am using Firefox.  I installed Chrome the other day and all videos were working well, then yesterday, videos other than those on YouTube, were not playing right.

Should I uninstall Chrome, and see what happens? 

Thank You

---

### Post by sillyboy on 2014-09-14
I un-installed Chrome.   When going to watch a video, other than YouTube, I get the message: failed to load, "libpepflashplayer.so".

How do I properly in stall libpepflashplayer.so?

Thank You All

---

### Post by sillyboy on 2014-09-15
Hello................has this thread ended????  Should I start a new one???

---

### Post by yancek on 2014-09-15
Take a look at the google site below to install the plugin.

[https://support.google.com/chrome/answer/108086?hl=en](https://support.google.com/chrome/answer/108086?hl=en)

---

### Post by mörgæs on 2014-09-15
> **sillyboy said:**
> Should I start a new one?
Only for a new topic, else please stick to an existing thread.

---

### Post by sillyboy on 2014-09-20
Using latest version of Firefox

Still having problems on some sites viewing videos...like, CBS.com/survivor.  Videos on you Tube work fine so far.  When I try to view a video from that site I get the message "Please install Adobe Flash Player".
I reinstalled AFP thru the terminal, went to Ubuntu Software Center, and it shows as installed now.  Back to CBS.com/survivor video, still displays "Please install Adobe Flash Player".

In my plugin list it shows that Shockwave Flash v11.2.202.406 is disabled and Shockwave Flash v13.1.2.3 is disabled.If I enable one of these the videos will play but are lagging badly and the video is unwatchable.  Audio is good though

All my videos worked good a month ago.    I don't know how Shockwave Flash 11 and 13 got into my plug in list.  :confused:

I need some easy to follow directions to solve this issue.

Thank You All for the past help...

SB

---

### Post by mörgæs on 2014-09-21
What happens if you reinstall Chrome?

---

### Post by sillyboy on 2014-09-21
I reinstalled Chrome...Same message "Please install AFP to view this video." 

Any other suggestions???  

Thanks for the help

---

### Post by Frogs Hair on 2014-09-21
Google Chrome includes Pepper Flash and Chromium from the repository doesn't . If using Chromium then the following package would be required.
```
sudo apt-get install pepperflashplugin-nonfree
``` Google Chrome is based on the Chromium open source project and if you have installed Google Chrome from the website the package wouldn't be needed. Keep in mind that extensions such as adblock can interfere with video playback.

I have tested the survivor videos with Firefox running Ghostery and they all seem to be playing though I haven't viewed them all. 

 [https://www.google.com/chrome/browser/](https://www.google.com/chrome/browser/)

---

