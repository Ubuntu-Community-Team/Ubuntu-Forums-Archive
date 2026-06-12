---
title: "[Video]Firefox Flash Crash"
date: 2007-06-21
forum: General Help
---

### Post by TheVault on 2007-06-21
I got annoyed with how Firefox constantly crashes when I go to sites such as YouTube, MetaCafe, Dailymotion & more. So, I thought I could educate people who might not understand what it means, or may be experiencing and may not know whats going on. I hope this video can educate the developers and possibly find a fix. 

[http://www.youtube.com/watch?v=cY_KrB8Mepg](http://www.youtube.com/watch?v=cY_KrB8Mepg)

Comments/Suggetions welcome :D

---
EDIT: I would like to make another note. I just now turned off beryl and put back everything to normal, and for some reason, firefox is not crashing when I go to youtube and watch videos. I was watching many videos, from beginning to end and then going to another video. I closed the tabs, windows etc and nothing happen.

I'm starting to wonder if the whole flash crash has something to do with Beryl, because its not doing it. If firefox does crash after me turning off beryl, then I can confirm something.

EDIT 2: I have confirmed that its not just beryl. After browsing about 10 different videos, it did finally crash. So maybe beryl speeds it up? I donno, but either way, Firefox crashes when viewing flash.

---

### Post by vexorian on 2007-06-21
It is a tricky issue considering flash doesn't crash firefox like that on most machines... (mine for example)

So post the video in launchpad or bugzilla or whatever bug report site firefox uses if you want to ensure the developers watch it.

---

### Post by galo on 2007-06-22
I also share this problem, and I also feel it's really annoying.
I haven't figured out the conditions in which the crash occurs, but sometimes you can watch a lot of videos on youtube and everything is fine, and other times it crashes a lot of times in a row. 
I've also seen the crash on websites with flash interfaces, so it's not only video sites that use flash that crash.

---

### Post by TheVault on 2007-06-22
Yeah I know. I, along with other users, have searched Google for answers and found some but none of it works. I really hope they find a good fix soon cause its really annoying. Launchpad has many many reports of this, but no cure.

---

### Post by bluemarvel on 2007-06-23
I've had two different installs of Ubuntu Feisty on my HP dv9000 laptop and I've had the same problem. Firefox locks up with videos on YouTube and MySpace, however it seems to happen randomly. To resolve the issue I have to kill the firefox process.

---

### Post by galo on 2007-06-23
I might be wrong but I'm not having crashes after changing my /etc/X11/xorg.conf and commenting these lines, which I think are AIGLX/Beryl related .

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        #Option         "AddARGBVisuals"        "True"
        #Option         "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"  
EndSection

---

### Post by Crafty Kisses on 2007-06-23
I think it's a possible resource issue.

---

### Post by redtrak on 2007-06-24
You wouldn't happen to have a Realtek sound card would you?

---

### Post by fooman on 2007-06-24
try swlftfox.  ;)

---

### Post by mam28 on 2007-06-24
Its onboard sound, Get a pci soundcard problem fixed.:KS

---

### Post by newpants2003 on 2007-07-03
samething for swiftfox.

---

### Post by Tripmonkey_uk on 2007-07-03
Swiftfox is just Firefox with some tweaks. It still uses all the same engine etc. so I'm not surprised it also crashes out :(

I was encountering the same problem with the videos, so I did a reinstall after deleting all the mozilla folders to make sure that it would be a clean install. Still got the same problem on booting the clean install though.

Never had trouble with my onboard sound before, but now I come to think about it.. I have started having problems with my sound not loading up on my laptop. Some times it loads up & works fine, but other times I need to restart my laptop to get the sound working again :(

---

### Post by jwh400 on 2007-07-03
What versions of Firefox and Flash are you using? I had this problem until I upgraded to Firefox 2.0 and Flash 9.

---

### Post by detroit/zero on 2007-07-14
My Swiftfox install does pretty much the same thing. I'm not running Beryl, though; I'm using Compiz Fusion. I never noticed it when I had Beryl Installed.

Over time I've noticed a few things:[LIST]
[*]The browser crashes when any video being played through Flash Player (YouTube, MetaCafe, all the others you mentioned, and then some) is stopped while *the video is still loading.* By "stopped", I mean the browser window or tab is closed, or a different video is selected, or if I simply try to leave the page by clicking a bookmark or typing a URL in the address bar.
[*]The browser will only crash *if the video is still loading*. Once download is complete, the window or tab can be changed or closed with no problems.
[*]If the video is being played in its own tab, it only happens when it's the *first* browser tab or the *last* browser tab. (Don't ask how I figured that one out.)
[*]It never happens twice in a row. For example, If I'm playing a video and stopping it causes a freeze, upon restoring my session and having my window or tabs reload, closing the video before it finishes loading does not  crash the browser again. Trying to stop a different video in a different tab or window will still crash the browser.[/LIST]I hope that gives some tips on where to look and helps someone fix this annoying little bug.

---

### Post by martian742 on 2007-07-20
I also have this problem with my laptop. So how can I solve it by changing soundcard ? Its not so smily solution for me. I think that finding error in software would be better.

NOTE: I am not using anything like beryl and firefox freezes with flash anyway.

---

### Post by zxccvb on 2007-07-28
I have this problem too.

It's pretty annoying, If i don't find a solution i'm basically forced back to win. :(

---

### Post by FuturePilot on 2007-07-28
Same problem here. There's a bug report on Launchpad. 
[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/98688]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/98688")
From my own experiments with this, it's not a Firefox bug, but a bug in the Flash plugin. I've had many other browsers freeze in the same manner. Opera, Swiftfox, Epiphany....
Perhaps we need to start complaining to Adobe about this. Very annoying bug.:(

---

### Post by mt330404 on 2008-06-01
hate to be the redundant guy in all of this, but Im having the same problem as everyone else... i play a flash video, and as it's loading, firefox closes suddenly without any error message or warning-- the whole program just disappears completely. I also find that after playing a flash video through firefox, my entire system becomes MUCH slower. I did the whole flash plugin-nonfree solution, to no success. 

not surprisingly, I find this to be VERY ANNOYING and this needs fixed ASAP if we expect Ubuntu to go mainstream eventually.. this is a bush-league problem....

---

### Post by bapoumba on 2008-06-02
mt330404, this is a year old thread in the archive section. Which ubuntu version are you running ?

---

### Post by mt330404 on 2008-06-02
8.04, using firefox 3.0 beta 5. running on a sony vaio laptop VGN-A150. i never had this problem in Gutsy at all

---

### Post by jbcano on 2008-06-08
Yes, im having the same problem in firefox 3b5 y firefox 3rc2 ubuntu hardy....

Its very uncomfortable but only rerun firefox restore session and works fine for another two or three videos (sometimes works fine all the session)..

I think that is a problem with firefox 3 or hardy because on firefox 2 gusty i dont have any problem...

---

### Post by schnauzer93 on 2008-06-11
So do I. It seemed to work well until i upgraded to RC.

---

### Post by mt330404 on 2008-06-12
> **schnauzer93 said:**
> So do I. It seemed to work well until i upgraded to RC.
yeah my comp hasn't crashed since the installation of firefox 3 yesterday........................................ knock on wood

---

### Post by JD82 on 2008-06-22
The only solution that worked for me (Part A-B):
[http://ubuntuforums.org/showthread.php?p=4928900](http://ubuntuforums.org/showthread.php?p=4928900)

---

