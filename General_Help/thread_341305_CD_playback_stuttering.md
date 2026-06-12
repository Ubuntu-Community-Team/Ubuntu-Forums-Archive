---
title: "CD playback stuttering"
date: 2007-01-18
forum: General Help
---

### Post by m_memmory on 2007-01-18
I like to listen to music quite a lot and most of my music is stored as FLAC files which I generally have played via a USB port into a DAC/Amp combo that I have which then powers my headphones.  Today however I tried playing a CD and playing the music through my headphones but the music stutters every 2 seconds or so (and very regularly)

I tried a few different programs and everyone showed the same problem.  I then switched back to my computers internal soundcard (an Audigy 2 ZS Platinum Pro) and had exactly the same problem again.

Is this a problem with some settings somewhere that's causing the error on playback of an audio CD?

---

### Post by khedron on 2007-01-18
Are you on Gnome or KDE? In KDE, there is a System Settings module called Sound System with a section called Skip Prevention that you could use to increase the buffer size. This is useful for preventing skips if the sound system is not getting a consistent stream of data, but there might be something else wrong.

Sorry that I can't help that much, my sound worked without much fuss.

---

### Post by m_memmory on 2007-01-18
I'm actually using Ubuntu with the Gnome interface.

To be honest it's not something that I'm really concerned about as most (if not all) of music is actually stored in FLAC which plays without any problems at all - although I would like a program that plays them gaplessly which I've not found yet.  I just wondered if this is a problem that a lot of people know about or maybe a symptom of something that I should be concerned about with my install.

---

### Post by allwin on 2007-01-18
I have this same problem.  It is exactly as if the CD being played is not buffered anywhere, at all!  It reads a block of the disk, plays it, pauses, and reads the next one.  I'm also using GNOME.  I haven't found any settings to help.  I even tried "sudo hdparm xxx" to see if there were any things like turning on DMA or something which could help.  None.

BTW, I have a lot of other problems with SOUND which are annoying.  If I play a WAV, they all end with a big WHOOOSH sound that I don't hear in Windows.  Volume in GNOME is OK, but in KDE it's too low and if I turn up the volume, it gets distorted long before it becomes ear splitting.  IOW...GNOME makes different sound than KDE on the same box.

Weird.  But IMHO sound+MIDI are not highpoints for UBUNTU.

I'll be watching this thread too.  To be sure, stuff played off disk is generally OK (except WAVs/MIDIs).

---

### Post by allwin on 2007-01-20
Bump?

---

### Post by khedron on 2007-01-22
Again, I can't really help, but I can suggest reasons and reading material from my limited experience.

One reason for skippy music might be that sound is not processed in realtime. I hear that **Jack** is a low-latency sound server, but this might be a bit of an extreme (or wrong) solution.

---

