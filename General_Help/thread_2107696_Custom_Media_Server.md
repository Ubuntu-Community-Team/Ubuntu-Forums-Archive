---
title: "Custom Media Server"
date: 2013-01-22
forum: General Help
---

### Post by pistonengine on 2013-01-22
Hi all,
 
First off, I want to apologize if this isn't the appropriate place to write this thread. I'm exploring options for this project I'm working on, and I want to consider a Linux based solution.
 
I am looking to build a music server to go with my stereo - essentially a MP3 player to store and play the files. There are high-end audio manufacturers who make these servers, but I'm looking to build my own and save a few thousand dollars. I do have some (but extremely limited) experience with Linux, and I'm fairly certain I can accomplish this task with Windows, but I want to explore every possibility.
 
That being said, there are a couple considerations to ensuring the quality of the sound is superb (no, an iPod or a Zune will not do, not even close).
 
Software and hardware latency. Anything that might cause any sort of delay or jitter in the processing or the final signal. There are guides on optimising XP for this sort of application ([http://www.cicsmemoryplayer.com/index.php?n=CMP.07Optimisations](http://www.cicsmemoryplayer.com/index.php?n=CMP.07Optimisations)). I've also read that an onboard audio chipset will perform better than a VGA soundcard for latency reasons (thought I'm somewhat doubtful that's true)
 
Electrical interference. This is big. Any electrical noise from a low-end PSU, back EMF from the fans or HDD, etc. can contaminate the audio signal from induced voltages or direct noise on the line.
 
So these are the ideal parameters for my system:
SSD instead of HDD
Overkill on CPU and RAM
Rock-solid, stable clock
Fanless, clean, high quality PSU
Fanless CPU heatsink (heat shouldn't be a problem with the very low loads)
Switch soldered in the power line for the CDROM drive (to turn it off when not ripping a new CD)
No video chipset (VGA card removed after installation, control remote via LAN)
Onboard audio with TOSLINK (ALSA drivers help support??)
 
Can something like this be accomplished with Linux by someone with my extremely limited experience? Are there high quality music players available like [www.foobar2000.com]("http://www.foobar2000.com/") and [www.jriver.com]("http://www.jriver.com/")? Is remote access and control of the computer easy enough? Drivers to support the motherboard TOSLINK, or if I think the mobo's audio chipset is crap, a VGA soundcard? Will Linux boot and run properly with no video card? Can I boot it with no video card and be able to remotely access it (i.e. I don't have to click around to open the remote access software)?  Can the OS be optimized to almost zero overhead?
 
Thanks in advance,
 
Piston

---

### Post by Cheesemill on 2013-01-22
Just use a motherboard with an optical S/PDIF output and connect it to an external DAC, this way you bypass all the problems of electrical interference that may originate from the PC, your audio quality will then depend on how much you are willing to spend on your DAC.

In my setup I have a computer in my basement that acts as a file server, and then a music streaming device (an original Squeezebox) in my lounge that streams all my music (stored as FLAC files) to an AV amp via an optical cable. This way my amp isn't located near any possible EMI sources.

Another advantage of separating the storage is that you can have multiple players, in other rooms in the house I have some Raspberry Pi's that output audio to AV amps via an HDMI cable.

---

### Post by pistonengine on 2013-01-22
> **Cheesemill said:**
> Just use a motherboard with an optical S/PDIF output and connect it to an external DAC
 
Yes that is how I do it now
 
> **Cheesemill said:**
> , this way you bypass all the problems of electrical interference that may originate from the PC, your audio quality will then depend on how much you are willing to spend on your DAC.
 
I don't necessarily agree with this.  The DAC is electrically isolated from the computer, but what I am concerned about here is the quality of the digital signal across the optical cable.  Essentially what we're after is:
1) Faithful reproduction of the PCM on the CD to a file on the SSD (not hard)
2) Faithful reproduction of the file on the SSD to an optical digital signal.
 
It's the second part I am designing around.  I really don't want to get into the question of "is this the best solution?" (I have a million solutions going through my head, and I hate all of them, including this one)
 
The question I am trying to answer is "is this solution doable as proposed?"

---

### Post by Cheesemill on 2013-01-22
The signal output over an optical S/PDIF cable will be a bit-perfect copy of the original CD, as long as you use a lossless audio codec such as FLAC.

This is true no matter how much (or little) you spend on your soundcard, whether it's an add-on card or integrated into the motherboard.

---

### Post by pistonengine on 2013-01-22
> **Cheesemill said:**
> The signal output over an optical S/PDIF cable will be a bit-perfect copy of the original CD, as long as you use a lossless audio codec such as FLAC.

This is true no matter how much (or little) you spend on your soundcard, whether it's an add-on card or integrated into the motherboard.

I already said I disagree with this.  I really didn't sign up for a Linux forum to debate the merits of electrical-to-optical conversion.

I am simply looking for advice from Linux experts if what I am trying to put together is technically feasible (e.g. I don't have to hire a programmer or figure out how to write a driver).  Whether it's worthwhile is a whole 'nother discussion.

---

### Post by tgalati4 on 2013-01-22
There are so many factors that affect audio quality that it is hard to make specific recommendations.  Obviously you are not satisfied with iPod or Zune audio quality.  You can get semi-pro audio cards (like M-Audio Delta66) which have both balanced analog in and out and digital I/O with master clock syncing.  I would run a realtime kernel optimized for music production such as [http://www.dynebolic.org/](http://www.dynebolic.org/).  The amplifiers are important.  I like modified Carver ZR1600's.  Speakers are important.  I like professional speakers from Community and subwoofers by Bag End.  I try to avoid the hobby-lobby stuff at high-end Audio/Video retailers, prefering the Pro/Touring audio gear.

You need a way to objectively measure your performance.  I use an oscilloscope and test tones as well as a suite of testing procedures to measure distortion, peak and RMS power.  Then you need decent audio recordings.  Your high-end system will make most of your audio collection sound like crap--then you will be motivated to upgrade the quality of your recordings.  The cycle is endless.  Audio manufacturers know this.

---

### Post by pistonengine on 2013-01-22
> **tgalati4 said:**
> There are so many factors that affect audio quality that it is hard to make specific recommendations.  Obviously you are not satisfied with iPod or Zune audio quality.  You can get semi-pro audio cards (like M-Audio Delta66) which have both balanced analog in and out and digital I/O with master clock syncing.  I would run a realtime kernel optimized for music production such as [http://www.dynebolic.org/](http://www.dynebolic.org/).  The amplifiers are important.  I like modified Carver ZR1600's.  Speakers are important.  I like professional speakers from Community and subwoofers by Bag End.  I try to avoid the hobby-lobby stuff at high-end Audio/Video retailers, prefering the Pro/Touring audio gear.

You need a way to objectively measure your performance.  I use an oscilloscope and test tones as well as a suite of testing procedures to measure distortion, peak and RMS power.  Then you need decent audio recordings.  Your high-end system will make most of your audio collection sound like crap--then you will be motivated to upgrade the quality of your recordings.  The cycle is endless.  Audio manufacturers know this.

Thanks for the link!  I will definitely look into that.

I have most of my gear sorted out, and yes, much of my previously loved music is now unbearable to listen to.  I have three upgrades I want to do before I wrap it in a bow, the pre-amp, the DAC, and the source.

It's the source part why I started this thread.  Still looking for an answer on that, but this dynebolic opens up another option.

---

