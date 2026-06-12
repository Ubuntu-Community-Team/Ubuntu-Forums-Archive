---
title: "Bringing my system up to speed after Hardy upgrade"
date: 2008-04-27
forum: General Help
---

### Post by Replicon on 2008-04-27
Hi,

After running the 7.10 to 8.04 upgrade, I seem to have lost some software (e.g. XMMS). Is this because it disabled some repos? If so, can I just re-enable them and update/upgrade, or do I have to painstakingly install everything from scratch after every dist-upgrade?

In particular, I'd rather not have to do everything in [the media/streaming thread](http://ubuntuforums.org/showthread.php?t=661833) after every single dist upgrade (yeah it's once every 6 months, but still...) ;)

---

### Post by ryanhaigh on 2008-04-27
I don't think xmms is available in the hardy repos although I did see this thread mentioned elsewhere, apparently there is a deb in there that will install. I have to ask though have you considered an alternative that is actually developed like audacious or beep-media-player.

That/or the newer version is a pretty comprehensive howto but I notice that it asks you to add some third party repos, this will almost always cause issues when doing an upgrade. If you really need to use that method rather than just installing ubuntu-restricted-extras and the other packages from the official repos then I would guess that you probably do unless you can re-add the mediabuntu repo for the new release before doing the upgrade. Perhaps you should ask in that thread about how to avoid having to do it all again every release.

---

### Post by Replicon on 2008-04-28
Ah, I didn't realize XMMS was no longer in development. Truthfully, I'm not sure how much of my stuff came out of medibuntu. Everything else I've played with seems to work (except MP4 playback). I'm definitely open to something that's more supported, so long as it has the same kind of un-intrusive demeanor as XMMS had. I guess I stuck with it because that's what I used to use 5 years ago (and it looks and feels like winamp).

What do the ubuntu-restricted-extras contain, that I might be interested in? hopefully my mp4 files will start working again...

<rant>So long as we're talking about alternate players, what is it with the video progress bar thing of most linux players (including VLC), where clicking somewhere doesn't seek to that location, but either skips an arbitrary amount of time (VLC) or just does... nothing (Totem). I can't find any "enable go where I told you to go" option in the configs :D </rant>

---

### Post by ryanhaigh on 2008-04-28
Ubuntu restricted extras installs codecs, fonts, java, flash, rar/unrar and probably more. Its a nice one stop shop to get all the stuff they can't include by default but everyone needs. Although you may still need to add libdvdcss2 or whatever its is (I haven't used retail video dvds in some time)

Audacious and beep are both winamp2 like which is why I suggested those specifically.

As for you rant, I feel your pain, although I do sometimes find similar issues in windows with some video files (they just CANT skip ahead at all). The easiest way to do the seeking is to drag the indicator or press where you want and hold it for a while. I can't be sure as Im not on my ubuntu system at the moment bug gnome mplayer might do what you want.

---

### Post by Replicon on 2008-04-28
Ah, audacious != audacity *headdesk* Yes, thank you, that's much better hehe.

---

