---
title: "Odd mp3 sound issue on Ubuntu"
date: 2007-12-19
forum: General Help
---

### Post by Sohn_of_a_Gunn on 2007-12-19
I am having this odd mp3 issue on Ubuntu, when I play mp3 files, it seems like the playback is odd and has some sort of, well IDK how to describe it but it seems like it loses a layer of audio. An example would be when I play one specific song, at one point there is supposed to be drums, it does not play those drums on the playback, used to, but not anymore.

Sorry for the wall of text but it is an odd issue and needs a good description, anyways please help me ASAP.

---

### Post by rsambuca on 2007-12-19
What bit rate are these mp3's?  mp3's are a lossy compression format, meaning audio data is lost when transcoding to this format.

---

### Post by Sohn_of_a_Gunn on 2007-12-19
Well they are 256 but it was fine before, now it is not good.

---

### Post by rsambuca on 2007-12-19
This is rather strange.  Do you mean that these exact same mp3's sounded OK before?  If that is the case then have you checked your speakers?  Also, try another media player or two.

---

### Post by Sohn_of_a_Gunn on 2007-12-19
> **rsambuca said:**
> This is rather strange.  Do you mean that these exact same mp3's sounded OK before?  If that is the case then have you checked your speakers?  Also, try another media player or two.

Yes it has sounded ok before, well I checked the speakers and tried others, sadly the issue exists still, and I have tried a few more and still some issues.

---

### Post by rsambuca on 2007-12-19
Have you tried these same mp3's on an external mp3 player?

---

### Post by Sohn_of_a_Gunn on 2007-12-19
They sound fine on my iPod, but not on my PC.

---

### Post by rsambuca on 2007-12-19
When you say they sounded OK before, do you mean that they have worked with this exact installation of Ubuntu before?

Also, what about .wav files (CD's), or other audio formats?

---

### Post by Sohn_of_a_Gunn on 2007-12-19
Yes, yes they did. WAV files seem okay to me.

---

### Post by rsambuca on 2007-12-19
If wav files sound OK, then it is obviously not a hardware or driver issue, which means it must be a codec issue.  Try re-installing the mp3 codecs.

---

### Post by Sohn_of_a_Gunn on 2007-12-19
Did, nothing was changed.

---

### Post by Dark Hornet on 2007-12-19
This is just an idea, but have you considered that you may be playing the MP3's in mono instead of stereo?  You may have a setting somewhere...anyway, just something to think about.

---

### Post by Sohn_of_a_Gunn on 2007-12-19
The general settings are in stereo but where else can I change my settings besides with my media player and the default sound configuration on Ubuntu?

---

### Post by Dark Hornet on 2007-12-19
the only other place I would look would be the actual MP3--usually, you can right click (depending on your player) and select properties, etc to see the information regarding that MP3--usually it will tell you the path where it is located, and the bit rate, etc...see if there is anything in there regarding it being stereo or mono, etc.

---

### Post by Sohn_of_a_Gunn on 2007-12-19
I know the mp3 files are in stereo so yeah, the properties will not help.

---

### Post by Dark Hornet on 2007-12-19
wow...well, i am not quite sure what to say...this is an odd issue (good title for the thread..lol).  Do you still have the same issues if your play the MP3s through headphones?--i am obviously scratching the bottom of the barrel here--

---

### Post by Sohn_of_a_Gunn on 2007-12-19
I have tried different speakers and I know it is not a hardware issue, my PC plays WAV files correctly, so sadly, nothing has changed, The mp3 files play right on my iPod and one thing though, it does sound like i am playing a stereo sound on a mono channel, is there anyway to configure an mp3 codec on Ubuntu?

---

### Post by Dark Hornet on 2007-12-19
not to my knowledge...as far as i know all you need to do (read: all I did) was make sure you have the proper dependicies and codecs installed.

---

### Post by Sohn_of_a_Gunn on 2007-12-19
I have libmad installed and the proper stuff for mp3 support on amarok, tried uninstalling and reinstalling, no changes.

---

### Post by rsambuca on 2007-12-19
Try 

sudo apt-get install ubuntu-restricted-extras

---

### Post by Dark Hornet on 2007-12-19
and you said that you have tried other players instead of Amarock--right?  Try Banshee, or Rythmbox, etc.

---

### Post by Dark Hornet on 2007-12-19
> **rsambuca said:**
> Try 

sudo apt-get install ubuntu-restricted-extras



Good call...yeah, make sure you add this.

---

### Post by Sohn_of_a_Gunn on 2007-12-19
> **rsambuca said:**
> Try 

sudo apt-get install ubuntu-restricted-extras

Tried that, did not do anything at all for playback.

---

### Post by Sohn_of_a_Gunn on 2007-12-19
> **Dark Hornet said:**
> and you said that you have tried other players instead of Amarock--right?  Try Banshee, or Rythmbox, etc.

I tried XMMS and Rythmbox, might try Audacious, is that one any good?

---

### Post by rsambuca on 2007-12-19
I found this on some site, although it was talking about Dapper:
> 
Amarok folks pay attention to this: if you use libxine-extracodecs together with gstreamer0.10-plugins-ugly installed, the sound of playing mp3 will become weird. Simply remove gstreamer0.10-plugins-ugly. 

Also make sure you have installed w32codecs.

---

### Post by Dark Hornet on 2007-12-19
I have never tried Audacious...currently I am in the process of finding a new music manager...I keep going back and forth between Banshee, and Rythmbox.

---

### Post by Sohn_of_a_Gunn on 2007-12-19
> **Dark Hornet said:**
> I have never tried Audacious...currently I am in the process of finding a new music manager...I keep going back and forth between Banshee, and Rythmbox.

Have you tried Amarok?

---

### Post by Sohn_of_a_Gunn on 2007-12-19
> **rsambuca said:**
> I found this on some site, although it was talking about Dapper:


Also make sure you have installed w32codecs.

Tried that, still no success:(

---

### Post by rsambuca on 2007-12-19
Well, I am pretty much out of ideas.  Since it was working before, you must have done something to cause these problems.  Perhaps you can go through your apt-get installation logs to see the recent changes and what might have caused the problems.

---

### Post by Sohn_of_a_Gunn on 2007-12-19
The only recent change with mp3 settings I can think of is changing the bitrate on Soundjuicer, I HIGHLY doubt that did a trick through.

---

### Post by rsambuca on 2007-12-19
Yeah, but are you sure you haven't installed another package that is conflicting with the gstreamer or whichever ones you are using?

---

### Post by Sohn_of_a_Gunn on 2007-12-19
I am PRETTY sure but LAME got removed somehow, would that do anything?

---

### Post by Dark Hornet on 2007-12-19
yeah, I have tried Amarock, but I have found that (and this may be because I am using GNOME, and not KDE) after a while, it starts eating up way to much memory, and will crash from time to time.

---

### Post by rsambuca on 2007-12-19
lame, or liblame0?

---

### Post by Sohn_of_a_Gunn on 2007-12-19
> **rsambuca said:**
> lame, or liblame0?

IDK, do I need liblame 0 by any chance, I have libmad 0 installed.

---

### Post by rsambuca on 2007-12-19
I am confused now.  Like I said, it is almost certainly something that you have installed or removed that caused these problems.  Go through your logs and figure it out.

---

### Post by Sohn_of_a_Gunn on 2007-12-19
> **rsambuca said:**
> I am confused now.  Like I said, it is almost certainly something that you have installed or removed that caused these problems.  Go through your logs and figure it out.

I am sorry but the apt get command is not working, says invalid command.

---

### Post by rsambuca on 2007-12-19
Copy and paste your command and the output.

---

