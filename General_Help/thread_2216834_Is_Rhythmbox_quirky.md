---
title: "Is Rhythmbox quirky?"
date: 2014-04-14
forum: General Help
---

### Post by Rick_Allen on 2014-04-14
Brand new to Ubuntu and Rhythmbox. I am probably not the typical user. But I noticed a few oddities and wondered if it's me, my installation, or the software. I mostly use it to play longer MP3 files.


[LIST=1]
[*]Clicking an MP3 file from a folder (at least from my WD LiveBook drive) the app opens, but does not play, and no file or tag information appears to add it to a queue or anything. I have to use Rhythmbox's own interface to find and play the file. It does not place it in the Play Queue either.
[*]Once you do have an item playing you cannot skip ahead within the file. So if I want to listen from the half-way point in a file - too bad. The progress slider to totally ineffective in moving to a different point in a given file in either direction.
[*]The Next Song button works, but the Previous Song button does not.
[/LIST]

---

### Post by coldcritter64 on 2014-04-14
I'm using Rhythmbox in Debian Wheezy at the moment, and just to compare checked off your list of concerns with Rhythmbox.
1. Right clicking an mp3 file and selecting open with Rhytmbox Music Player, the music starts playing opened in the Library under "Music", it is **not** in the Play Queue.
2. Clicking anywhere on the progress bar jumps anywhere I click immediately. No problem skipping and jumping back etc.
3. Navigation, next/previous work ok.

Which release did you install ? Does not sound normal for an install of Ubuntu to have rhytmbox performing like that. It has always worked the same in Ubuntu for me as it is in this install I'm currently using.

How did you install dvd or usb ? Did you check the iso image file you downloaded, for any corruption of the file, with the md5 for the download ?

 It can sometimes cause strange effects, a bit like you are describing, if you've used a corrupted installer. Do you notice any other discrepancies in how the interface and other applications are performing, apart from the Rhythmbox issues ?

---

### Post by tgalati4 on 2014-04-14
It's possible that your WD LiveBook is falling asleep and therefore *rhythmbox* has to wait for the drive to spin up to reread the file.  Open a terminal and run *rhythmbox* in it and check for error messages.  Copy the files you are having problems with to a local directory and play them and see if you have the same behavior.

---

### Post by Roasted on 2014-04-14
I've had some issues with Rhythmbox with stability being the biggest one. At times it's fine, others it needs to be force quit several times. I just avoid it and use Clementine. I know it's not a constructive response but I just haven't had that great of luck with Rhythmbox.

Fun fact - I ran the music for my own wedding in 2012 running on my own Ubuntu desktop being pushed through a huge rented sound system. I used Clementine for this as I could tweak the crossfades between tracks etc quite extensively. Likewise, I never had Clementine crash. I honestly couldn't have possibly done that with Rhythmbox. It may have worked, but I wouldn't have been able to really trust it to do so flawlessly, whereas with Clementine I was entirely care-free and it did the job fine.

Just my 2c.

---

