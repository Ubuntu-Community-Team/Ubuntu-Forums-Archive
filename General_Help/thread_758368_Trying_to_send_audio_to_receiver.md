---
title: "Trying to send audio to receiver"
date: 2008-04-17
forum: General Help
---

### Post by finlost on 2008-04-17
Hi all - a very green FNG here...

I have been banging around with Feisty Fawn for a few months.  I am hoping to get a stable setup and use it as my media machine (stream audio, light surfing, YouTube, play my collection of MP3s, view digital pictures).

Right now I am having an audio problem that I haven't been able to resolve searching this forum and using the Google.  Since I want to use my Linux box as a media machine, I want to run audio to my Harman Kardon receiver.  

I poked around with my Linux computer for a couple months before connecting it to my receiver.  The other day, I connected my computer to my receiver for the first time.  Audio could only be heard from the internal PC speaker.  I wasn't able to get audio out of my HK receiver.  So last night, I decided to reinstall Feisty Fox.  After a few package installations (codecs) I succeeded in getting sound to my receiver.  All is good.

Today, I install Firefox.  So far so good.  

I install the Flash plugin and stream Pandora.com to my receiver (old school CW!!!)

I install Gxine packages.  Now I am able to stream a local sports talk station.  All seems to be working as planned,

I had difficulty installing JRE.  Adept crashed and I ended up using the Google to find a resolution.  After cleaning up the mess Adept left, I finished the install using the terminal.  I think somewhere in the JRE installations, the audio died (it may have died prior to JRE, but I don't really know for sure)

I removed JRE and Gxine packages so see if I could get audio to my receiver again.  Packages were uninstalled, but no audio to the receiver.

I should mention that audio is always coming out via the internal PC speaker.  Even when audio isn't making it to my receiver, audio is coming out of the internal PC speaker.  The sound card (Intel8x0) is part of the motherboard.

As I stated above, I wasn't able to find a relevant solution searching the forum.  Any ideas?  Should I reinstall Feisty Fox and carefully track my package installations trying to pinpoint the exact time of failure of audio to my receiver?  Purchase a used sound card off the eBay?

Also, what other information is pertinent to help find a viable solution?

---

### Post by russo.mic on 2008-04-18
go into a terminal and run alsamixer, and play around with the settings in that.   I've got an intel soundcard in my MBP and the settings as far as the headphone jack can get kind of strange sometimes (having both play at the same time and such)

Play around muting and unmuting the various outputs, almost certainly one of them will be the headphone jack.

Good Luck!  

Russo

---

### Post by finlost on 2008-04-18
Yes, I just discovered that if I wind out my receiver, I get sound coming through it.  You beat me to it by a couple of minutes. :)

I am not sure what happened.  When I first had sound coming through the receiver, I had the receiver volume way down, but it was still quite loud.  Now it is the opposite.  I have to turn the receiver volume up to a very high level to get any sound.

Regarding alsamixer, is that the same as KMix?  I have poked around with both, but I haven't found the right slide to get the receiver volume adjusted to an appropriate level.

---

