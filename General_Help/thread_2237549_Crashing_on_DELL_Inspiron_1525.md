---
title: "Crashing on DELL Inspiron 1525"
date: 2014-08-02
forum: General Help
---

### Post by Niemil on 2014-08-02
Hey, I wanted to try out the ubuntu 14.04 LTS and thought that I can use it on one of my old laptop I use time to time.
The computer is a DELL inspiron 1525 that I been testing Ubuntu 12.04 on for over a half year ago, but then I been running Windows 7 on it due some applications that Ubuntu nor wine could run correctly.
Now I don't need those applications anymore as I just surfing on internet mostly and will start learn programming.

I've installed the Ubuntu 14.04 version on the computer and when I go on Firefox and go to google.com/chrome to download google chrome, the computer tries to load the website and it's white in 5 seconds in firefox webbrowser, then suddenly the whole computer screen turns black.
the blue light buttons on the computer is still blinking, so computer is on, but screen is total black.

Anybody who might know fix to this issue? I guess it may be hardware issue or?
It's the 32 bit version of Ubuntu I installed.

thanks in advance!

---

### Post by grier-devon on 2014-08-02
Does this only happen when trying to get chrome on the machine? If so must be the open source gods hinting to stay away from proprietary software, just kidding. If that is the only time it happens I could not imagine why, a quick solution would be to just install Chromium from the store, make sure to click on "more info" first and scroll down and place a check mark in the box for the pepper plugin. The only difference from chromium and chrome is chromium does not have a built in pdf viewer, but in my opinion it is silly to base a web browser decision of it ships with that or not and in my experience for some reason chromium loads pages faster then chrome.

---

### Post by Niemil on 2014-08-02
Yes, it was happening only when I were trying to visit the download page of chrome.

I've always prefered chrome since many years back as it felt more light and smooth than Firefox. Firefox in my eyes were more like a huge machingun that loads slower, that surely got lots good addons but is just too slow and takes up space on screen more than Chrome does.
However now after I been using Firefox most of time for today I really enjoy the smooth scroll functionally it have though, maybe that works to use on chrome.


And yes, now I got Chromium, I knew about that software before but wasn't sure about the name, I had searched for Chrome and Google Chrome in the software center but couldn't find anything.
Now going to use chromium :D

Nothing hasn't crashed for me and I been visiting quite lot websites that I visit daily, so I guess it's fine now. I don't dare try visit the google chromes website again in case if it is some problem there that cause the crash so I've to restart the computer.


Anyways, thanks a lot for the tips of chromium! :D

---

### Post by grier-devon on 2014-08-02
Glad to hear, please mark thread as "solved" by clicking on "thread tools".
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by emi3 on 2014-11-12
I don't think this is solved. He just changed his web browser!
I'm with this too. Dell Inspiron 1525 - Ubuntu 14.04LTS. And Chrome crashes when I go to Youtube and try to wacth a video. The screen's turn off but I can still hear the sound.
The reason for choosing Chrome is just to watch 60fps vids.

Anybody?

**EDIT: My solution was to disable hardware acceleration in Chrome settings.**

---

### Post by JoaoMachado on 2014-11-30
I can verify that this appears to be a bug in Ubuntu 14.04 (64bit) and not Chrome or Firefox. I have a Dell D630 with 2.6gHz, 4G memory and a 250GB SSD. The system is a screamer but visiting google.com/chrome will kill the X-server and the systemhas to be shutdown by force. In Ubuntu 14.04, Chrome works but watching videos in UBuntu will eventually cause the same thing.

Did an upgrate to 11.10 and both issues were gone, but Ubuntu 11.10 is full of bugs and I cannot use as a daily driver. I decided to install Elementary OS (which uses Ubuntu 14.04 base) and sure enough, problem is back. 

My Laptop also has a second HDD and I installed 11.04 on it and same issue, deleted 11.04 and installed a fresh 11.10 and both issues were gone.

This is an Ubuntu 14.04 issue for sure!

Sticking with Elementary OS and just avoiding google.com/chrome and not using Chrome for youtube...

---

### Post by mörgæs on 2014-11-30
Did you try the solution mentioned in the post above?

---

