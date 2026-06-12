---
title: "Could using dvd+rw-tools damage a burner?"
date: 2007-04-10
forum: General Help
---

### Post by Calgaricky on 2007-04-10
I've been using Ubuntu for about three months now (dual booting with Windows XP), but I'd never actually tried to create a DVD or CD from within Linux until a couple of days ago.

My first attempts at creating a DVD seemed to work okay, but when I did a rewrite of the DVD+RW disc later on, growisofs appeared to go through the entire burn process and then hang after it said it was writing the lead out.

I tried killing the process, but that didn't seem to work, so I just rebooted the machine to see what would happen. At this point, I was unable to view any sort of media in the drive at all... I tried several pressed CDs and DVDs, but nothing would show up.

Next I rebooted into Windows and found the drive no longer seemed to work there either. (I did manage to get it to half recognize an audio CD in XP, but after a few seconds of playback it stopped and the drive just started making clicking noises).

Alrighty, I'm pretty sure this is a hardware issue, and my gut is telling me it's just a coincidence that this happened while I was burning a disc under Linux... but being relatively new to Ubuntu, I'm wondering if I could have done something wrong from the command line that caused the drive to fail?

This is the command I used to burn the disc: 
"growisofs -dvd-compat -Z /dev/dvdrw -dvd-video ./dvd/"

and my burner was a "LG Super Multi DVD Writer 18x18x10 DVD +/-RW"

I had no problems with this drive before trying to burn DVDs on Linux, so I'm hoping it was just bad luck and coincidence that the drive decided to die when it did. I think I'm a little worried that I caused this myself with my experimentation, and I don't want to get into an endless cycle of destroying burners... :-)

---

