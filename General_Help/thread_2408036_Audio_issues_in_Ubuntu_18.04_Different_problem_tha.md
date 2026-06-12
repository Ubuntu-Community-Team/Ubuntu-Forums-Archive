---
title: "Audio issues in Ubuntu 18.04: Different problem than others have had"
date: 2018-12-12
forum: General Help
---

### Post by druidkat7 on 2018-12-12
Hey, everyone! :-)

I recently installed Ubuntu 18.04 about less than a month ago, via the Ubuntu software center, as opposed to the disk, which is what I normally use. About two days ago, I did a major update to my software, likely the second update since installing 18.04. 

Before the update, the sound on my laptop, an HP Elitebook, worked fine. I could listen to all my usual YouTube channels in either Chrome or Firefox, via headphones or not. 

After the update, however, this is what's going on: 

1) There are specific YouTube audios, in BOTH Firefox and Chrome, that sound choppy and distorted in my headphones, and ONLY my headphones, regardless of which type of headphones I use, be it my fancier noise-cancelling ones, or my earbuds. If I take the headphone plug out, and I listen via my laptop's main speaker, or my Wonderboom (portable Bluetooth speaker), then the sound is all good. No problems. Which made me initially think something is wrong with the hole for the headphones, such as temperature extremes might have gotten to it. (I've been carting my laptop back and forth to the library and restaurants, from below-freezing temps to the warmth of the buildings I go into.) But this doesn't make sense because it was quite cold on the day I did the update, and the audio in my headphones was working just fine. It was after the update I started having problems.

2) Some of the videos I've watched in the "choppy/distorted" list are, interestingly enough, those of the high-profile channels I like such as "Late Show w/Stephen Colbert," "Daily Show w/Trevor Noah," etc. Some videos that feature famous music or shows, such as "Riverdance," (for example), are affected by this distortion as well. 

3) Audios in my favorite meditation/relaxation channels don't seem to be affected by this distortion at all, and neither is the audio output on Twitch, on which my boyfriend currently has been streaming his "Let's Play" videos, complete with webcam. I can hear his audios just fine in my headphones. 

My scant research up to this very moment revealed the possibility of a system-wide bug caused by a typo, resulting in the PulseAudio code not "reading" or "interpreting" MP4 files correctly. I also read very briefly where ALSA is, for some reason, now considered obsolete, but I'm not sure why such a change would be made if it was serving people reasonably well. Can anyone elucidate or disprove any of this for me, as it's been a while since I've been in here, and to be honest, I don't often come here unless there's a problem. 

So my question is: if there is a bugfix, is it a relatively simple one, or am I gonna have to jump through a lot of hoops? 

If the bugfix isn't all that simple, then I'm gonna switch to Mint for a time, until Canonical fixes this--unless they already have and I just haven't found the solution via my scant research. :P I was thinking I'd get the 18.04 disc and reinstall that way (I installed 18.04 via the software center, thus I was under the impression that this audio issue was due to my having updated without a disc, i.e. corrupted files from the get-go), but apparently, that won't solve my problem because I think I would still have to deal with that fateful update soon after.

This audiophile would love to hear solutions and ideas, because my research for my particular problem has come up dry.

---

### Post by Autodave on 2018-12-12
I am assuming that you *upgraded *to 18.04 rather than doing a clean install?  I rarely find that upgrading works.  It is usually quicker and easier to just do clean installs.

---

### Post by CatKiller on 2018-12-12
> **druidkat7 said:**
> I also read very briefly where ALSA is, for some reason, now considered obsolete, but I'm not sure why such a change would be made if it was serving people reasonably well.

ALSA is very much the way that Linux interfaces with sound hardware. It's just that *configuring* ALSA directly is only for lunatics and masochists. PulseAudio is just flat-out better in every way for that. ALSA controls the hardware, PulseAudio controls the audio streams.

The fact that it's only a single output that's affected shows that it's not a systemic problem. You say that it's only some content that's affected: is it only loud content? Having the output level too high for just that output could cause clipping that wouldn't be in anything else.

---

### Post by druidkat7 on 2018-12-12
> **Autodave said:**
> I am assuming that you *upgraded *to 18.04 rather than doing a clean install?  I rarely find that upgrading works.  It is usually quicker and easier to just do clean installs.

You're right: I did do an upgrade instead of a clean install, mostly because I wanted to see if my system would behave any differently, re: any possible bugs, etc, and because I was running a bit tight on funds, temporarily. Otherwise, I would have ordered a disc, as I usually prefer. Now that I know that a fresh install from a disc is easier all around, and my little "experiment" more or less failed, I'm gonna get me a disc and do a complete reinstall.

---

### Post by druidkat7 on 2018-12-12
> **CatKiller said:**
> ALSA is very much the way that Linux interfaces with sound hardware. It's just that *configuring* ALSA directly is only for lunatics and masochists. PulseAudio is just flat-out better in every way for that. ALSA controls the hardware, PulseAudio controls the audio streams.

The fact that it's only a single output that's affected shows that it's not a systemic problem. You say that it's only some content that's affected: is it only loud content? Having the output level too high for just that output could cause clipping that wouldn't be in anything else.

That's what I'm trying to figure out, as far as volume, because I usually don't listen to stuff with my headphones turned up all the way anyway. Secondly, some of the content that's affected is music that starts out quietly and finishes loudly as part of the musical score. I can barely hear the beginning of those certain music videos because of the distortion, and turning the volume up doesn't help anyway. And as I said, it only happens with my headphones on certain videos and/or YT channels. The video I'm listening to now via my headphones at this writing, is of Tibetan singing bowls recorded at a reasonably safe, yet listenable volume, with the sound quality being top-notch, and zero amount of the post-update distortion I've mentioned.

The question I'm thus trying to work out the answer to is: [I][B]Why is the distortion happening on only certain channels--the ones belonging to Stephen Colbert and The Daily Show, just to name two--despite my listening to them in my headphones at a safe volume, and not others? And why is it happening on BOTH Firefox and Chrome? 
[/B][/I]
The only thing I can think of is that there *is *a problem with something in the system that's maybe not detecting the proper volumes at which the affected videos were recorded. After all, Colbert's show is likely recorded at a certain volume, as is Trevor Noah's show. Someone putting an entire high-quality video of themselves playing or singing music may record their work at a specific volume that was otherwise detected prior to what seemed like a typical system update (via the Software Updater) after I upgraded to 18.04 (which was two weeks ago, give or take).

I confess I am grasping at straws here with my speculations, so I'm just gonna do what I've been planning on doing and getting an installation disc for a fresh reinstall of 18.04.

---

