---
title: "Embedded media plugin for Firefox?"
date: 2007-05-18
forum: General Help
---

### Post by Zeikcied on 2007-05-18
I run Kubuntu.  And I currently use the Kaffeine plugin for Firefox for handling embedded media.  And I'm wondering if there is something that will remain embedded in the browser?

See, unless I'm missing some configuration, the Kaffeine plugin simply loads the main Kaffeine player, and plays the media in that.  I know that there is a VLC plugin for Firefox, but as I recall, that didn't give me any control interface.

All I want is something that embeds itself in the page to play the media, much like the Windows Media Player and Quicktime plugins on Windows.  With some form of control interface.

Is this possible?

On a side note, how do I get the current song info out of Kaffeine (with the Xine engine) via the command line?

Thanks.

---

### Post by reckless2k2 on 2007-05-18
I'm not sure we are talking about the same thing or not but remove the kaffeine plugin and install the mplayer plugin. If i'm thinking what you looking for will be with that plugin.

---

### Post by gavintlgold on 2007-05-18
The mplayer plugin works very nicely, with controls and an awesome fullscreen mode. You should be able to synaptic that.

---

### Post by Zeikcied on 2008-02-07
I know I'm bringing up an old topic of mine, but I wanted to follow up on this.

Are there any other alternatives?

I've had the MPlayer plug-in for a long time.  While it does its job, and it has the features I want, there is one major annoyance of it.  The plug-in seems to demand full control over the sound adapter.  Meaning I can't have any other sounds playing on top of it.  Personally, I don't understand why some Linux programs are like this, while others aren't.  I figured that, as a matter of personal convenience, that all Linux programs would share the sound adapter by now.

Anyway, this becomes a real annoyance when I stream audio shows from a favorite website of mine.  They have regular audio shows.  Not really a podcast, but they're available for streaming or download.  I choose streaming, because it saves space from downloading every show.  But, when MPlayer is playing the show (which can sometimes be longer than an hour), I can't go to any sites with flash-based content.  (Granted, a handful of sites work, like Homestarrunner.com, but most won't.)  If I attempt to go to those sites, Firefox freezes completely until MPlayer is done playing the audio file.  So I either have to kill Firefox, or wait until the audio show is over.

I've tried the Kaffeine plug-in, but the last time I used it, the plug-in only launched Kaffeine and opened the file in the main player.  I don't know if that's changed, but I doubt it.  The VLC plug-in, last I tried it, had no controls at all.  Again, I don't know if that's changed or not.

I'm really hoping for an alternative to the MPlayer plug-in, or at the very least a solution to the problems it's been giving me.

---

### Post by hyperair on 2008-03-08
You need to change the audio output plugin of MPlayer to use ALSA or ESD. Option's available by right clicking on the plugin control when it appears in Firefox.

---

