---
title: "Can't get Amarok Help file to work"
date: 2019-06-30
forum: General Help
---

### Post by Ralph L on 2019-06-30
I am running Xubuntu 18.04.  I installed Amarok (the Kubuntu music manager) and amarok.doc, both using Synaptic.  However, I can't get the Amarok Help feature to work.  When I select Help>Amarok Handbook, I get Documentation not Found.  I have installed khelpcenter, and have several Kubuntu apps for which the Help feature works: kb3, digikam, okular, Some Kubuntu apps require being on-line; some don't.  When trying to use Amarok Help, I have been online.

Any help getting amarok Help to work is appreciated........

---

### Post by CatKiller on 2019-06-30
I use Amarok on 18.04, too, because it does things that other media players don't, but it's... pretty much dead. It uses KDE 4, which was a valid thing to do between 2008 and 2014. A big chunk of the users stopped using it after the change *to* KDE 4. That KDE's former default music player didn't make the transition to Plasma Frameworks 5, KDE 4's replacement, in five years means that it's probably never going to. It will be out of place in every environment and drag in massive dependencies on an obsolete desktop environment. *Maybe* they'll get round to rebasing on Plasma 5 before Plasma 5 becomes something else, but I wouldn't bet on it.

Having said all that, the Amarok Handbook (because all the support stuff for KDE 4 isn't used by anything any more) is preserved [here](https://docs.kde.org/stable4/en/extragear-multimedia/amarok/index.html).

I would really like Amarok to move to something supported, although the last mention of progress there was March 2018, or, failing that, for another media player to be able to do the *curated random* smart playlist that Amarok does. Amarok really doesn't function that well in its current state.

---

### Post by Ralph L on 2019-07-01
CatKiller:  Thanks for the response.  Maybe I don't want to use Amarok after all.  I am looking for some way to copy my library of music CDs to a USB disk, so I can play them on my Samsung TV and sound system.  Previously I have done the copy with something that looked up the CD on the Internet and created a nice "cover" for the video part of the player.  It also translated the .wav files to much smaller m4a files. (I think there are less lossy formats so I might not want to use m4a in the future.)  It has been several years, since I did this, but I thought I did it with Amarok.

Can you give me any advice on copying my CDs to a USB disk, how to get the nice "cover" for the video, what format to convert the .wav files to, and what music manager to use???

Thanks.......

---

### Post by CatKiller on 2019-07-01
It could well have been Amarok you used in the past; I think it was one of the first ways available to do library management with iPods in an iTunes kind of way. m4a was, I think, an Apple-popularised way of describing AAC-encoded audio in an MPEG 4 container, used by iTunes. 

> **Ralph L said:**
> Can you give me any advice on copying my CDs to a USB disk, how to get the nice "cover" for the video, what format to convert the .wav files to, and what music manager to use???
For formats, it comes down to preferences and how exactly you'll use them. The playback capabilities of what you're using to play them are a big consideration. 

If you want lossless audio, flacs do exactly that, and that's how I archive my cds where storage is plentiful. They come out at around 10 MB per minute of audio.

If you need lossy compression because space is constrained, both ogg and mp3 are about the same for size and quality at about 1 MB per minute of audio. Ogg has freer licensing, but mp3 is more widely supported by proprietary devices.

In my case, it's all really easy because I use a NAS which works as a media server on its own. It has plenty of storage, so I just use flacs to store them, and it's able to just send the file if the receiving device supports flacs, or transcode them on the fly to either another format that the receiving device supports or an audio stream. So I just don't have to worry about any of it any more.

Clementine might be a good choice as a substitute for Amarok - it was modelled on Amarok from before Amarok's move to KDE 4.

Otherwise there are quite a few to choose from, ranging from bare cd rippers to full-on library managers like Amarok. There are lots of cd rippers in the middle ground that will fetch cover art and store it either in the same folder as the file or in the file's tags; I couldn't recommend a specific one.

Even if the file doesn't have cover art stored with the file many media players will be able to fetch that on playback. Amarok, Kodi and Volumio, which are the ways I play back my music library, can all do that, which is why I don't have any information about doing it at the ripping stage.

---

### Post by Ralph L on 2019-07-09
I took the advice to install Clementine, but to get it to work right I compiled from source.  See [https://ubuntuforums.org/showthread.php?t=2422498&p=13871796#post13871796](https://ubuntuforums.org/showthread.php?t=2422498&p=13871796#post13871796) .

---

