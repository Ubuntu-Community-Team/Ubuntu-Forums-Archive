---
title: "Random Crashes In Hardy"
date: 2008-04-27
forum: General Help
---

### Post by czechman86 on 2008-04-27
I have recently built a brand new pc, to welcome hardy onto, however, I have been experiencing many weird and random crashes. for example, it seems as though the system will lock it. Like i will try to open up a terminal window and it will freeze and ask me to force quit it. this continues until it just starts closing on its own with no crash dialog box or anything. my first thought was memory, as i have had to deal with linux on a faulty memory computer before. mem test yielded two passes and there are no instances of kernel panic in the system logs. this is very confusing to me. Has any other user been experiencing this problem? Does anyone know of any diagnostics to run or any possible solutions?

Thank you!

EDIT: Please ask me for any documentation, which you wish me to post, and I will gladly do so.

---

### Post by czechman86 on 2008-04-27
I read on another forum that uninstalling tracker might fix this. i have done so and will continue to provide updates.

---

### Post by czechman86 on 2008-04-28
New developments: This problem seems to begin after I play a video on youtube. after leaving youtube, i received a link to go back there and when I did, the sound wouldnt work, so i decided to just close youtube and attempted to open up my music player. it wouldnt launch, so then i tried the terminal, which launched, but then froze and asked me to force quit. any ideas?

EDIT: Here are some of the errors/interesting events I have been getting:

```
Apr 28 00:06:01 uBox pulseaudio[5561]: pstream.c: Failed to import memory block.
```

```
Apr 27 23:09:37 uBox kernel: [   37.668502] hda-intel: Invalid position buffer, using LPIB read method instead.
```

```
Apr 27 23:09:37 uBox kernel: [   37.668502] hda-intel: Invalid position buffer, using LPIB read method instead.
```

Next time this happens, I am going to post my entire log for that secession. Thanks

---

### Post by czechman86 on 2008-05-05
i figured that i would add an update to this. i uninstalled tracker, and the crashes seem to go away. however, today i have had two unexpected freeze ups and crashes. both seem related to youtube and sound. ill watch 1 youtube video (with the alternative codec, not flash) and then i will proceed to watch another. like cake work, the sound is gone on the second video and then my programs loose their sound (ie music players) and the freeze up and crash begins.

Has anyone else had this problem?

---

### Post by Lutherian on 2008-05-06
Hi friend. I've been having the same problem. I've been waiting for the latest LTS version, but I've had the same problem with each version that I've tried. It happens if it's installed on the Hard Drive and also if I boot from the CD.
I've notices that my File Manager Windows and Firefox both just shutdown in the same way.
I must be a hardware problem, and I suspect your's is too. Perhaps I have too little RAM (256 MB) becuase the only version that ever work for me was Dapper 6.06. 

Can't offer much help, but if I find something, I'll let you know.

---

### Post by Gatemaze on 2008-05-07
I don't know if it is related to a bug that many users have experienced (including me) and has completely crashed their systems. Check the following:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204996)
[http://ubuntuforums.org/showthread.php?t=768200](http://ubuntuforums.org/showthread.php?t=768200)

---

### Post by grazed on 2008-05-07
There is currently a bug with pulse audio and flash that causes loss in sound like you are describing.

Go into synaptic, not add/remove, and search for and install libflashsupport.

Hope that helps. =/

---

### Post by squidmaster on 2008-05-09
wowzer I went to Firefox 2 (down from beta3) and everything is SO much faster and best of all, NO RANDOM FREEZING OR LOG OUTS!!!

---

