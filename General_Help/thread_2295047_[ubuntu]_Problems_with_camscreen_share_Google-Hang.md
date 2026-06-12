---
title: "[ubuntu] Problems with cam/screen share Google-Hangouts with both Chrome and Firefox"
date: 2015-09-15
forum: General Help
---

### Post by Dean_MacGregor on 2015-09-15
[COLOR=#111111][FONT=Ubuntu]I recently installed Ubuntu server 14.04 with standard Ubuntu desktop. I used to have Kubuntu 14.04.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]When I had Kubuntu my webcam worked fine without any special driver tweaking. Now I have Ubuntu and when I try to use Google hangouts with my webcam it crashes after a few minutes. (Just the window crashes, not the whole computer)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Here's my lsusb -v for the webcam [http://pastebin.com/LL6S3wUD](http://pastebin.com/LL6S3wUD)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]If I keep the webcam turned off and only use the embedded mic it seems to work fine also with hours of uptime.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The crashes occur in both Chrome and Firefox. I haven't tried other browsers. I have cheese open and although it crashed the first time I opened it, it hasn't crashed since.

I used the screen share on google-hangouts to share my Cheese window and that too prompted a crash.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I have Nvidia Geforce GTX 650 Ti with Nvidia 340.76 driver.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Here's how the crash unfolds: I'll be using the cam and I'll suddenly the audio and video of the people I'm chatting with freezes.  When I look at my system monitor, one of the CPU cores will go to 100%. When I go to the Processes tab and View All Processes I don't see a process that is using more than a trivial amount of CPU%.  If I open a terminal for `top` I still don't see a process taking a lot of CPU.  Despite not knowing what process it is, the mystery process will continue to take up 100% of one core for about a minute or two until the crash window shows up. After I click through the crash window the processors return to normal usage.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Are there any logs I should be looking at or anything obvious that might be causing the problem?[/FONT][/COLOR]

---

