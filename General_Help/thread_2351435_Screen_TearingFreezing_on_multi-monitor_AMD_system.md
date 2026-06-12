---
title: "Screen Tearing/Freezing on multi-monitor AMD system?"
date: 2017-02-03
forum: General Help
---

### Post by Skillet98 on 2017-02-03
Okay, so I've been having a problem for a while now that basically amounts to extreme screen tearing and random freezing, usually while watching videos. 

I'm pretty sure this has to do with the drivers for AMD (my system is an i5 6600k paired with an R9 390), the fact that I have dual monitors, the fact that my monitors have different resolutions (one is 1080 and the other 900), or any combination of the above. 

When I was running Ubuntu 14.04 originally, I didn't have too many problems. It was stable at first, but eventually ended up slowing down, so I decided to update it. That was apparently a huge mistake because my problems only got worse. Screen tearing started happening after I upgraded from 14.04 to 16.04. On top of that, my system freezes randomly while watching videos and sometimes while moving windows around. Firefox is super bad about this, freezing my system within 5-10 minutes if I start watching youtube videos, so I switched to Chrome which lessens the frequency of freezing, but it still happens. Watching videos using Ubuntu's video player or VLC also causes frequent freezing. When it does this, the system becomes unresponsive for around 10 seconds or so, the screens switch off and then back on, and I can move my cursor on my primary display, but the system is otherwise frozen. If I'm watching a video while this happens, I can still hear the audio for the video playing in the background until the video ends or I turn off my system.

This issue seems to be related to the loss of the fglrx drivers, as those were the drivers I used before these issues started happening. I tried both the default drivers and the proprietary AMD drivers after upgrading to 16.04, but the issue persisted. I eventually tried switching to Fedora, but had the same issue there (should have known, really), and then I went back to 14.04. The problem is that I can't seem to install the fglrx driver on 14.04 anymore... so I guess I'm basically SOL.

Screen tearing seems to be a pretty common issue on AMD GPUs and I've tried many of the things people have suggested to fix it when googling the problem, but none of them work and seem only seemed to make the issue worse. 

So that's my long-winded story... my question is, has anyone here experienced similar issues on a similar system? If so, have you fixed the problem? Would using the newer 16.10 version of Ubuntu, which uses a newer kernal than 16.04, potentially fix the issue?

Thanks.

---

### Post by RobGoss on 2017-02-03
Have you tried using the proprietary drivers provided by Ubuntu?

Post your system specs it will help others give you the best possible answer for your issue.

Have you tried other distributions of Ubuntu preferably lighter versions which might perform better

16.10 is not a LTS release so unless you want to have to upgrade every few months I would stick with 16.04 if it works as it should

---

### Post by dragonfly41 on 2017-02-03
There are some keywords in your opening post which ring a bell from recent research into causes of freezing. 
e.g. you write ...
"update" (14.04 to 16.04 rather than fresh reinstall)
"watching videos"
"youtube"
"freezing"
"AMD"

If you read this recent thread where I threw in some ideas ...

[https://ubuntuforums.org/showthread.php?t=2350902](https://ubuntuforums.org/showthread.php?t=2350902)

you will find similar clues/patterns.

"freezes randomly"
"AMD FX 8320 (8 core @ 3.5 GHz)"
"videos"
"youtube"

Read from about post#29 (earlier posts are not too relevant and didn't work out)

I don't know if that OP actually tried the approach suggested in post#31 since the thread stopped. 
But I suggest that you try it since it is found in quite a number of threads referring to freezing.

The suggestion is to edit the grub line using Grub Customizer.   But do ensure that you backup your grub file and have a means (live USB/CD) to edit changed file back to original if this experiment causes you to fail to boot in.  You have been warned.

All of this is from just comparing clues from different threads.

---

