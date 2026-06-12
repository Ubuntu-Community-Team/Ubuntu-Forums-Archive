---
title: "Firefox crashing"
date: 2007-05-20
forum: General Help
---

### Post by sh1znack on 2007-05-20
I'm not sure if it's my Ubuntu or Firefox. Whenever I just browse through different sites, a lot of times my Firefox locks up just by me doing something as simple as clicking a link. Actually, this only occurs when I click links within a web page. Any suggestions? Here is a video (sorry for the quality):

[http://youtube.com/watch?v=FkON_31e5l4](http://youtube.com/watch?v=FkON_31e5l4)

I'm currently running an up-to-date version of Feisty Fawn. I'm using Firefox 2.0.0.3 (latest version I believe).

---

### Post by evilc on 2007-05-20
Are you using Beryl/Compiz I have seen that in there seems to be using all memory and just freezes if watching video's, sorry have not found any answer except stop beryl/compiz when using video.

---

### Post by phidia on 2007-05-21
Firefox is crashing frequently on my computer, up to date feisty,  and I'm not using Beryl/Compiz.
I'm using Ephinany now. No crashing with it.

---

### Post by mrdodo on 2007-05-31
I have been having the same problem in Feisty, although I don't get an pop up message, Firefox just closes.

---

### Post by tsnj on 2007-06-01
Yep, I'm havin' the same problem.  Firefox just shuts down.  This began immediately after upgrading to Fiesty.  Is there a simple way to go back?

64bit Fiesty, 32bit Firefox.

---

### Post by neuromancer on 2007-06-01
Same problem here. No compiz/beryl, i'm using web developer toolbar and firebug plugin, plus flash and java plugins.
is there a bug report for this problem?

---

### Post by tsnj on 2007-06-02
After some automatic (ubuntu) updates late yesterday, Firefox hasn't crashed yet.  We'll see......

---

### Post by elucidblue on 2007-06-11
I'm having this same problem as well.  Firefox just closes without warning. Has nothing to do with online videos, though I have had gmail open it a tab almost every time.  I'm running Beryl.

---

### Post by awcreamsoda on 2007-06-12
Yup same here and after a while of lock ups and crashing I'll reboot and it fsck's the HD and basically ruins the install.  I am going to try "unmount" on the next fsck.
I've have also heard while pulling my hair out with Linux Mint after doing a little googling that Flash causes lockups ans crashes but after following the advice of a few users I gave up and installed Ubuntu.  In my opinion I don't believe Ubuntu or Linux Mint like AMD processors and their chipsets.

---

### Post by Crafty Kisses on 2007-06-12
> **sh1znack said:**
> I'm not sure if it's my Ubuntu or Firefox. Whenever I just browse through different sites, a lot of times my Firefox locks up just by me doing something as simple as clicking a link. Actually, this only occurs when I click links within a web page. Any suggestions? Here is a video (sorry for the quality):

[http://youtube.com/watch?v=FkON_31e5l4](http://youtube.com/watch?v=FkON_31e5l4)

I'm currently running an up-to-date version of Feisty Fawn. I'm using Firefox 2.0.0.3 (latest version I believe).

This can be caused by a lot of issues.

1. RAM
2. You have a lot of processes going at once.

You can check your processes by going into terminal and typing:
```
top
```
That should tell you what processes are going at the time, and see if anything is eating up resources.

There's also a program called "Conky" and you can see when FireFox is running to see what the CPU Usage% is at, to install Conky go into terminal and type:
```
sudo apt-get install conky
```

The third thing you can try is downloading a different Web Browser, I really like Opera so I'm going to go with Opera:
```
sudo apt-get install opera
```
Hope this helps. :D

---

