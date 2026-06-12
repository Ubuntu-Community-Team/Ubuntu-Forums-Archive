---
title: "Problem with videos and music"
date: 2013-09-25
forum: General Help
---

### Post by scott_Henderson on 2013-09-25
Hey everyone. I just installed Ubuntu 13.04 last night. This is my first ever experience with Linux and so far I'm loving it. The only problem is music will not play in Rhythm box or Amarak, the play button turns into a pause button in both programs as if it is playing, but the duration bar makes no progress, the song just doesn't start. When using Firefox, Chrome and Chromium Youtube just freezes as soon as I get onto the site, I can't even use the search bar. Also using the same browsers with Pandora, it shows a song playing for 2 seconds(no sound) and then skips to another continuously and then just freezes. Pandora through Nuvola also just completely freezes. I'm assuming that these are all related, probably due to a problem with Adobe Flash? I reinstalled Flash through the Ubuntu software center and that did not help. I have quite a bit of experience with computers but only with Windows, so this is all new to me, I'm sure it's something simple though. Usually is. I'm exclusively running Ubuntu 13.04 64 bit on an HP Pavillion Dv7, it has an i5 and 6 gb of ram if that helps. Any help would be GREATLY appreciated as I'd love to use this over Windows 7. Thank you

---

### Post by Quarkrad on 2013-09-25
I'm not sure this will sort your video/music issue as I'm a newbie but one thing I always do after installing a new version of ubuntu is the following command in terminal:

sudo apt-get install ubuntu-restricted-extras

This command install all sorts of 'things' you need.  A Google search will probably detail.  Another good source after a new install is to goole something like '10 things to do after installing ubuntu 13.04'   or what ever version you have.   You will get to know the common web addresses - there are many things to add after a new install that will enhance your environment.  You will find many common things to add from these sites - go with these.

---

### Post by whitesmith on 2013-09-25
Did you install Flash? It's terribly insecure and is known to cause bizarre problems similar to those you describe. If you're not sure exactly what you installed, open a terminal and type ```
dpkg --get-selections
```Another thought: with just 6 GB of RAM, you'll need a swap partition. You have one, right?

---

### Post by scott_Henderson on 2013-09-25
Ok I've got it figured out (kind of) haha. I reinstalled the sound drivers and restarted and the sound worked again, youtube, amarok, pandora etc.. worked, but when I used the Nuvola player it crashed and then I had the sound issues again. So basically I guess I'll just avoid Nuvola or reinstall it or something. Just curious, does anyone else use Pandora through Nuvola? I liked it for the ease of access but I can definitely do without it. Thanks for support, sorry for bothering with such a stupid error :P

---

