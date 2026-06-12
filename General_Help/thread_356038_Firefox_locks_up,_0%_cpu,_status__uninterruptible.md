---
title: "Firefox locks up, 0% cpu, status:  uninterruptible"
date: 2007-02-07
forum: General Help
---

### Post by nfriedly on 2007-02-07
This has happened to me a few times, firefox will completely lock up. I can click the close button and Force Quit, but it's still running in the background.  The system Monitor shows the process as  Uninterruptible, 0% cpu load, not much ram (35MB) 

Telling the process manager to Stop, End or Kill it all have no effect. It just sits there as Uninterruptible. I can't restart firefox because it's already running. sudo kill <pid> does nothing. Ctrl + Alt + Backspace leaves me hanging with my wallpaper and nothing else. I had to reach down and hit the reset button to get the system to snap out of it.

It seems like it's hit this problem when I open Firefox and immediately try to type in a url, before my homepages are loaded.

Any ideas to make it stable? Or at least how to kill it without bringing down the rest of my system?

I'm on Ubuntu 6.10 with all the updates,
Firefox 2.0.0.1 with these extensions:
Adblock Plus 0.7.2.3
Firebug 1.0
Reload Every 2.0
Slashdotter 1.8.9

---

### Post by sdide on 2007-02-08
Have you tried 
sudo kill -9 <pid> 
?

---

### Post by nfriedly on 2007-02-08
nope, but I will the next time it happens. thanks.

---

### Post by nfriedly on 2007-02-14
Ok, happened again. I just started up my computer. Logged in and clicked the firefox icon. I did not click a single other thing and firefox locked up. The tabs have the name of my two homepages but nothing else. Status bar reads waiting for static.netvibes.com.

I open up the System Monitor and see this:
```
Process Name 	Status			% CPU	  Nice	ID	  Memory
firefox-bin	    Uninterruptible	0		0	4889	29.0 MiB
```

so I try **kill -9 4889** and nothing changes. **sudo kill -9 4889 **does likewise.

Any ideas?

---

### Post by z987k on 2007-02-14
have you tried using an older version of Firefox until this gets sorted out.  It seems a lot of people are having this problem.

---

### Post by nfriedly on 2007-02-14
haven't tried that.. bummer.

---

### Post by vicnov on 2007-05-03
On my laptop Firefox sometimes hangs and becomes "uninterruptible" when working with Flash. Such process can not be killed - only reboot helps.
As I read in many posts and discussions, normally, a process becomes "uninterruptible" because of some driver's bug (the driver waits indefinitely for some event which never occurs). So I do not understand - is this Flash's bug or some driver's bug?

Firefox version 2.0.0.3
Flash plugin version 9.0.31.0
Ubuntu 7.04 Feisty Fawn
Kernel 2.6.20-15-generic

---

### Post by Hesperion on 2008-04-28
Joining in here...I find that all works superbly well but my problem is related to this I think. Firefox works flawlessly until I download something and direct it to save to my SD card.

The full scenerio:
I am at a newsgroup reader site called Easynews.com. I go to a group called alt.binaries.sound.mp3.classical and select a file to save, choose the SD card destination. It goes through the download process and gets to the end and just hangs. Firefox is listed in the System Monitor as using no resources and as "Uninterruptible"; cannot be closed; cannot be stopped; cannot be ended; cannot be killed; will not go away. Only way out is the power button. Later I installed some codec packages for mpeg1 layer 3 and for flac and also the VLC player and all that comes with that. Just before typing this I tested the thing again. It asked for my site UN/PW and commenced playing the file. It saved to the SD card full sized and that was that. I don't know if the hang had to do with hunting for codecs or a suitable player or what but it works now. 

At any rate, Firefox didn't lock up and the file operations that were stuck seemed to complete this time. The only addon I have in Firefox is the Flashblocker which I highly recommend. Flash has always been a problem so it is nice to have control over the object in each page rather than wondering which advertisement, which you didn't come to see anyway, is screwing up things. LOL. 

BTW: I am on an ASUS EeePc 701 4G Surf running Ubuntu 8.04. So far have been able to fight through all the problem I had coming from Gutsy and it all seems quite good. Don't know if anything in this gives some clues. If not I apologise for inserting myself unwanted.

---

### Post by Hesperion on 2008-04-28
Sorry for the duplicate. OOPss!

---

### Post by nfriedly on 2008-04-29
Well, I had a couple of other things that I had goofed up on my system and so I ended up just wiping it out and reinstalling Ubuntu. That seed to fix this issue. 

That was Ubuntu 7.04, btw.

---

### Post by sankz on 2008-07-16
I had this problem nearly every time I opened firefox...
Have switched to Opera 9.51 now and it works like a dream now...
I hope somebody fixes this problem, i really miss my addons from Firefox...

---

