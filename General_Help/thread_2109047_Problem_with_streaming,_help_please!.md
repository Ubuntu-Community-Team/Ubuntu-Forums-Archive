---
title: "Problem with streaming, help please!"
date: 2013-01-26
forum: General Help
---

### Post by nookey on 2013-01-26
Hello to all Ubuntu friends.

I need some help, and I am very desperate.
Here is the thing. I have a very old PC with some lame configuration ( Pentium 4 1.7 GHZ, 512 MB RAM, ATI Radeon 9200, 40 GB HD). I use it only for watching football games online, dpwnloading and watching movies, and for office.
But even this configuration worked fine with Windows xp for viewing streaming videos, you tube etc.
Now when I installed Ubuntu 12.04 , I cannot watch any HD movie that I have downloaded, all the football game streams are bad and the video is slow and late after the sound...
I am so frustrated, can anyone please help me?
Can I do anything to boost up my computer so I can watch the videos again?
I really like Ubuntu, but I am so dissapointed with this.

If anyone has any advice, I will be thankfull...

---

### Post by lisati on 2013-01-26
*Thread moved to **General Help**.*

---

### Post by Impavidus on 2013-01-26
Not surprised it worked fine with XP, considering this was very decent hardware when XP was released (a decade ago). However, for standard Ubuntu it isn't enough any more.

Have you considered one of the lighter versions of Ubuntu? I suggest Lubuntu.

---

### Post by nookey on 2013-01-26
> **Impavidus said:**
> Not surprised it worked fine with XP, considering this was very decent hardware when XP was released (a decade ago). However, for standard Ubuntu it isn't enough any more.

Have you considered one of the lighter versions of Ubuntu? I suggest Lubuntu.
Yes I've been thinking about it, but will this help me?
I know it is the much lighter version of Ubuntu, but will this have any effect on my problem?

---

### Post by Impavidus on 2013-01-26
It will free up a few 100MB of RAM, which should make your computer faster. RAM seems to me your bottleneck.

---

### Post by Calinou on 2013-01-26
Did you install the proprietary driver? It might make video decoding faster.


Also, try a lighter variant of Ubuntu. You don't need to reinstall to switch variants, just type this in a terminal to install Lubuntu:

```
sudo apt-get install lubuntu-desktop
```

Then log out, click the Ubuntu logo, choose "LXDE", then log in.

---

### Post by scbingham on 2013-01-26
I would imagine your motherboard would handle 1Gb RAM, probably 2Gb & that would run Ubuntu easily.

---

### Post by nookey on 2013-01-27
Thank you all for sugestions.

I installed Lubuntu and nothing is changed.

How can I check and update my drivers?

---

### Post by Spyderkid on 2013-01-27
go onto additional drivers and enable any which are available?

---

### Post by nookey on 2013-01-27
it says _no proprietary drivers are installed on this system_

---

### Post by ccrs8 on 2013-01-27
You can double or quadruple your RAM for pretty cheap, so that could be an easy solution if it really is a RAM issue.

Not sure about streaming - assuming Flash is correctly installed, not much I can add.

As for the HD movies, when you say they don't play, do you mean they don't play at all, or they open and play but are choppy?  If it is the former, you may need to install the proper codecs.  I'd go in to the software center and install the restricted extras.

---

### Post by nookey on 2013-01-27
I will try to find some RAM, if there is any on the market, because its ancient...

About HD, it 'works' but, video is late behind audio and constantly stopping. This is when I play downloaded material on hard disk.
But when I try to watch something online its like one frame per 5 seconds.
Even the smallest streams like 250, 300 kbps don't work properly, and then what to expect from HD 1800-2000 kbps.

I know this configuration is low, but until I get something better (I hope sooner than later)
I want to have this pc for this purposes only, so I really do not now what to do.
I really like to watch football matches, but now I cannot.
Also I didn't mention that speed test isn't working since I installed Ubuntu, few weeks ago.
I tried everything, installed chrome, updated flash, java but it still doesn't work.
It just say it is finding server and that's all. Could these two problems be related?
Maybe its got something to do with flash?

---

### Post by HiImTye on 2013-01-27
> **nookey said:**
> About HD, it 'works' but, video is late behind audio and constantly stopping. This is when I play downloaded material on hard disk.
But when I try to watch something online its like one frame per 5 seconds.
Even the smallest streams like 250, 300 kbps don't work properly, and then what to expect from HD 1800-2000 kbps.
are you playing them locally, or serving them to another computer on the LAN/WAN?
if locally, what media player are you using? I would try SMPlayer or VLC
```
sudo apt-get install smplayer
sudo apt-get install vlc
```

---

### Post by kurja on 2013-01-27
> **HiImTye said:**
> 
if locally, what media player are you using? I would try SMPlayer or VLC
```
sudo apt-get install smplayer
sudo apt-get install vlc
```
I second this, in my case the default video player can't play anything over 480 smoothly but vlc works ok for hd video. Likewise youtube etc videos are horrible in firefox but run very well in chromium browser.

---

### Post by kurja on 2013-01-27
> **nookey said:**
> I will try to find some RAM, if there is any on the market, because its ancient...


where are you located, I have some old ram that I'll give away.

---

### Post by nookey on 2013-01-28
> **HiImTye said:**
> are you playing them locally, or serving them to another computer on the LAN/WAN?
if locally, what media player are you using? I would try SMPlayer or VLC
```
sudo apt-get install smplayer
sudo apt-get install vlc
```
 
I have installed already smplayer and vlc and I'm playing them locallybut it's the same...

---

### Post by nookey on 2013-01-28
> **kurja said:**
> where are you located, I have some old ram that I'll give away.
 
I'm in Sarajevo, thank you for your kind gesture, but I think I found some RAM on our local online store, and after I get it I will give you feedback how it works...

---

### Post by afoin on 2013-01-28
You probably should not spend any money on this computer.

---

