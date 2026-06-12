---
title: "Occasional Audio/Video Pause"
date: 2005-08-02
forum: General Help
---

### Post by Gnuklear on 2005-08-02
Hi All,

I'm fairly new to Ubuntu (and GNU/Linux in general) and I've  been having a little bit of trouble with the multimedia applications. I'm running Ubuntu on a new laptop (on which virtually all hardware works, which is amazing because it was custom built) and I think this may have something to do with it. The problem is that when I try to play a large music or video file (normally FLAC and Xvid encoded) it will occasionally pause (and then start  back up about a second later) during play. MP3's and OGG files generally play fine, as do Audio CDs.

I believe I know what the problem is,  but I'd like a second opinion and help on a solution. My HDD is 80GB and 5400RPM (I think that's the problem) and I have a 1.5GB swap partition set up. I believe that the problem centers on the drive being only 5400RPM, and thus not able to read the data off the drive as fast as it's needed to be played (though the fact that Audio CDs play fine leads me to question this idea). Either that, or the swap partition is being utilized and so the delay occurs because the 5400RPM HDD is obviously much slower than RAM.

Any insight into the source of the problem or the solution would be greatly appreciated. Thanks guys.

---

### Post by heimo on 2005-08-03
You should check if you have DMA enabled. That's common problem in Hoary. Check that it's enabled for both hard disk and cd.

For example:
* hdparm -d /dev/hda* should give:
 ```
/dev/hda:
 using_dma	=  1 (on)
```

You need to substitute hda with correct device name (hints from /etc/fstab). You can turn DMA on with *sudo hdparm -d1 /dev/hda* but if that fails, you need to find out which chipset your laptop uses and then add correct module to /etc/modules If you can tell us which chipset it's, we probably can tell you which module to use. (For my Via KT400A/8237 it's via82cxxx, ide controller is on south bridge).

You can test performance of your disk with *hdparm -t /dev/hda *

BTW, some devices (scsi/sata) are of the form /dev/sda (or b, c, d) On my 7200rpm SATA disks I get values around 56 MB/sec. Hmm.. wait, I have one 5200rpm disk* on my server (yeah..) Ran the hdparm -t /dev/hda several times:

 ```
 Timing buffered disk reads:   34 MB in  3.13 seconds =  10.88 MB/sec
 Timing buffered disk reads:   52 MB in  3.05 seconds =  17.06 MB/sec
 Timing buffered disk reads:   64 MB in  3.02 seconds =  21.20 MB/sec
 Timing buffered disk reads:   60 MB in  3.05 seconds =  19.68 MB/sec
 Timing buffered disk reads:   66 MB in  3.08 seconds =  21.45 MB/sec

``` 

hdparm -d /dev/hda 
 ```
/dev/hda:
 using_dma	=  1 (on)

``` 

I hope this helps / gives some tools / background to work with.

*) Oh! Have to clarify that this is actually "laptop disk" in a desktop case. And now as I start remembering it, it's not actually 5200rpm disk at all! It's Hitachi 7K80, so it's 7200rpm disk, but "dog" compared to those 7K250 / Samsung P80 for which the other values were. Still plenty for playing video (however my box is used for serving email).

---

### Post by Gnuklear on 2005-08-03
Thanks for the help, Heimo!

I checked, and DMA was enabled for my hard disk, but not for the CD drive, so I enabled it for that. Also, I ran the diagnostic tests you suggested and averaged a disk read speed of 29MB/sec, so it should certainly be fast enough to play the files in question.

Sadly, the problem persists. I have used the system monitor to try to see if this is some sort of memory issue, but to my surprise it appears to have nothing to do with memory: No matter what I do memory usage stays stable at about 158MB out of a total of 512MB of ram, and 1.9 MB or 1.4GB of swap. Also, just now as I watched, it skipped during 3% CPU usage. This leaves me at a loss, as there appear to be plenty of resources available. However, it does appear to skip MORE when there is a high level of CPU usage.

If it helps:
I'm using Rythmbox as my default music player
I using an AMD64 laptop, with 32bit Ubuntu (so not the AMD64 version)
80GB HDD, 5400RPM (not sure of cache off the top of my head, I can find out is needed)
512MB Corsair RAM

If more info is needed, I can look it up. Thanks again for the help guys.  ;-)

*) I just now had Rythmbox skip while trying to play an MP3 file, which makes me wonder if this might be some kind of issue with GStreamer/Rythmbox? Probably not, but just thought I'd throw that out there...

---

### Post by heimo on 2005-08-03
Oh, let's rule out one reason. I don't know which framework rhythmbox uses, but you could try totem, then install totem-xine (will uninstall totem-gstreamer), try that one, then xine (or more specifically gxine) and vlc. If some of those will work, it could have something to do with gstreamer. Just something you should try to isolate this problem.

---

### Post by Gnuklear on 2005-08-03
Yeah, I had thought about that just after I posted the last message.... (Rythmbox uses GStreamer, as does Totem)

So, while I was waiting for your (extremely quick, thanks so much) response, I decided to try Totem out as a music player, and to my great shock, it has not skipped since I started.... I've been listening for about 20 minutes, so I'm not absolutely sure it won't skip, but Rhythmbox skips about once every 50 seconds... It's looking to be a Rhythmbox issue, which is weird as both programs utilize the same core code.... I'm using Rhythmbox 0.8.8 and Totem 1.0.1 (which Totem says is using GStreamer 0.8.9). If more info is needed, let me know, and thank you so much again for all the fast help! :smile:

*) Actually... I installed xine a few days ago, and I'm not sure if I installed totem-xine... is there any way to check without just reinstalling totem-gstreamer?

**) NVM, I just checked Synaptic and totem-xine is not installed while totem-gstreamer is, so that should put my previous question to rest. It appears to be an issue unique to Rhythmbox

---

