---
title: "Playing Windows Media with Mozilla"
date: 2005-09-06
forum: General Help
---

### Post by User-007 on 2005-09-06
Hi all!

I am trying to watch windoms media video on my Ubuntu (browser FF 1.02). Please visit here: [http://www.yle.fi/yle24/videosali/?a=1&t=4&q=](http://www.yle.fi/yle24/videosali/?a=1&t=4&q=) . Then try to select some stream, for example "Uusin uutislähetys". Then the stream should begin to play. But it doesn't on my Firefox. I think I have all required installed: MPlayer, mozilla-mplayer win32codecs etc. This stream works fine on Suse 9.3 (I have also it..). I would be very happy if someone solved this problem.

BTW, I am newbie with Ubuntu. But I am amazed, this is so good. Light and workable. If I will get these streams working, Ubuntu will be my OS number one.

Thanks in advance
Pate

---

### Post by frodon on 2005-09-06
Before trying to solve this issue just try to open this stream with mozilla and your mozilla-mplayer plugin. In my case embedded videos don't work with firefox and mplayer-plugin but works perfectly with mozilla.

---

### Post by User-007 on 2005-09-06
Thanks for the quick answer.

No, the result is same whether I use Firefox or pure Mozilla. How to get these working? 

Pate

---

### Post by frodon on 2005-09-06
I will give a try to this stream after my job. Meanwhile you could have a look to vlc plugin (in synaptic) try it with mozilla and firefox or you could also try this [way](http://ubuntuforums.org/showthread.php?t=17727) .

---

### Post by User-007 on 2005-09-06
Hi!

I tried mozplugger-way, it works but that way doesn't let me change to the full-screen mode. Mplayerplugin is good, because I can choose in which mode I want to play the stream. The other way you told - Which vlc-plugin is needed and what configurations are needed to get it working? 

Pate

---

### Post by mcduck on 2005-09-06
I'm using VLC and mozilla-plugin-vlc, and those streams work just fine. I've also installed vlc-plugin-alsa, as I use alsa for my sounds and that seemed like something I'd need.. The plugin automaticly configures all vides (in net) to open in browser window, so no further configuring is needed.

Except that the "Uusin uutislähetys" stream doesn't work today as workers of YLE are on strike today end there was no news from YLE today ;)

[weird foreign language]
Asenna tuo vlc, mozilla-plugin-vlc ja riippuen äänisäädöistäsi sitten noita ääniplugareita. Muuta ei tarvitsekkaan säätää, plugin löytyy Firefoxin asetuksista Downloads-kohdasta, ja vakiona kaikki videot näkyvät selaimen ikkunassa. Klikkaamalla kuvaa saat sen koko ruudulle. Ja ihan vinkkinä muuten, gnomessa valikosta system/preferences/keyboard shortcuts ja kohtaan Toggle fullscreen mode laita vaikka alt+enter niin saat noilla napeilla minkä tahansa ohjelman koko ruudulle..
[/weird foreign language]

---

### Post by User-007 on 2005-09-06
Hi again!

Thank you, I've now using vlc-plugin. Now the video works with no problems but the sound is crashing... there are interrupts. If we'll get the sound working, this replaces the mplayerplugin.

Pate

---

### Post by frodon on 2005-09-07
Check that you have well installed w32 codecs. Does vlc plugin allow you to use fullscreen mode ?
Your stream works for me with mozila and mozilla-mplayer plugin.

---

### Post by User-007 on 2005-09-07
Yes, w32codecs are installed well. VLC-plugin allows me to use fullscreen mode, when I double-click the video. That (VLC) would be very good solution if I got also sound working....

Pate

---

### Post by frodon on 2005-09-07
you could try [that](http://ubuntuforums.org/showthread.php?t=61386&highlight=vlc+sound) .

---

### Post by User-007 on 2005-09-07
I tried, but no success. The audio crashes.... Any other ideas?

Pate

---

### Post by frodon on 2005-09-07
Hum really strange, are you sure that you have selected ESD as default audio codec ?
System->Preferences->Multimedia System Selector. Default Sink -> Output : ESD.  or something like that (i'm not sure of the english menu name). Does vlc sound work with videos on your harddrive .avi, .wmv ?

---

### Post by void_false on 2005-09-07
Quick question. How do I change my player in Firefox from Totem to VLC? I have both istalled, but dont know how to make streaming media open in VLC.

---

### Post by User-007 on 2005-09-07
Frodon.. yes, esound is set up for the default, but the sound doesn't works when watching streaming video. I tried to play some local avi videos with vlc, with perfect success. Then I tried to play local wmv video with vlc, and surprise! Now the sound works perfectly but where is the video? Nowhere. The same clip works perfectly with Xine....

How to get these working?

Nullman - You can use vlc with mozilla by installing the appropriate plugin - see earlier messages on this thread.

Pate

---

### Post by User-007 on 2005-09-08
I tried to play same stream with Mozillla, but no success. So, I have tried 3 ways to get those streams working. Mplayerplugin doesn't work with either Mozilla or Firefox. Totem works but it has no fullscreen option. Vlc works with Mozilla and Firefox, but with crashing sound. So none of these ways works as desired for me. You have had good ideas. Any other ideas. My only goal is to get those streams working with some way (with fullscreen).....

Pate

---

### Post by User-007 on 2005-09-08
I am thinking mozilla-mplayer again. What could this mean? The mplayer-plugin freezes immediately when trying to launch a stream.... (see attachment)

Pate

---

### Post by najames on 2005-09-09
No Totem full screen umm, did you click view - fullscreen?

Video seems to work fine for most wmv files I've tried.  I just tried a major leage baseball demo, but the sound did not work right however. hmmm.

I have w32codecs, totem-xine, totem installed.  I may be wrong, but it seems like that got working video.

---

### Post by User-007 on 2005-09-10
Yes, I tried but that option allow me to adjust the video size only within the space which is reserved for the video in the browser. So that is not the "real" plugin. Frodon... how did you get the mplayer-plugin working in the Mozilla?

Pate

---

### Post by frodon on 2005-09-11
When i just want to see a stream quickly and without fullscreen i use the totem plugin which i installed with mozilla.
When i want to see the stream in fullscreen mode i use firefox and the new mplayer plugin which  i installed yesterday following this [HOWTO](http://www.ubuntuforums.org/showthread.php?t=60505&page=1&pp=10) , i don't know why but i have the same problem than you now, at the end of download of the stream the video don't start. However it's not a problem because this version of the mplayer-plugin allow you to save the downloaded stream where you want, i like this way because when the stream is saved on your computer you can send it to friend and watch it with the player you like.

---

### Post by User-007 on 2005-09-11
Thanks, Frodon.

I installed the same new plugin but the result was same than you had. Has anyone ideas which causes this problem? Lack of some library? Any ideas?

Pate

---

### Post by frodon on 2005-09-11
Have you seen that after right click and choose play or reload the page you can save the video on your hard drive, it should solve the problem for a moment even if it's not a "magic" solution.
You should create a new thread for this mplayer-plugin problem, if not i think i will create a new one because i'm curious to know if it's a common problem and also how to solve it.

---

### Post by User-007 on 2005-09-11
Yes, I tried, but I am not thinking that is an appropriate way to watch streams... thank you though. Yes, I will now start a new thread, a big thankyou for you!

Pate

---

