---
title: "lost audio preview feature"
date: 2007-10-21
forum: General Help
---

### Post by ZERO_SHIFT on 2007-10-21
After installing Gutsy I lost the feature of being able to preview sound files without opening them (ie by just pointing the mouse on the)

Is there a way of getting this feature back?

Thanks

---

### Post by NeoLithium on 2007-10-21
In a nautilus window, go to EDIT -> PREFERENCES and click on the preview tab.  You can set the preview up in there :)

---

### Post by bluedog800 on 2007-10-21
I also had the same problem, in preferences, preview mine was already set to "Always"

any other suggestions?

Thanks

---

### Post by isecore on 2007-10-21
Same problem here. My Feisty-system previewed audio-files just fine, but after upgrade to Gutsy this feature went awol. I too have "always" checked on all file-types, but no dice when trying to get a preview.

---

### Post by ZERO_SHIFT on 2007-10-21
> **isecore said:**
> Same problem here. My Feisty-system previewed audio-files just fine, but after upgrade to Gutsy this feature went awol. I too have "always" checked on all file-types, but no dice when trying to get a preview.

I confirm the problem it does not seem to work.

Any ideas?

---

### Post by simpsonatwork on 2007-10-22
I have exactly the same problem. Gutsy upgrade leads to audio preview lost.

---

### Post by Colsta on 2007-10-22
Yes, unfortunately I am experiencing this problem with a completely fresh Gutsy install.  For the record, all features in Nautilus are enabled for file previewing - text and graphical files work fine, just no audio previews of any file type on mouseover.  Yet the same audio files play fine in their respective default handlers.

I did try previous Ubuntu version fixes out of curiosity but without much hope e.g.
sudo aptitude install mpg321 vorbis-tools sox
but this resolved nothing.

So anybody got any further thoughts?

---

### Post by bionnaki on 2007-10-22
sudo apt-get install pulseaudio-esound-compat

do that. and reboot.

---

### Post by bluedog800 on 2007-10-23
bionnaki,

That did not seem to solve it for me,  did this solution help others??

Thanks

---

### Post by chrisccoulson on 2007-10-23
Yes, that fixed it for me. I think I also installed the music123 and mpg123 packages as well though. I have since removed pulseaudio though, as I have a problem with pulseaudio not terminating when a user logs out, leaving no sound for the next user.

---

### Post by isecore on 2007-10-24
> **bluedog800 said:**
> bionnaki,

That did not seem to solve it for me,  did this solution help others??

Thanks

Worked fine for me. I have not noticed any negative aspects of using PulseAudio yet.

---

### Post by spedoinkle on 2007-10-24
wow,  "sudo apt-get install pulseaudio-esound-compat" worked great. i also have mpg321 and vorbis-tools already, so if the above doesnt work, sudo apt-get install mpg321 vorbis-tools

:twisted:

---

### Post by ricardisimo on 2007-10-24
No luck here, not with mp3s nor - quite surprisingly - with ogg vorbis. Any idea what's up? I always thought it was a nice, time-saving feature, and I'd like to have it back. Thanks in advance.

P.S. - Curiouser and curiouser. Neither XMMS, nor Beep nor Audacious will play audio files, but all of the broader "Media Players" will: Rhythmbox, Exaile, Amarok, Banshee, what have you. The former give this error - ```
Couldn't open audio.

Please check that:
1. You have the correct output plugin selected.
2. No other programs is blocking the soundcard.
3. Your soundcard is configured properly.
```
Any ideas?

---

### Post by Colsta on 2007-10-24
> **bionnaki said:**
> sudo apt-get install pulseaudio-esound-compat

do that. and reboot.

Thanks for the suggestion.  That had the effect of adding the musical note symbol to each file on mouseover (which I didn't realise was missing), but still no preview sounds.

Unfortunately, doing this has messed up ALSA.  I can no longer multiplex sounds from different applications (like Skype and Totem).  Now when I test the sounds in System|Preferences|Sound, I get 'gconfaudiosink: Resource busy or not available' for each option.

Will have to revert.

---

### Post by Nunu on 2007-10-24
Worked like a charm for me thanks guys

---

### Post by ricardisimo on 2007-10-24
pulseaudio is almost certainly the culprit. I won't be installing it here at work, for sure. Another problem I just noticed (this on the work comp, where I have yet to try anything): the panel volume control has no effect on, say, Audacious. To the contrary, if I lower the volume on Audacious, XMMS or Totem, for example, it lowers the volume on the entire system. I'm pretty sure that's not supposed to happen. Any ideas on either of my problems? Thanks.

---

### Post by Colsta on 2007-10-24
> **ricardisimo said:**
> pulseaudio is almost certainly the culprit. I won't be installing it here at work, for sure.

I certainly don't blame you.  I thought everything was meant to be converging to play nicely with each other using ALSA anyhow?

I'm a bit loathe to go back to the old days of several sound servers to get stuff working (not that the pulse fix worked for me anyways).  It's an annoying bug, and I'll be pleased to hear of anyone fixing it.  But it's not that much of a deal that I'd be prepared to break everything else that's working nicely with ALSA just to get it working.

---

### Post by MyR on 2007-10-24
bug report here

[https://bugs.launchpad.net/ubuntu/+source/mpg321/+bug/125739](https://bugs.launchpad.net/ubuntu/+source/mpg321/+bug/125739)

none of the solutions have worked for me however

peace

---

### Post by ricardisimo on 2007-10-25
Thanks for the bug report. It may have helped. I completely removed pulseaudio-esound-compat and esound, as well as reinstalling mpg321, vorbis-tools and sox... just in case. Didn't work, because there is no preview without ESD, aka esound. So, I reinstalled just esound and I now have previews, albeit in a really buggy way; I have to mouseover repeatedly and in a bizarre, aggressive manner to get it to sample. Mind you, I have yet to reboot (don't want to interrupt my current downloads), so I'm hoping it's a tad more well-behaved next time 'round. I'll try to follow up here either way.

---

### Post by logos34 on 2007-10-25
mpg123-esd was the key for me.  Until I installed it I was getting the popup note but no sound on mouseover.

mpg123-esd
pulseaudio-esound-compat

But when attempting to normal playback with media players (everything except Rhythmbox) I was getting this error message:

> Couldn't open audio.

Please check that:
1. You have the correct output plugin selected.
2. No other programs is blocking the soundcard.
3. Your soundcard is configured properly.


So I had to change Audacious and Amarok audio prefs to use the **pulseaudio output plugin.** Pulseaudio says it's a high-quality, low-latency sound server...hope sound quality is as good as Alsa.

-----------------

*Update:

Went back to **esound** (uninstalled pulseaudio) and now I have mouseover sound preview AND normal playback on media players using default Alsa 1.3.5 output plugin.   Nautilus preview is now working as it was in feisty.  :)

