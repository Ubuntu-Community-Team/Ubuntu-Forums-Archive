---
title: "Random popping but no sound - tried every solution I could find on this forum, help!"
date: 2014-02-20
forum: General Help
---

### Post by fm-illuminatus on 2014-02-20
So, I just reinstalled 13.10 from a bootable USB [I was running 13.04 and the sound was working fine], set everything up, and sound doesn't work.  I can see the right devices in sound configuration, adjust the volume, but I get no sound - only an irritating pop every couple of seconds.  I reinstalled the audio system - nothing.  I went into alsamixer, unmuted everything, made sure the right sound output was selected, etc, nothing.  Tested the speakers on a Windoze machine, they work fine.  I ran a laundry list of commands from every no-sound trouble-shooting post on this forum, half of which I don't remember, NOTHING AT ALL CHANGED. I didn't even manage to make it worse, all I get it that irritating popping every few seconds and no sound in the sound test or on any media.  Even when I was removing and adding back pulse the popping still continued during the entire process. IT WAS POPPING WHEN PULSE WAS COMPLETELY 'REMOVED' AND IT WASN'T POSSIBLE FOR SOUND TO PLAY!!!  Restarted countless times.

Anyways, I'm pretty much fed up.  Maybe this is a 'feature' of 13.10 - permanent annoying pops that are impervious to any commands while nothing else plays. At this point, I'd be happy to just 'break' my sound to stop the popping - to show that anything I'm doing is actually changing something.  Even that would be a good start.  Anyways - someone please show me how my sound can actually work on 13.10. 

Thanks.

---

### Post by TheFu on 2014-02-21
Welcome to the forums.
What sound card?
Does it work with a LiveCD running?

Rebooting is seldom the answer to Linux issues.

---

### Post by fm-illuminatus on 2014-02-25
> **TheFu said:**
> Welcome to the forums.
What sound card?
Does it work with a LiveCD running?

Rebooting is seldom the answer to Linux issues.

Don't have liveCD, but I haven't checked booting with the USB.  I'll check and let you know.  No sound card, it's just onboard sound on an HP motherboard.  The thing is, it worked fine in 13.04.

Edit: tried the USB, it doesn't work either.  So, it looks like 13.10 broke the sound for some computers.  That's irritating.  I can even adjust the volume with my keyboard and headset, and it makes the little 'pop pop' sound and shows the sound slider going up and down, but no sound will play on any program I run.

---

### Post by TheFu on 2014-02-25
So it is the driver for the sound card.
"Sound card" is a generic term for "whatever chips make sound possible inside a computer."  So ...  [http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware](http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware) might be helpful to determine the hardware, then determine the needed driver.

---

### Post by tgalati4 on 2014-02-25
It's possible that the sound chip's amplifier has released the "magic smoke".  Popping sound is usually indicative of a blown amplifier.  The digital section is probably OK because the sound module loads and you can see and select the card in alsamixer.  Do you have a digital output (optical or RF connector)?  Do you have an HDMI output?  Try other ways to get sound.  

Open *audacity*, and see if the microphone works and that you can record sound at different levels.  Turn the monitor on in *audacity* so you can see the microphone level meter.

Make sure the motherboard is clean.  What is the output of:

```
lsmod | grep snd
```

and

```
aplay -l
```

That's "l" for "list".

---

