---
title: "Make this play in linux challenge"
date: 2006-12-17
forum: General Help
---

### Post by helmeteye on 2006-12-17
I have been trying to get this video to work forever.  When I say forever, I have literaly reinstalled linux from dapper fresh to edgy about 15 times with different ways of loading video codex each time.

     The site is silent partner, a tennis stringer website.
[http://sptennis.com/stringer.asp](http://sptennis.com/stringer.asp)

The video is of the Silent partner maestro:
javascript:newWindow('http://www.sptennis.com/videos/Alex120.html')

     I haven't been able to make this play on Linux.  Windows played it.

---

### Post by blackened on 2006-12-17
I had no problems playing this video in Dapper with the mplayer firefox plugin installable via automatix.

---

### Post by helmeteye on 2006-12-17
I have and am using mplayer.  Can't seem to get it going.  I used automatix around my 3rd or 4th install.  I am not using Dapper but Edgy.

---

### Post by helmeteye on 2006-12-18
No takers, aye!  What do I need to cut and paste for someone to see what is going on?

---

### Post by shoagun on 2006-12-18
The video works fine for me.  Have you tried installing the mplayer plugin for firefox?

---

### Post by helmeteye on 2006-12-18
> **shoagun said:**
> The video works fine for me.  Have you tried installing the mplayer plugin for firefox?

     Yes.  ](*,)   ahhhhhhhh!  Not for you:D   Just in general.  I have tried dapper and edgy.  Argh!  I was just looking at Fiesty for the hell of it.  Can't stand it.  I have managed to have compiz and all that working perfectly and destroyed everything I've done so far just to get those videos, yet, I have none of those videos working.  The best I've done is one third or just audio](*,)  Compiz won't work now.  As a matter of fact compiz was atleast 3 installs ago.  Tried Baryl, no good.  Nothing works good.  I haven't done a fresh install in 4 days.  A new record.  I even tried beryl back when I could spell it, when I didn't drink.

---

### Post by towsonu2003 on 2006-12-18
I can play them with mplayer plugin as well (no automatix). 
I found the links to the videos using the unplug Firefox plugin. So,

install kaffeine and the [restricted format stuff]("https://help.ubuntu.com/community/RestrictedFormats"),
tell kaffeine to play these URLs:
mms://www.sptennis.com/videos/estrFO41.wmv (first vid)
mms://www.sptennis.com/videos/estrFO165.wmv (2nd)
mms://www.sptennis.com/videos/estr38.wmv (3rd)
mms://www.sptennis.com/videos/estr170.wmv (4th)

If you have a firewall, disable its outgoing (not incoming) restrictions while playing, as kaffeine will probably use port 1755 to play these. good luck.

PS. give a little break to trying to make compiz or beryl work... they are eye candy anyway, they shouldn't make you hate the OS ;)

---

### Post by pgatrick on 2006-12-18
Have you tried using vlc? It can play pretty much anything I can throw at it, even in the 64 bit version.

---

### Post by helmeteye on 2006-12-18
i've tried everything yall have mentioned.  As soon as I finish installing something, I'll try a couple more things.  I don't hate the OS, I love it.  I am however, a working man and don't have time to memorize all the diffent configs of all these differnt players.

---

### Post by shoagun on 2006-12-18
Hey, I understand your frustration.  The first time I installed Ubuntu, I got compiz working but had a hell of a time with video and sound stuff.  I actually ended up getting it all working eventually.  I've since tried installing Ubuntu without using compiz and everything worked really easily.  There are a few ways compiz can make video a little more difficult.  If you're set on using compiz, then it will probably just take some fiddling around.  Here are a few things that need to be done to have things working well:

Install the codecs found here [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)
Install the mplayer, java, and flash plugins for firefox

If you post a little more info, people might be able to better assist you

---

### Post by towsonu2003 on 2006-12-18
interesting... kaffeine usually plays everything for me, even radio streams and stuff... weird. try this: 

sudo apt-get install mimms and use it to download the stream. maybe than you can play it. if you can't, try converting it to avi using ffmpeg. 

using mimms:
cd /path/to/where/you/wanttodownload
mimms video1.wmv mms://www.sptennis.com:80/videos/estrFO41.wmv

bla bla

if they still don't play in mplayer or kaffeine after downloading them, try converting them:
sudo apt-get install ffmpeg
ffmpeg -i video1.wmv video1.avi

if ffmpeg spits an error, pls copy paste here.

---

### Post by helmeteye on 2006-12-19
Shoagun and Town,  appreciate the help.  Just got home and have a doctors appointment tomorrow morning so I won't have time to try those set ups.  When I try them I will post to let yall know if they work.  Have any of you watched the videos to see how long they will play?  A few incarnations ago, ahem, I mean installs ago, I actually had it playing with video but the video only lasted around 3 minutes and then there was only sound.  I almost always get the sound going.  One of the things I worry about is getting so many codex and players that they actually interfere with each other, I have never actually seen that happen but I figure it could.  Oh by the way, I almost always get sound from those videos but no video unless it is with the mozilla plugin, in which case, I get nothing but a white square.

---