[B]> mpg123-esd
esound[/B]

I had to **reboot** for changes to sound server to take effect.

---

### Post by MyR on 2007-10-25
thank you logos43! this worked for me

---

### Post by Colsta on 2007-10-25
Thanks Logos34 - these were the critical packages that got everything working (after a reboot) for me too.

>   sudo apt-get install mpg123-esd esound Just for the hell of it, I tested by previewing sounds on mouseover concurrently with a movie playing, Rhythmbox playing AND firefox playing a youtube film.  I am still puzzled as to what exactly has been fixed in this scenario - or more precisely, why Nautilus was broken to begin with.  I thought the Gutsy release was meant to use gstreamer which output through ALSA (or have I got this mixed up - no pun intended).  Obviously Nautilus was coded to use components that just weren't included in the standard release.

Would you mind feeding this fix back into the launchpad bug mentioned by MyR ([http://tinyurl.com/2mjrbw](http://tinyurl.com/2mjrbw)) so that the devs can get a handle on it and maybe others benefit too?  I would do it, but the glory is yours :)

Cheers!

EDIT: As a bonus, the Ubuntu logout sound now works, too - another minor bug cleared up.  Obviously Ubuntu still depends on ESD to some degree.

---

### Post by ricardisimo on 2007-10-25
Worked here as well. A fine job done by all, and special kudos to logos34! One minor kink: mp3s get sampled immediately, while oggs take a bit longer. Test it out yourselves. Put an album's worth of each in separate folders (one for 10-20 oggs and another for 10-20 mp3s) and mouseover in each. perhaps vorbis-tools is just a much bulkier program than mpg123, but it really does take quite a bit longer... at least on my machine.

Thanks again.

---

### Post by logos34 on 2007-10-25
> **Colsta said:**
>  I am still puzzled as to what exactly has been fixed in this scenario - or more precisely, why Nautilus was broken to begin with.  I thought the Gutsy release was meant to use gstreamer which output through ALSA (or have I got this mixed up - no pun intended).  Obviously Nautilus was coded to use components that just weren't included in the standard release.

This is the only explanation I've come across:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/153391](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/153391)

Doesn;t make much sense to me.

---

### Post by Colsta on 2007-10-26
Oh Lordy, Lordy.  Looks like I celebrated too quickly :)
I get .wav and .mp3 previews, but not .ogg :(  I forgot to check the examples in my home directory :(  I didn't have any flac samples, so i downloaded one and it doesn't preview either.  All I get is the note symbol pop up and a long wait.......

I have got sox and vorbis-tools installed.

---

### Post by logos34 on 2007-10-26
I have preview on mp3, ogg and wav...never had it on my lossless files--flac and apple lossless/alac/m4a.

---

### Post by simpsonatwork on 2007-10-29
Thanks logos34, installing esound and mpg123-esd worked great.

---

### Post by bojo42 on 2007-10-30
To summarize:

You need **esound** for generell preview capability in Nautilus.

**mpg123-esd** or ** mpg321** for mp3 support (although the first has less cpu-usage)

**vorbis-tools** for ogg vorbis support

**sox** for wav support (aiff, voc, snd, au, gsm should also work, but i didn't test them)


so let's keep crawling through our music files :guitar:

---

### Post by freanir on 2007-11-01
The Preview is working. But, what do I have to install, to enable FLAC-preview?

---

### Post by logos34 on 2007-11-01
> **bojo42 said:**
> You need **esound** for generell preview capability in Nautilus.

**mpg123-esd** [COLOR="Red"]or[/COLOR] ** mpg321** for mp3 support (although the first has less cpu-usage)

**vorbis-tools** for ogg vorbis support

**sox** for wav support (aiff, voc, snd, au, gsm should also work, but i didn't test them)


with the stress on 'or'...I had ogg preview on mouse-over working just fine, then at some point I installed mpg321...the next time I checked it I had lost preview on hover! (although it worked if I highlighted the file first).  Finally by a process of elimination I narrowed the culprit down to mpg321--I think it conflicts with ogg123 (included in vorbis-tools) which handles ogg preview.  Uninstalled it and now hover preview on ogg works normally.

---

### Post by VON_CAPO on 2007-11-01
It works great. Thanks. :)

There is an exception: "wma" files do not work. :(

---

### Post by oldsmobile_mike on 2008-01-05
Thanks, all!  Just wanted to confirm that this fix works for me, as well.  What a PITA, having to install all those packages, though!  :-(

PS - getting wav support required a reboot, mp3's started playing right after the killall, however.

---

### Post by rahimveron on 2008-01-06
Yes installing esound and mpg123 got the preview back working. Thanks everyone.

---

