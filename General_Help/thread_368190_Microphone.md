---
title: "Microphone"
date: 2007-02-23
forum: General Help
---

### Post by JELO on 2007-02-23
Hello everyone,
I'm currently have a bit of trouble to get my microphone working.
What i've done thus far is the following
I went to System -> Sound
Changed Auto, Auto, Auto, Also to OSS (I'm assuming this enables the OSS driver for the mic input?)
Clicking the test button on the sound capture doesn't enable any audible sound (Also, Silent, etc), on all of the others I hear audible sound.
I then tried going to Applications -> Sound Recorder
Opens up fine but Recording then playing back doesn't give any audible sound.
I then found this post
[http://ubuntuforums.org/showthread.php?p=2189449](http://ubuntuforums.org/showthread.php?p=2189449)
Perhaps I did something wrong?
I've also tried messing with the mixer a little but have gotten no where. 
I'm currently using a soundblaster audigy ls.
The mic works in windows fine, but i'd like to get it working in ubuntu as well.
Any help is appreciated.

---

### Post by JELO on 2007-02-25
bump

---

### Post by reclusivemonkey on 2007-02-26
ALSA is the default; is there any reason why you are not using ALSA?

I have a SoundBlaster Live, and my mic works fine using ALSA.

Have you got more than one soundcard? What do you want to use your microphone for?

---

### Post by abh83 on 2007-02-26
hey jelo,

i had a similar issue. In fact i had no sound at all but after using this solution: [http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)

i got everything working even my mic.

once u're done with the above link restart and then double click on the volume icon in ur panel then click on the capture tab and activate the mic.

see if this works... good luck!
ABH

[COLOR="Red"]EDIT: btw the code to restart ALSA in edgy: sudo /etc/init.d/alsa-utils restart (for the link above)[/COLOR]

---

### Post by JELO on 2007-03-04
Thanks for the posts guys, I've tried and I still can't get it working.
I was thinking about taking the Audigy LS out and trying the onboard sound.  Question is do I need to uninstall the Audigy in anyway and will linux automagically pick up the onboard sound?

---

### Post by reclusivemonkey on 2007-03-04
> **JELO said:**
> Thanks for the posts guys, I've tried and I still can't get it working.
I was thinking about taking the Audigy LS out and trying the onboard sound.  Question is do I need to uninstall the Audigy in anyway and will linux automagically pick up the onboard sound?

If you completely remove the Audigy, then no you shouldn't have to "uninstall" anything. However if you have made any manual configurations, you will want to delete those. As long as you have your onboard sound card enabled in the BIOS, Ubuntu should pick it up.

---

### Post by JELO on 2007-03-10
Hey guys I finally got around to trying out the onboard sound.  The mic works now.
There is a degree of background static involved though, it does come through clear however.  Doing the +20db mic helped a bit.

Maybe ubuntu just didn't like my ls?  I have been thinking about getting a newer audigy, would those give me any trouble?  Also, not related to ubuntu exactly, but my onboard sound has options for headphones and mic in the front of the case (plugins).  I double checked my manual and didn't see any option for it on the LS.  Do you know if the newer audigy cards support that?

Edit:  Hey guys, got my hands on an audigy 1.  Looks like everything is working.  Though, my mic isn't working in CS:Source.  However, it looks like it's working on teamspeak and the built in sound recorder.  I'll post again if I run into more trouble.  Quality is much better than built in.

---

