---
title: "Mplayer not &quot;fullscreen&quot;"
date: 2005-04-24
forum: General Help
---

### Post by DutchLau on 2005-04-24
Hello everyone

The very first day Ubuntu 5.04 came out I installed it and it's working great!

I've installed almost all of the appications I need, but I can't seem to get Mplayer to work properly. It plays the video, sounds and does everything correctly, but it doesn't go "fullscreen," - it leaves a black border around the video which it leaves the original size. It seems like it doesn't strech the movie. 

Could someone help me out with this annoyance or give me a link to another thread that covers this please? I've Googled a few times, but I haven't found anything that solves my problem. Thanks. 

Btw, I'm running an AMD 1700+ Scoring approx 2.1 ghz, 512 Mb PC 266 Ram, 256 GeForce FX 5200 with the latest drivers and I've got Mplayer 386 installed (could this be the problem? - I installed the mplayer-k6 package, but that didn't work AT ALL) Cheers to all.

---

### Post by cowbud on 2005-04-24
when running mplayer use mplayer -zoom this will stretch the picture so that when you go in to fullscreen mode it will fit to the screen. 

Hope this helps

---

### Post by DutchLau on 2005-04-24
Hi, and thanks for the reply,

I'm not sure what you mean by the mplayer -zoom command. Should I use it in the terminal while opening a movie? I just use mplayer via gnome, so I open it with X. Could you please help me out a little more? I'm a bit of a linux noob, but I'm already at ease with the terminal. Thanks again

---

### Post by tomchuk on 2005-04-24
Some video output drivers don't do scaling - x11 is one of them. Make sure your /etc/mplayer/mplayer.conf has vo=xv and you don't have a ~/.mplayer/config that is overriding the one in /etc

---

### Post by cowbud on 2005-04-24
Sure,

In gnome right click on one of the files you generally open with mplayer 

then goto the Open With  tab
then click on Add

Then click on Use a custom Command 

type in the location of mplayer -zoom

e.g.

/usr/bin/mplayer -zoom

another mplayer will be added to the list of your open with applications 

Make sure that one is selected (it should select it by default once you add the custom command)

Double click on your file and you should be good to go.

---

### Post by Sam on 2005-04-24
[QUOTE=DutchLau]Hello everyone

The very first day Ubuntu 5.04 came out I installed it and it's working great!

I've installed almost all of the appications I need, but I can't seem to get Mplayer to work properly. It plays the video, sounds and does everything correctly, but it doesn't go "fullscreen," - it leaves a black border around the video which it leaves the original size. It seems like it doesn't strech the movie. 

Could someone help me out with this annoyance or give me a link to another thread that covers this please? I've Googled a few times, but I haven't found anything that solves my problem. Thanks. 

Btw, I'm running an AMD 1700+ Scoring approx 2.1 ghz, 512 Mb PC 266 Ram, 256 GeForce FX 5200 with the latest drivers and I've got Mplayer 386 installed (could this be the problem? - I installed the mplayer-k6 package, but that didn't work AT ALL) Cheers to all.[/QUOTE]
I've already asked this question ([here](http://ubuntuforums.org/showthread.php?t=24797)). You have to go to the Preferences window, Video tab and set "xv" as the driver.

---

### Post by crazybill on 2005-04-24
You should be able to open mplayer with your terminal.using mplayer -zoom. You will get an error message in the terminal window but it should open in Gnome and play correctly. Try it.

---

### Post by Turin Turambar on 2005-04-24
Yes, use the XV (videx or vodex, I forgot) driver instead of X11. I had the same problem. However, I couldn't select XV, I received some error during application start, although my card was supported by that driver.
Then I installed VLC and I'm happy. :)

---

### Post by DutchLau on 2005-04-25
Thanks for the replys guys, I'm going to try changing the X11 codec to the XV codec as soon as I'm on my Linux box. I already saw that you could change these in the prefrences tab in Mplayer, but I wasn't sure if I'd mess things up. 

P.S. is there a "search" function in the Ubuntu forums yet?

Greets

---

### Post by Turin Turambar on 2005-04-25
[QUOTE=DutchLau] P.S. is there a "search" function in the Ubuntu forums yet?

Greets[/QUOTE]

Of course, it's in the middle of "Unanswered threads" and "quick links", at the top of the page.

---

### Post by DutchLau on 2005-04-25
Ooops, sorry!  :) 

I'll search around a bit next time before posting

---

### Post by cymkhat on 2005-05-12
man you soluttion - "mplayer -zoom" works absolutely perfectly - FLAWLESS!!!.

thanks

---

### Post by cymkhat on 2005-05-12
man your solution - mplayer -zoom works absolutely perfectly - flawless.

thanks

---

### Post by lleberg on 2005-05-31
I had this problem to one minute ago.

opened the  /etc/mplayer/mplayer.conf to change vo=X11 to xv or whatever it was.
but a bit further down there is (or was) a "Zoom=No", i changed it to yes thinking what could go wrong.. and it worked!

Edit: And i'm running the 64bit version with a ATI vga, if it matters! ;-)

---

### Post by brandan on 2005-06-02
i use the x11 gl driver and it stretches without a problem (in the video preferences).

---

### Post by kvidell on 2005-06-02
I hate using -zoom
This is how I do it:
mplayer -fstype fullscreen -fs filename.to.be.played

THAT works awesome.
- Kev

---

### Post by stoffepojken on 2005-06-02
I did what you said with the drivers and my mplayer crashed completely. I get three failure messages and the first is: Mplayer is interupted by signal x11 in modul: demux_open. What does that mean?

---

