---
title: "Thunderbird .wav notification not playing cleanly - CLICK sound"
date: 2006-10-20
forum: General Help
---

### Post by dwasifar on 2006-10-20
Thunderbird by default uses the "system mail notification" select, which for some reason creates a beep from the case speaker.  (wtf?)  I set it up to use a .wav file instead, but I find that no matter what .wav file I use, Thunderbird inserts a static click at the beginning.  So for instance if I set it to /usr/share/sounds/question.wav, I hear CLICK-bongo-bongo instead of just bongo-bongo as it should be.

The files play fine in other applications, with no click.  Weird?  Weird.  Anyone else have the same issue?

---

### Post by marianom on 2006-10-20
Like this:
[http://www.ubuntuforums.org/showthread.php?p=1247138#post1247138](http://www.ubuntuforums.org/showthread.php?p=1247138#post1247138) ?

I still have the same issue on TB. On skype, after update it's fixed. It has something to do how the program interacts with the soundcard. Suggest checking the mozillazine.org, maybe there's a fix over there.

---

### Post by sagara on 2007-03-29
Same problem here... we can't be the only three people having this problem in the entire forum!

---

### Post by marianom on 2007-03-29
I turned the tb sound off and I'm using mail notification to know if there's incoming messages. 
I'm even using Vincent Price's laugh from Thriller to alert me about new messages. :twisted: 

Some problems can't be fix (or you get bore before finding a solution).

---

### Post by MGStreak on 2007-04-23
> **sagara said:**
> Same problem here... we can't be the only three people having this problem in the entire forum!

You're not.  Consider me 'subscribed' to this thread, and also hoping for a quick resolution.  (As well as a shameless bump to this topic!)

Here's hopin!

---

### Post by kolinab on 2007-04-24
> **MGStreak said:**
> You're not.  Consider me 'subscribed' to this thread, and also hoping for a quick resolution.  (As well as a shameless bump to this topic!)

Here's hopin!

Well I initially was going to agree what I heard this noise too, but I just listened more carefully again and it's not a click at the beginning I hear, it's just general poor sound quality. I'm going to try a different sound file and see if it's any better . . .

K

---

### Post by johnko99 on 2007-12-26
I have installed romans.wav (88,3KB) from oppenoffice as a sound notifier for new arrived messages in Thunderbird. But it doesn't play in full. Almost 3/4 of the sound is played and the rest is suddenly cut off. This has been observed and on some other .wav sounds tested. What is wrong? How can I remedy it?

---

### Post by lleonard on 2007-12-28
Johnk099 - I have exactly the same problem.  Have you been able to diagnose what's causing it or find a fix?

---

### Post by lleonard on 2007-12-30
Johnko99 - The abrupt notification sound cut-off is open as [bug 155648 in Launchpad]("https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/155648") if you want to follow it.

[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/155648](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/155648)

---

### Post by nealos on 2008-07-02
For what it's worth, using TB version 2.0.0.14 (20080505) under Ubuntu 8.04 (32 bit), I was having the few seconds of static in place of audio when trying to play a notification wav in both TB and the "Mailbox Alert" add-on.  It seems that TB is picky about the wav codec so I followed the following course of action based on various sources (Thank you people):

1.  Identified the codec of the problematic wav:

[I]$ file Mail03.wav
Mail03.wav: RIFF (little-endian) data, WAVE audio, MPEG Layer 3, mono 16000 Hz[/I]

2.  Attempted to convert this file to a more TB friendly wav codec using sox:

[I]$ sox -a Mail03.wav -s -w soxMail03.wav
sox soxio: Failed reading `Mail03.wav': unknown file type `auto'
[/I]
3.  Having failed at step 2, I went out and found a different source for my wav file and determined its codec:

[I]$ file new.wav
new.wav: RIFF (little-endian) data, WAVE audio, Microsoft PCM, 8 bit, mono 11000 Hz[/I]

4.  Noticing that this new file was encoded differently, I decided to try it in the TB notification and it worked!  My hope is that someone with a little more audio conversion experience can contribute a command or gui that would convert audio files to the above TB-friendly encoding.

Thanks to those whose contributions led me to this solution.

nealos

Dell Dimension 4300
Ubuntu 8.04

---

