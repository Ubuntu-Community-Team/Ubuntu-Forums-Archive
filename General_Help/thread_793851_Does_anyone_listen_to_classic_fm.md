---
title: "Does anyone listen to classic fm?"
date: 2008-05-14
forum: General Help
---

### Post by Despot Despondency on 2008-05-14
Hey, does anyone listen to classic fm? Have you been able to get it to work? I use to listen to the listen again service before I dumped windows for linux, but don't seem to be able to get it to work now. It says I need a media player that is compatible with windows media content, like mplayer. I have mplayer but it still doesn't work.

---

### Post by TeoBigusGeekus on 2008-05-14
I used to listen to classic fm until I discovered shoutcast radio:
Open vlc and go to Settings->Preferences. 
Choose playlist and click on services discovery. Check the shoutcast radio listings button and click save.
Now go to view->playlist and expand the shoutcast menu. Double click a category and there you go...

---

### Post by Despot Despondency on 2008-05-14
Hey, thanks for that. Looks pretty cool. :)

If anyone has worked it then I would still like to know. Always liked to be able to look at the playlist and find the recordings I liked so I could buy them. Pretty annoying that they seem to have completely disregarded linux users though.

Thanks again! listening to Beethoven fm at the moment.

---

### Post by TeoBigusGeekus on 2008-05-14
I prefer Otto's Classical Music :)

---

### Post by Despot Despondency on 2008-05-14
Yeah, they have a quite a lot of adverts on Beethoven fm. Will give that one a try. There's so many to choose from I'm sure I'll find some that I like. :-({|=

---

### Post by happyhamster on 2008-05-14
Do you also have the mozilla-mplayer plugin installed? If not: 

sudo apt-get install mozilla-mplayer

---

### Post by Despot Despondency on 2008-05-14
I had the mplayer plugin installed but I found it quite volatile, so I installed vlc instead. Can I have two installed and just pick and choose which one to use? If so, how? Cheers

---

### Post by tgalati4 on 2008-05-14
Don't forget tunapie:

>sudo apt-get install tunapie audacious

---

### Post by MedellinManDem on 2008-05-26
Can you listen to the BBC on Shoutcast?

---

### Post by flangemonkey on 2009-10-09
```
mplayer http:/mediasrv.musicradio.com/classicfm 
```

works after about 20-30 seconds, haven't tried it in any non-cli progs, but whack this into a terminal and you're away

man mplayer will give you the controls, but a quick overview for the unititated:

9, volume down
0, volume up
p 'comma' or 'space' for pause
q to quit
'[' and ']' to change playback speed

Phill

---

### Post by 1jackjack on 2010-06-07
Using google chrome on ubuntu 10.04, simply navigating to the following URL works for me:

[http://mediaweb.musicradio.com/Show.asx?StreamID=2](http://mediaweb.musicradio.com/Show.asx?StreamID=2)

Note: I have mplayer and vlc installed

If that doesn't work, their FAQ says: "If you are using the Linux Ubuntu operating system we recommend installing VLC player and then opening the following URL in VLC player to listen to Classic FM: http://mediaweb.musicradio.com/Show.asx?StreamID=2"

---

### Post by RedRat on 2010-06-07
> **TeoBigusGeekus said:**
> I used to listen to classic fm until I discovered shoutcast radio:
Open vlc and go to Settings->Preferences. 
Choose playlist and click on services discovery. Check the shoutcast radio listings button and click save.
Now go to view->playlist and expand the shoutcast menu. Double click a category and there you go...
I tried your method but something is clearly missing. When I click on the radio button for shoutcast, in the panel at the bottom the word "shout" shows up. I think that an url is supposed to go in there. Could you help out and tell me what that ought to be? Because without this url the Playlist has merely "shout" and I get an error that says it cannot connect to "shout".

Here is the error I get:
 p, li { white-space: pre-wrap; }  [COLOR=#ff0000]File reading failed:[/COLOR]
 [COLOR=#000000]VLC could not open the file "shout".[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'shout'. Check the log for details.[/COLOR]
 [COLOR=#ff0000]File reading failed:[/COLOR]
 [COLOR=#000000]VLC could not open the file "shout".[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'shout'. Check the log for details.[/COLOR]

---------------------------
Well after a day and half, the problem has indeed corrected itself. The only explanation I could see is that VLC needs time to down load all the Shoutcast stations.

---

### Post by tgalati4 on 2010-06-07
I got a few errors in the console, and then click play.  It works under Jaunty.

---

