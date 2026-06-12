---
title: "Poor Audio Quality"
date: 2005-04-05
forum: General Help
---

### Post by honeywelljr on 2005-04-05
I am brand new to Ubuntu.  Switching from SuSE, and already overjoyed with the decision.  (I was very new to SuSE before switching and found Ubuntu when looking for something more friendly to a home user)

I haven't had too many problems with anything so far. Except, for the longest time  I wasn't able to get audio working in alot of programs. That is until I found the article at:

[Hoary Sound Problems](http://www.ubuntulinux.org/wiki/SoundProblemsHoary/view?searchterm=no%20audio) 

With this I was able to get sound in flash animations to work perfectly.  But after following the directions for Totem the sound cuts in and out and is of poor quality (only when using Totem).  I don't even know where to begin to look.  It works fine when viewing flash animations, just not when using totem.  Where do I start? What do I do?  

(please remember that I am not only new to Ubuntu, but linux in general)

---

### Post by honeywelljr on 2005-04-05
I was hoping I would get this figure out quicker.  

I was wondering, would using Mplayer possibly fix this problem?  I only have the audio problem when using totom-xine.

---

### Post by honeywelljr on 2005-04-07
Okay.  Maybe I have been going about my questions wrong.  Hopefully that will explain the lack of response.

This is what I did to fix the "no audio" problem

```
      in a Terminal, cd ~/.gnome2
    *

      gedit totem_config (or something like that, easy to find with ls)
    *

      uncomment audio.driver and write (in that line, after audio.driver:) esd
```


I am assuming that when I added "esd" that it was in some way referring to an audio driver or something.   Do I have a choice of audio drivers?  Could it be that I need a better one?  If "esd" is not a referenct to an audio driver what is it a reference to?

Even if you don't know the answer, I would appreciate any information that might help me discover the answer on my own.  Or at least let me know that someone is reading my messages....   It is very disconcerting to have my first post on the board go unanswered (without so much as a welcome).

---

### Post by nicholaspaul on 2005-04-07
Seems like that link in the same post pointed to problems with xmms. 
On that note: 
I noticed way too much distortion (ie. any at all!) with xmms, so I use beep-media-player instead. Bloody brilliant! I run it on a machine that does nothing all day except play mp3s, and it sounds great! This is on a new install, no tweaking, no fancy stuff(!). 

I'd ditch xmms and use beep-media-player instead (its avail. at synaptic)

---

### Post by honeywelljr on 2005-04-07
[QUOTE=nicholaspaul]Seems like that link in the same post pointed to problems with xmms. 
[/QUOTE]

If you scroll further down it talks about Totem and Xine.  I am needing something to play DVD's and Avi files with.  will this other program do that?

I have been meaning to try installing mplayer that everyone seems to talk about but the quick try that I gave it showed a dependency issue I didn't have time to delve into and this weekend I have to exchange hard drives and boot into windows to work on something using macromedia flash. (that is the only program I ever have to do this for... does anyone know a linux alternative?  Then I can cut the strings completly)

---

### Post by raublekick on 2005-04-07
[QUOTE=nicholaspaul]Seems like that link in the same post pointed to problems with xmms. 
On that note: 
I noticed way too much distortion (ie. any at all!) with xmms, so I use beep-media-player instead. Bloody brilliant! I run it on a machine that does nothing all day except play mp3s, and it sounds great! This is on a new install, no tweaking, no fancy stuff(!). 

I'd ditch xmms and use beep-media-player instead (its avail. at synaptic)[/QUOTE]
 hmmm i'm going to have to remember to install beep-media-player, as i noticed xmms producing distortion in FC2 unless i set the volume below about 70%. how is the interface? i really love the xmms/winamp interface, it'll be tough to change.

---

### Post by Nis on 2005-04-07
[QUOTE=honeywelljr]If you scroll further down it talks about Totem and Xine.  I am needing something to play DVD's and Avi files with.  will this other program do that?

I have been meaning to try installing mplayer that everyone seems to talk about but the quick try that I gave it showed a dependency issue I didn't have time to delve into and this weekend I have to exchange hard drives and boot into windows to work on something using macromedia flash. (that is the only program I ever have to do this for... does anyone know a linux alternative?  Then I can cut the strings completly)[/QUOTE]
 Try changing the audio driver in totem_config to alsa or oss.  See if that helps and report back here.

As for playing DVDs and avi's, you'll need libdvdcss for DVDs and w32codecs for avi's (and other such formats such as mov).  You can get both of these using the HAIH (as in my signature); totem-xine works great with these two.

And by the way, welcome to the Ubuntu community. :)  Sorry about the lack of response to your problem.  Sometimes things just fall through the cracks. :(

---

### Post by honeywelljr on 2005-04-08
I actually was able to get DVD and AVI to play back.  It may be easy to get lost in the online documentation but there is alot of information there and it is extremely easy to follow.

[QUOTE=Nis]
And by the way, welcome to the Ubuntu community. :)  Sorry about the lack of response to your problem.  Sometimes things just fall through the cracks. :([/QUOTE]

That is okay, It looked like alot of people were trying to help the other Suse convert that will remain un-named (he went back to XP, which I will never understand) and it sounded like he was keeping everyone pretty busy.  I have been lurking for a week or two in the forums and everyone seems very helpful so I figured someone would find me... eventually  :p

---

### Post by honeywelljr on 2005-04-08
okay when I switch to alsa I got an "unsupported codec" warning and then no audio when playing .avi files.  DVD played with audio but same issue with audio.  It just has static in it.  Not a continuos static more like a fluttering of static.  OSS didn't have a warning about a codec on .avi but it also had no audio and the same fluttering in the static.  The sound was better though, not the static at all, but it didn't sound tinny. (really I didn't even notice the tinny sound until after switching to OSS and ALSA).

Since it happened on both of the other drivers... is it fixable. Are there other ones?

I would almost think it was the audio card but when I listen to audio that is in flash animations on the web it sounds fine.

I tried searching this issue, but I don't know what to put in as a search.

---

### Post by nicholaspaul on 2005-04-08
[QUOTE=raublekick]hmmm i'm going to have to remember to install beep-media-player, as i noticed xmms producing distortion in FC2 unless i set the volume below about 70%. how is the interface? i really love the xmms/winamp interface, it'll be tough to change.[/QUOTE]
BMP is based on xmms and uses winamp skins - you'll love it! It just doesnt have the double size feature, thats all.

---

### Post by honeywelljr on 2005-04-18
Okay, I had a small problem with my system crashing that distracted me from this issue.  That is fixed.  So, now I am back to the audio issue.

Since I last dealt with this problem I have changed out the sound card and I have the same problem with the new one.  CD and MP3 playback is crystal clear; as are games and system sounds.  However, when I try playing a DVD, AVI files, or even MP3 files using Totem I get a weird choppy static noise in the audio.  almost like the speaker is talking through a fan.  It almost sounds like a problem specific to Totem and/or Xine?  Would switching programs fix it?  

I would rather fix the programs I have than bail and use another program.  Not that I am that attatched to them, I just feel that problems like this are good learning opportunities and would rather find out what is wrong and then decide if I want to change.  If I bailed on every program that didn't work right away I would surely run out of programs at some point.

---

### Post by ubuntulnx on 2005-04-24
im having _exactly_ the same problems. if i get it solved, ill let you know.

also see.. [http://ubuntuforums.org/showthread.php?p=145876#post145876](http://ubuntuforums.org/showthread.php?p=145876#post145876)

---

### Post by ubuntulnx on 2005-05-06
update. this seems to work for me:
[http://ubuntuforums.org/showpost.php?p=160789&postcount=5](http://ubuntuforums.org/showpost.php?p=160789&postcount=5)

regards ubuntulnx

---

### Post by nicholaspaul on 2005-06-01
[QUOTE=honeywelljr]
I would rather fix the programs I have than bail and use another program.  Not that I am that attatched to them, I just feel that problems like this are good learning opportunities and would rather find out what is wrong and then decide if I want to change.  If I bailed on every program that didn't work right away I would surely run out of programs at some point.[/QUOTE]
-or you would quickly find the programs that work the best. I could have tried other drivers, played with parameters until dawn, and still not got xmms to sound good. I found the problem, got a new prog (BMP) and got on with my life. 

Part of running linux is finding the suite of programs that work for you. Its not quitting. Its searching and doing what works with your setup.

---

### Post by honeywelljr on 2005-06-02
That is true, I hadn't looked at it like that.  I did end up fixing this issue.  Though it was by changing computers, so I don't know what the problem was.  I know that it has a bad wrap in some of the forums but I actually like totem.  It is no frills and easy to use.  I don't listen to alot of multimedia on my computer and when I do I don't want to have settings to adjust or anything like that.

---

