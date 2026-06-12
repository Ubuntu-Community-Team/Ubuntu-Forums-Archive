---
title: "Weird: Sound file won't play in Ubuntu"
date: 2007-12-23
forum: General Help
---

### Post by dlegend on 2007-12-23
**Problem has been resolved -- possible BUG in login window preferences**
Hey -- just wanted to give another update. After a LOT of configuration I actually found out my problem has to do with the configuration of the login window preferences. For SOME strange reason if I set my login sound to the custom file (that won't play) then a lot of problems occured as I stated in my later posts (read full thread). I have absolutely NO clue why but this is a really weird bug...

I was able to reset all my sound settings to Autodetect and everything works perfectly.

I want to know if anyone else has this problem? Try this:

1. First download this sound file: [http://simplythebest.net/sounds/WAV/events_WAV/event_WAV_files/startup.wav](http://simplythebest.net/sounds/WAV/events_WAV/event_WAV_files/startup.wav)
2. Now go to System > Administration > Login Window.
3. Go to "Accessibility tab". Check "Login screen ready" under the sounds area and select the sound file you have just downloaded.
4. Try playing the sound (it shouldn't work).

Now save the settings and close. Try rebooting/logging out. Now log back in. This is where all my problems started happening!

I don't know if there is any direct correlation or if somehow my stuff just started working again. But I know that the sound file still won't play at the login screen (for some odd reason).

---

### Post by ed-koala on 2007-12-23
Have you got the gstreamer package installed?  I believe that will allow you to play wav files and other formats such as mp3 too, which are not built into Linux by default due to licensing issues.

---

### Post by dlegend on 2007-12-23
I believe so -- if you could direct me with the commands so I can be sure that I have everything set up properly. I just found out that other system sounds aren't working when I try to play them, though they work when the system plays them. What's weird though is I can play mp3s fine in Amarok.

Edit: I think I just screwed up my codecs/sound-related stuff somehow..

---

### Post by ed-koala on 2007-12-23
Here is what I have installed ...
Go to System - Administration - Synaptic Package Manager ... you will have to input your password.   Click Search ... look for "gstreamer".   Once a list pops up, here are the packages I have installed ...
gstreamer0.10-alsa
gstreamer0.10-esd
gstreamer0.10-ffmpeg
gstreamer0.10-gnomevfs
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-a
gstreamer0.10-plugins-good
gstreamer0.10-plugins-ugly
gstreamer0.10-x

Those should get you running all sound formats in your programs.  :)

---

### Post by dlegend on 2007-12-23
I'll try it out, thanks for the help so far. I have no clue what I did to screw things up xD

I've done a lot of customization to my system and screw things up from time to time and get frustrated xD

---

### Post by ed-koala on 2007-12-23
Tell me about it, I tried getting 3 fancy Compiz plugins and ended up spending 6 hours getting my system back to as it was.  But, I learned a lot in the process! lol

---

### Post by dlegend on 2007-12-23
I seem to have all the packages installed. I tried re-installing them just now. Also by "gstreamer0.10-plugins-base-a" -- I assume that is "gstreamer0.10-plugins-base-apps", correct?

---

### Post by dlegend on 2007-12-23
Just the other day I was able to play videos via VLC player but now it seems like it will start but then freeze on me. Also when I go to Sound Preferences the Sound playback works fine for sound events but it doesn't seem to work for music/movies. I have no clue why =/

Whatever I try to play sounds in seem to freeze up.

---

### Post by ed-koala on 2007-12-23
Correct, I didn't have my column wide enough :)  Still looking for answers for ya tho.

---

### Post by ed-koala on 2007-12-23
What type of computer / sound card do you have?

---

### Post by dlegend on 2007-12-23
Hmm, while I was frustrated I had installed libxinel-ffmpeg and some other stuff. I just went into synaptic and it said I had totem-xine and not totem-gstreamer. I installed totem-gstreamer and got rid of totem-xine if that could have anything to do with the problem...

As for my comp/sound card I have a Dell Latitude D600 -- sound card I'm not sure about. Not sure what my sound card is in the device manager.

---

### Post by dlegend on 2007-12-23
YES! I got it to work! Somehow For the Music and Movies section in Sound Preferences it was set to Autodetect which failed to detect it -- I changed this to OSS and now everything works fine! Thanks for your help =)

---

### Post by dlegend on 2007-12-23
Hey -- just wanted to give another update. After a LOT of configuration I actually found out my problem has to do with the GDM configuration. For SOME strange reason if I set my login sound to the custom file (that won't play) then a lot of problems occured as I stated earlier. I have absolutely NO clue why but this is a really weird bug...

I was able to reset all my sound settings to Autodetect and everything works perfectly.

All I can say is I think I found a bug and I think it is something that may need to be addressed?

---

### Post by dlegend on 2007-12-23
OK sorry for the many posts in a row I've been making but I made updates to the original post to explain the situation... It might not make a lot of sense at this point xD

---

### Post by seuzy13 on 2008-07-22
What exactly are the steps you took to fix this problem? I am having the same problem, too. If I restart my computer, audio files will play for a while, but at random intervals all of my media players refuse to move forward and won't begin playing an audio file. Very annoying having to restart my computer all the time!

I don't have a custom file set for my login window, but it seems to be the same problem.

Thanks!

EDIT--Ahah! Changed the sound preferences from auto detect and it worked.

---

