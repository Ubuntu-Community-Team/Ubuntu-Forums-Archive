---
title: "My python script stopped working from 1st of November onwards, did anything change?"
date: 2020-11-04
forum: General Help
---

### Post by themeditationcenter on 2020-11-04
Hi,
I have a simple python script for my non profit organization whom I am helping with IT stuff. A simple script to play random playlist at a specific time.
It was working fine till now and all of a sudden from November 1st, 2020  onward it stopped working. No error messages too. It just stays in a hung state.

My code can be found [here]("https://paste.ubuntu.com/p/4bwjZccRFG/").

But please note the code worked from 2018 all the way till now, why all of a sudden on Nov1st it stopped working? Is ubuntu blocking anything? 
I use kubuntu and is current.
Version: 20.04

Let me know if you need any further info.

Any help on this is really appreciated.

With hopes

---

### Post by TheFu on 2020-11-04
fix the xdg-open.

---

### Post by themeditationcenter on 2020-11-04
> **TheFu said:**
> fix the xdg-open.

How do I go about doing it?

---

### Post by SeijiSensei on 2020-11-05
[https://linux.die.net/man/1/xdg-open](https://linux.die.net/man/1/xdg-open)

---

### Post by TheFu on 2020-11-05
My script that plays audio playlists doesn't use xdg-open.  

I just use /usr/bin/mpv as the player.  Think I posted my script here a few months ago. 

I suppose there's a way to tell xdg to use mpv as the player for audio playlists.  Sorry, I have no clue how to control which apps are setup for the different mime-types.  I'd guess using a file manager and "opening" one of the playlists will open a dialog to choose the application to be used. That's just my guess, but I don't really know.  I haven't used a file manager in months.

---

### Post by themeditationcenter on 2020-11-06
so basically my below line of code is causing issues
> 
        opener ="open" if sys.platform == "darwin" else "xdg-open"
        subprocess.call([opener, pathToPlaylist])

so xdg-open is blocked from november 1st onwards by Kubuntu/Ubuntu? Is that the take away?
So any script which uses xdg-open need to modify their scripts?
Sorry for all these questions, just want to make sense of this. This worked so well till now and then all of a sudden it stopped working.
The only thing which happened could be auto updates to the machine. Not sure if any new updates were pushed by Ubuntu to block xdg-open?

---

### Post by TheFu on 2020-11-06
I would guess that some update to an audio program reset or removed the default application for xdg-open audio mime-types.

If you double click on a playlist manually using the GUI (somehow), then you should be asked to choose an application to be the default for audio mime-types.

Nothing sinister happening.  If you install another web browser, wouldn't it be nice to be asked which browser you'd like xdg-open to use to open HTML files going forward?  That's all this is ... probably.

You can read up on xdg-open ... google should find lots of references or there are always the manpages - both on the system and google will find some too.  On one of my systems, the headline from the xdg-open manpage is this:
> xdg-open - opens a file or URL in the user's preferred application

---

### Post by The Cog on 2020-11-06
I would ask if the sound plays when the file is opened manually. 

All of a sudden, my laptop sound stopped working in the last few days, and it seems to be a problem with pulse audio not seeing the sound card even though the underlying alsa can see it. See [https://ubuntuforums.org/showthread.php?t=2453293](https://ubuntuforums.org/showthread.php?t=2453293) for reference. Yours may be the same problem. Or it may be coincidence.

---

### Post by themeditationcenter on 2020-11-07
Thank you "The Fu" and "The Cog" for your prompt response.

When I double clicked on the playlist, it just opens with the default application as expected (which is clementine)

And yes the sound plays normally when the file is opened manually.

I think I can zero in on the xdg-open. I'll try to get an alternative way of opening the music player from my script and see how it fares.

---

### Post by TheFu on 2020-11-07
Sound playing is good.
Clementine working is good, but if nobody is logged into the system and the script tried to start a GUI program when there isn't any X/Session, then it won't work.  I know Clementine has a client/server mode, but don't know anything more about that.  I do know that mpd works fine in daemon mode and doesn't require any userids logged in.  PulseAudio is tied to the X/Session for some reason.  There is a way around that, but I think it is a hassle and sometimes crashes the pulseaudio daemon.

I don't know if this is helpful or not and I would avoid using it, but [https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/SystemWide/](https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/SystemWide/)

---

### Post by themeditationcenter on 2020-11-07
Thank you TheFu, I figured it out.

It was a logic failure in my script. It was nothing to do with the audio nor xsession. The logic of the script is supposed to reset a temp file and it failed there.

As always, no words to describe my gratitude to you all.

---

### Post by themeditationcenter on 2020-11-07
Thank you all for your time and energy to walk me through this.
The issue was with the logic of my Script. After the script plays all the playlists in the folder, it resets a tmp file. This is where it failed.

Long story short - the issue was just with my script and nothing to do with audio or xsession.

But please don't get me wrong, my extreme gratitude to "TheFu", "The Cog", "[[COLOR=#000000]SeijiSensei[/COLOR]]("https://ubuntuforums.org/member.php?u=698195")" and others who took time to explain the nitty gritties of Ubuntu and Linux. It was a learning experience for me.

---

