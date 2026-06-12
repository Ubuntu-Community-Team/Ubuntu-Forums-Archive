---
title: "NowPlaying Screenlet + Amarok = No Cover Shown"
date: 2008-06-17
forum: General Help
---

### Post by jusuchin85 on 2008-06-17
Hi all,

I need some help in this. I remember using the NowPlaying screenlet in Gutsy, and it worked very well in retrieving and displaying cover arts from my MP3 files. Since I've upgraded to Hardy and installed the new screenlet (ver 0.1.2), I'm unable to view them at all!

Here's a sample of the music being played in Amarok:
[[IMG]http://img253.imageshack.us/img253/6210/screenshotzg5.th.gif[/IMG]](http://img253.imageshack.us/my.php?image=screenshotzg5.gif)

And here's the one with the NowPlaying at the right-hand side:
[[IMG]http://img386.imageshack.us/img386/5285/screenshotnocoverpt7.th.gif[/IMG]](http://img386.imageshack.us/my.php?image=screenshotnocoverpt7.gif)

FYI, the cover art is embedded into the ID3 tags, and believe me when I say that it worked in Gutsy in that condition!:confused:

I hope someone can help me? I'm really into desktop cuztomization, and want to do this a whole lot!

Thanks!

p/s: I've already installed the python-dcop as well.

---

### Post by jusuchin85 on 2008-06-18
Bumping this up!:-#

---

### Post by jusuchin85 on 2008-06-18
just to make sure, i've already installed python-dcop, so it shouldn't be that problem...or is it?

---

### Post by rune0077 on 2008-06-18
Nah, I think it's because NowPlaying gets the covers from Amazon, and Amazon has changed their databases so it can't find them anymore.

---

### Post by migueletorres on 2008-06-19
NowPlaying DOES NOT donwloads cover art from internet, it uses the ones in your PC.

By the way.. I have the same issue... and it was working before the last screenlets update...

---

### Post by rune0077 on 2008-06-20
> **migueletorres said:**
> NowPlaying DOES NOT donwloads cover art from internet, it uses the ones in your PC.

By the way.. I have the same issue... and it was working before the last screenlets update...

If NowPlaying can't find a local path for a cover, it does actually try to find the cover from Amazon instead.

---

### Post by jusuchin85 on 2008-06-20
> **rune0077 said:**
> **#1:** Nah, I think it's because NowPlaying gets the covers from Amazon, and Amazon has changed their databases so it can't find them anymore.

**#2:** If NowPlaying can't find a local path for a cover, it does actually try to find the cover from Amazon instead. 


Hmm, I don't really think that was the issue. It's true that there's an option for NowPlaying to attain covers from Amazon, but maybe what you pointed out is true as well; since Amazon has changed their database and all.

> **migueletorres said:**
> NowPlaying DOES NOT donwloads cover art from internet, it uses the ones in your PC.

By the way.. I have the same issue... and it was working before the last screenlets update... 

Yeah, I have to agree with you on that part; the last version before the latest one worked out perfectly! I remember it attaining the covers directly from the ID3 tags of the playing MP3.

Hmm, it could be the Python codes, but I'm not really sure. If anyone out there who are using the screenlet and making it work under Hardy, I hope I can hear a solution from you! Thanks (Honto arigatou!):)

---

### Post by migueletorres on 2008-06-21
I've Just tested NowPlaying with rhythmbox, and cover art works well, so it is an issue only on amarok.

Can somebody help us?

---

### Post by jusuchin85 on 2008-06-27
hello all,

sorry for the late reply. been having exams this week, so real life issues come first!

anyways;

@migueletorres

thanks for testing out with rhythmbox. too bad it didnt work under amarok for you too. i'll try to report to the developer of this version and see whet he can do abt it.

also, i've tested with screenlets version 0.0.14, and it worked great! The NowPlaying screenlet works like a charm. so definitely an issue with the 0.1.2. So, in the meantime, i'm using this version for the moment...until the matter is resolved!

---

### Post by jambare on 2008-06-27
Hey guy! I did it!!
[www.screenlets.org](www.screenlets.org)
1. i just deleted any mention to screenlets
2. add to your sources.list deb [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) gutsy main universe.
3. install from synaptic then screenlets
4. Nowplaying works with amarok now.
Bye and luck!!

---

### Post by jusuchin85 on 2008-06-27
> **jambare said:**
> Hey guy! I did it!!
[www.screenlets.org](www.screenlets.org)
1. i just deleted any mention to screenlets
2. add to your sources.list deb [http://ppa.launchpad.net/gilir/ubuntu](http://ppa.launchpad.net/gilir/ubuntu) gutsy main universe.
3. install from synaptic then screenlets
4. Nowplaying works with amarok now.
Bye and luck!!

Nice work, jambare! Just want to confirm with ya: are your cover arts embedded into the MP3 tag or as an image in the same folder as the MP3 itself?

UPDATE:
I went researching all afternoon and found out that they updated the version 0.1.2 to cater for all music players. The thing is, when I installed it, it still doesn't work! The music title was rolling, but no images still. So, i stuck with the old NowPlaying. If you can get it to run with the covers embedded into the MP3 tags, that would be an extra help needed! Thanks!

---

### Post by jambare on 2008-06-28
Well, i have the pictures into the music folder (some called folder.jpg), but works with the covers that search amarok in amazon... (i test it)
Try also start first amarok, then nowplaying screenlet. 
Pd. (sorry about my english - im spanish :) and luck!!
This is my msn if i can help (kasspy@hotm...)

---

### Post by CLEARviewF on 2008-07-18
Well i read all the post and....
I have installed Ubuntu Hardy 8.04.1 with Compiz and ScreenLets.
One installation in my PC and other here in my Laptop.
I recently installed Ubuntu here in my laptop and had that problem with Nowplaying Screenlet.
[COLOR="Red"]**I just installed python-dcop and restart NowPlaying Screenlet and done**[/COLOR], Covers are working. **[COLOR="Red"]Even with ID3 tags[/COLOR]**, i tried it right now.
For example, every single song in Nine Inch Nails Ghosts I-IV albums have a cover and each of its works with NowPlaying ScreenLets right now with python-dcop.

I hope all of you could solve your problem right now.

BTW, somebody mentioned before that he installed python-dcop and even that nowplaying did not work, that is weird, i did that and it is working charming.

maybe you want to chat with me in: mauricio.mora.meza@hot...


bye.

P.S.: when i have an album that have not every single track with cover embebed in ID3 tags, then i set a general cover for that album from amazon with amarok and, it affects only to the tracks that have not a ID3tag cover, that is even better :D

That is true, you have first to run Amarok and then run nowplaying screenlet.

---

### Post by migueletorres on 2008-08-02
Actually I did run a full clean installation, but no album covers with amarok... and yes there were album covers with rhytmbox... 

Any suggestions?

---

### Post by hermeschris on 2008-08-05
Same problem here on three different hardy machines. :(

---

### Post by amr2205 on 2008-09-11
> **CLEARviewF said:**
> Well i read all the post and....
I have installed Ubuntu Hardy 8.04.1 with Compiz and ScreenLets.
One installation in my PC and other here in my Laptop.
I recently installed Ubuntu here in my laptop and had that problem with Nowplaying Screenlet.
[COLOR="Red"]**I just installed python-dcop and restart NowPlaying Screenlet and done**[/COLOR], Covers are working. **[COLOR="Red"]Even with ID3 tags[/COLOR]**, i tried it right now.
For example, every single song in Nine Inch Nails Ghosts I-IV albums have a cover and each of its works with NowPlaying ScreenLets right now with python-dcop.

I hope all of you could solve your problem right now.

BTW, somebody mentioned before that he installed python-dcop and even that nowplaying did not work, that is weird, i did that and it is working charming.

maybe you want to chat with me in: mauricio.mora.meza@hot...


bye.

P.S.: when i have an album that have not every single track with cover embebed in ID3 tags, then i set a general cover for that album from amazon with amarok and, it affects only to the tracks that have not a ID3tag cover, that is even better :D

That is true, you have first to run Amarok and then run nowplaying screenlet.

Yeap, it worked for me too... btw, I had restart my media player too in order to get the covers to work in Nowplaying screenlet. (I'm using Banshee)

---

### Post by cesar_spain on 2008-09-11
> **amr2205 said:**
> Yeap, it worked for me too... btw, I had restart my media player too in order to get the covers to work in Nowplaying screenlet. (I'm using Banshee)

  I have the very same problem. I solved it using the gutsy version. Add this line to  your /etc/apt/sources.list

[PHP]deb http://ppa.launchpad.net/gilir/ubuntu gutsy main universe[/PHP]

  Now force this screenlets version:

 0.1.2~bzr451-gutsy1-1

   This is the only version that works in my system for showing Amarok covers in NowPlaying. I tried hardy version, but did not work.

César

---

### Post by roebeet on 2008-10-08
I have the same issue as cesar_spain  (Hardy x64, in my case).  His fix worked for me, as well.

---

### Post by Da_Muffin on 2008-12-26
I could not solve the problem using the above fixes. I am running Intrepid 64bit. However it was solved after I installed this modified version of now playing to my screenlets daemon.

[http://gnome-look.org/content/show.php/Nowplaying+Screenlet+modified?content=69988](http://gnome-look.org/content/show.php/Nowplaying+Screenlet+modified?content=69988)

---

