---
title: "Audio Streaming"
date: 2014-03-25
forum: General Help
---

### Post by Quarkrad on 2014-03-25
I've installed icecream as it appears to split an audio stream into individual tracks - but as a newbie I'm struggling and got no where so far.  Is there anything gui based for Ubuntu that will list/save individual audio tracks?  (I am trying to find out what songs are played on a weekly bbc radio show - unfortunately 'they' do not provide a playlist.  However, I can record the stream so in theory I could find out.  It would be an advantage if some software could extract the songs rather than me have to do it in real time.  Icecream has a -t option that looks to do it but I cannot get it to work).  Thanks.

---

### Post by philinux on 2014-03-25
Moved to general help forum.

---

### Post by QDR06VV9 on 2014-03-25
> **Quarkrad said:**
> I've installed icecream as it appears to split an audio stream into individual tracks - but as a newbie I'm struggling and got no where so far.  Is there anything gui based for Ubuntu that will list/save individual audio tracks?  (I am trying to find out what songs are played on a weekly bbc radio show - unfortunately 'they' do not provide a playlist.  However, I can record the stream so in theory I could find out.  It would be an advantage if some software could extract the songs rather than me have to do it in real time.  Icecream has a -t option that looks to do it but I cannot get it to work).  Thanks.

I think you wil be pleased with [guayadeque]("http://ubuntuforums.org/showthread.php?t=1398128") post#1 How to
You will then have to setup your Recording Options
Screenshots also
1st. Enable recording(tick the enable recording option)
If you need more help I will try to stick around for a bit.

---

### Post by HermanAB on 2014-03-25
Yu could use Streamtuner.  It includes Streamripper.  I use it to make USB sticks with music to play in my car.

---

### Post by Quarkrad on 2014-03-25
Thanks for the Guayadeque link - it looks good.  My only problem is it keeps telling me I have a GStream error:  a missing plugin.   I have googled and this looks a nightmare - I have most and install a few more but I keep getting the missing plugin error (I have restricted-extras).

---

### Post by QDR06VV9 on 2014-03-25
> **Quarkrad said:**
> Thanks for the Guayadeque link - it looks good.  My only problem is it keeps telling me I have a GStream error:  a missing plugin.   I have googled and this looks a nightmare - I have most and install a few more but I keep getting the missing plugin error (I have restricted-extras).
I'm going to assume here that you followed that how to a tee(Compiling and all successfuly)
On opening the player in the tab section you will see Sources + Veiw + Help
Select the View tab go down to the bottom and Select Preferences.
Next off to the Left as seen in attachment scroll to find Playback and select that.
Next off to the Right towards the bottom you will see Output device with a dropown select 
and simply choose one that works. May I suggest Pulse or Alsa.
If that don't get you happy send me the URL of the stream your using
They also have a Forum [HERE]("http://guayadeque.org/index.php?p=/discussions")
Regards

---

### Post by 3rdalbum on 2014-03-26
If the purpose of all this is to find out what songs are being played on the radio show, there is an easier way.

On a smartphone or tablet, install an app like Shazam or Soundhound. It will listen to a song that is playing and identify its name and who is performing it.

---

### Post by Quarkrad on 2014-03-26
**3rdalbum** - this is exactly what I want to do,  I will try these apps, many thanks.  **runrickus** - attached screenshot of what is happening but I have a possible clue.   Setting the playback options made no difference so I have left it on Auto.  The url for BBC 2 I'm using is **[http://www.bbc.co.uk/radio/player/bbc_radio_two](http://www.bbc.co.uk/radio/player/bbc_radio_two)**  which works if you use a browser.  However, I tried the **tunein** option and selected local radio and the player is currently playing **[http://media-ice.musicradio.com/SmoothHampshireMP3](http://media-ice.musicradio.com/SmoothHampshireMP3)** so the player is working OK.  Interestingly(?) when the scanning was complete for the local radio stations there were no BBC stations - so perhaps my problem is not with guayadeque but with the fact that I'm trying to play a bbc station.

---

### Post by Quarkrad on 2014-03-26
Cracked it!   I was using the wrong URL - the correct one (for BBC Solent is [http://bbc.co.uk/radio/listen/live/bbcsolent.asx](http://bbc.co.uk/radio/listen/live/bbcsolent.asx)) - the correct one for radio 2 is [http://bbc.co.uk/radio/listen/live/r2.asx](http://bbc.co.uk/radio/listen/live/r2.asx).  Many thanks for your help.

---

### Post by QDR06VV9 on 2014-03-26
Good Job Quarkrad I also found a page for more BBC Radios [HERE]("http://www.listenlive.eu/uk.html")
I had to right click and save the windows media player button.

---

