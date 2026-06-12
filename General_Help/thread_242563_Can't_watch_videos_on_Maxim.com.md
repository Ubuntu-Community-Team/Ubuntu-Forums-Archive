---
title: "Can't watch videos on Maxim.com"
date: 2006-08-23
forum: General Help
---

### Post by slugkilla on 2006-08-23
My video apps have gotten screwed up latly :( and I had to move from xine to mplayer. Another thing I noticed is that the mplayer pulgin for firefox no longer plays video from Maximonline.com
What's up with that? I mean come on?? My other thread has gotten maybe one reply so I thought addressing the real cause of devistation would get more attention! Somebody help me out here. Videos from my comp and from other sites will play in firefox but maxim will not. It worked fine till a few days ago. So thanks for any help.

ps. My old thread that tells the state of my system:
[http://www.ubuntuforums.org/showthread.php?p=1409802#post1409802](http://www.ubuntuforums.org/showthread.php?p=1409802#post1409802)

---

### Post by nalmeth on 2006-08-23
Are you getting an error from mplayer in firefox?

Or does it just sit at 99% and not play? 

Will it play if you right-click mplayer and hit play? I find this makes mplayer work when it appears it won't. 

Need a little more info :-k

---

### Post by slugkilla on 2006-08-23
It accutally says that it is finding the playlist, and then says "stopped". I think it starts buffering, but it does everything very fast and I can't read everything. If I hit play, it just sits there at "stopped". Thanks for the reply by the way.

---

### Post by nalmeth on 2006-08-23
I just went to maximonline.com, and videos seem to work fine for me and mozilla-mplayer..

I would just try reinstalling all the extra codecs including w32codecs, it  seems this might cause your problems..

---

### Post by slugkilla on 2006-08-24
Yeah I have completly removed every thing and put it all back again to no avail. I put the win32codecs in manually, the Ubuntu way, and with Automatix. Do you think that there is something else I need? Some other codec pack?

---

### Post by nalmeth on 2006-08-24
I went again to maximonline, and used the videodownloader extension to check, and it is a wmv/asx file. If you are sure you have all the codecs, I can't explain what the problem might be. I don't know if they use java in one form or another to feed the videos, maybe this is the case? 

Also, removing an app with a faulty configuration won't change anything, as the configuration is maintained for the future. To purge config, you have to add the --purge function before remove.

sudo apt-get --purge remove w32codecs. Again, I don't know if this will actually do anything for you, there shouldn't be any configuration for w32codecs..

Check into the java route. I have the stock java, not the Blackdown 1.4 version.

---

### Post by slugkilla on 2006-08-24
Nalmeth, how could I have not know about this --purge thing for so long? I reinstalled XINE and then purged it and the installed it again. And now it works! So now i'm gonna do this for all the media things that don't work. Thanks! 

P.S. do you prefer the totem plugin or the mplayer plugin for firefox?

Edit: totem-xine-firefox-plugin does play tons of videos from around the net, but does not play Maxim and a popup says it is because it is WMV9. hmmmmmm And purging the mplayer plugin did not help.

---

### Post by slugkilla on 2006-08-24
All the videos on linspire testing area work for me, however, Maxim and the "plugin testing grounds" place still don't work. When using sudo the mpeg link on the testing grounds place works, but everything on that site works with totem-xine-firefox-plugin. So as of right now, that is how things stand and I have no way of watching some embeded stream videos like CNN and Maxim. Thanks for the help.

---

### Post by nalmeth on 2006-08-24
I prefer the mozilla-mplayer plugin.

Hey, if its working, maybe you *should* try
sudo apt-get --purge remove w32codecs

and then reinstall the package from wiki.ubuntu.com/RestrictedFormats

That's really all I can think of, sorry if it doesn't work..

---

### Post by slugkilla on 2006-08-24
I tried that many times. This just seems to be not working. I am stumped. Thanks for all your help though. At least I have xine working again now.

---

### Post by berserker on 2006-08-31
I was able to play videos on cnn.com up until a few days ago.  Now, I receive messages that it's connecting, connected, playing the wmv, then connecting again then it tries a different server and repeats the pattern.  Never does end up playing the video.

Same thing happens at maximonline.  

I have the latest Nvidia drivers, mplayer from cvs and mplayerplug-in.  Trailers and HD clips at Apple and videos at Google play just fine.

Anyone else experiencing trouble with CNN or Maxim recently?

---

### Post by slugkilla on 2006-08-31
This is my exact problem! I'm not alone! I don't know why this happend. Did you do anything before this happend?

---

### Post by berserker on 2006-08-31
The only thing I did was upgrade to the mplayerplug-in that was just released.  So, assuming that the upgrade was broken, I went back to the earlier version but got the same result (constantly connecting but never playing a video).

I think CNN and MAXIM must have changed something about their videos recently.

---

### Post by slugkilla on 2006-08-31
Possibly, but someone within this thread says that they work fine on there comp. Some videos work fine, so i'm doubting it that it is the type of video. It seems to be big websites that have this problem.

---

### Post by berserker on 2006-09-02
> **berserker said:**
> The only thing I did was upgrade to the mplayerplug-in that was just released.  So, assuming that the upgrade was broken, I went back to the earlier version but got the same result (constantly connecting but never playing a video).

I think CNN and MAXIM must have changed something about their videos recently.

I figured out a workaround so that I can watch videos on cnn.com, maximonline.com and Yahoo videos:  For some reason enabling full screen starts the video and then I can go back to normal size and the video keeps playing.  Strange behavior but it works.

---

### Post by slugkilla on 2006-09-03
I tried this and it does not work for me. Can you please step by step describe it?

---

### Post by berserker on 2006-09-03
> **slugkilla said:**
> I tried this and it does not work for me. Can you please step by step describe it?

Sure.  As the pop-up window is trying to connect to the video stream, right click on it and choose Full Screen.  The video should eventually start playing.  You can then right click again and uncheck Full Screen to get the window back to normal size.  Wait for the video to start playing; it might take a minute or two.

---

### Post by slugkilla on 2006-09-03
After playing around with it for a while,(Mplayer that is) I got all the stuff to play with you workaround! This is great. Thanks for telling me about it!

---

