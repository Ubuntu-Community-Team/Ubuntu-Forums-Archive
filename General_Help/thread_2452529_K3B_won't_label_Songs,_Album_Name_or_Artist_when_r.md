---
title: "K3B won't label Songs, Album Name or Artist when ripping audio cd"
date: 2020-10-23
forum: General Help
---

### Post by Ralph L on 2020-10-23
I have been using K3B Version 17.12.3 on Xubuntu 18.04 to rip audio cd's for the last few years.  Recently I tried to rip some more cd's, but k3b wouldn't/ couldn't find the artist, album name, or song names like it used to.  I see in Settings>Configure K3b>CDDB that k3b uses freedb and MusicBrainz to look up this information.  I also see that freedb has gone away (no more web site), but MusicBrainz is still there.  Hence I unchecked the box to use freedb, but k3b still can't find album name, etc.  I tried File>New Project>New Audio Project, then ejected and reinserted the cd into the drive (the track numbers appeared) did a Select All (Ctrl-A), dragged all the tracks to the Audio Project window pane, clicked on the Query CDDB button and k3b found most of the meta information (Song name, artist; I didn't Album title).  So I know that k3b can find the info, but I can't make it find the info, when ripping.  Also Clementine  finds all the information, but is very slow ripping.  Hence I want to use k3b.

Any help in getting k3b to find meta information would be appreciated....

---

### Post by Ralph L on 2020-10-25
On the chance that newer versions of K3b might have fixed the cd ripping problem I downloaded and tried Kubuntu 20.4.1.  It had K3b version 19.12.3.  However, the problem is not fixed there.  I still could not get the cd ripping function to find Album, Artist, Song information from the web (Musicbrainz or other).  However, K3b finds that same information for the New Audio Projects function so I know it is available and the code to do it is in K3b, just not working in the CD ripper function.  I hate to go back to one of the other CD rippers (Clementine, Sound Juicer, etc), since K3b will rip a CD in half the time the others do it, and I have over 100 CDs to rip.

Maybe I am doing something wrong and it is operator error.  Is anybody else able to get the ripper function work in K3b.  I would really appreciate any input from anybody who has tried K3b Audio Ripping in the last few months????

---

### Post by Yellow Pasque on 2020-10-25
Try changing to gnudb.gnudb.org (Port 80, HTTP)
Make sure you have "Enable freedb lookup" checked.

---

### Post by Ralph L on 2020-10-26
Yellow Pasque:  I really appreciate your responding to my problem.  I tried your suggestion, but I couldn't make K3b work.  It just created a folder called "unknown" and put songs in it with the artist name as "unknown" and the song name as "unknown".  However, it did rip the songs twice as fast as most of the other rippers.
While I fiddling, I did find that by using the New Audio Project function I could create (in a folder on my disk) a new folder with the ripped songs in it "~/music/ripped-track/the various songs automatically named correctly".  However, I don't want the extra 2 levels of folders (music/ripped-tracks) and I want the ripper program to automatically name the folder with the album name.  The K3b rip function used to do all this.  Also, the ripping using New Audio Project was slow--much slower than the K3b Rip function.
While exploring all the rippers I could find, I came across Asunder.  I entered gnudb.gnudb.org and port 8880 into its CDDB setting, and it worked great.  It found all the meta data, and created appropriately named folders and song names.  I did have to set the No Error Correction box to get fast ripping out of it.  It ripped my Fleetwood Mac cd in 3 min. with No Error Correction, but with Error Correction it took 6.3 min--among the slowest rippers I tested.  I don't know exactly what error correction it is doing (I guess it would be read error correction), but the music all sounded fine with No Error Correction.  Also, while I am using the flac format for my ripped files, I might want to use aac at sometime in the future, and Asunder supports that encoding format.
Anyway I think I will just use Asunder unless K3b gets fixed.
Thank you very much for your help.

---

### Post by Yellow Pasque on 2020-10-27
Yeah, Asunder works well. It's not the most modern-looking program, but it gets the job done. To encode AAC, remember to install fdkaac package.
Maybe I will try out ripping a CD with K3b here on Debian sid, which has the latest version, to see if I have the same issue.

> Thank you very much for your help. 

Sure. I just wish my help would have been.. well, helpful.

> ripped my Fleetwood Mac cd 

I've heard some "rumors" about them.

---

