---
title: "using Handbrake and having a little trouble"
date: 2013-08-25
forum: General Help
---

### Post by squakie on 2013-08-25
Short story:  in the process of scanning in DVD's, old VHS, music, photos, etc. for a media center.  Using Handbrake for the DVD's.

I've run into something I don't understand and could use an idea or 2 on.  There is 1 particular DVD - The Da Vinci Code - that seems set up quite differently and Handbrake doesn't seem to be able to make sense of it.  When Handbrake goes to process it, it completes in literally 2 seconds, and the resulting video is 2 seonds of nothing.  I've looked at the video-ts files, and the actual movie portions are all over the place and not in order.  I've tried having Handbrake process 1 at a time and using Openshot to splice everything together, but most of the time Handbrake won't even process the files.  It seems to be (so far) just for this 1 particular movie's DVD.  It's sequel - Angels and Demons - was doing the same thing but I was able to eventually process each piece through Handbrake and use Openshot to join them together to make a single file for the media center.  VLC, mplayer, etc., don't have any problem actually playing the DVD, but if I have something like VLC open just one of the video ts files it says it is not a valid format and does nothing.

I don't know squat about video or audio things, so perhaps there is some easy explanation to all of this?

Thanks.

---

### Post by carl4926 on 2013-08-25
When it reads the DVD, what is the longest part it shows (in time length)

---

### Post by squakie on 2013-08-25
The longest and what *should* be the movie is title 1:  2 hours 28 minutes and 58 seconds.  This is the title selected when I click "Start".  It VERY quickkly shows 0.01% and immediately says encode complete, and the resulting file is nothing.  Had this same problem with the sequel, but on it I could pull the individual video_ts files in and process them.

---

### Post by squakie on 2013-08-25
I also just tried to use the video player to play one of the larger video_ts files (there are 4 at a little over 1 gig each).  The movie player said decoding error.  I then tried a very small video_ts file and it plays (it's just the menu screen picture and the music) but it is still garbled like the decoding isn't working.  I do have libdvdread4 and the css package installed.

There is an autorun.inf file on the disk and it runs a DOS program dvd.exe.  I can only assume something in that program knows how to piece things together and also provides the additional decoding.

---

### Post by carl4926 on 2013-08-25
> **squakie said:**
> The longest and what *should* be the movie is title 1:  2 hours 28 minutes and 58 seconds.  This is the title selected when I click "Start".  It VERY quickkly shows 0.01% and immediately says encode complete, and the resulting file is nothing.  Had this same problem with the sequel, but on it I could pull the individual video_ts files in and process them.

And you have successfully worked through the process with other DVD's?
Are you sure you have all the encoding options etc.. correctly?
I'm not with my main box that has handbrake ATM, so my assist is limited, it's not something I do much of.
One thought, could you do a DVD copy with k9copy, then process what you want with handbrake?

---

### Post by squakie on 2013-08-25
Yep - everything has worked fine (so far) on over 150 DVD's until this one.  I did find [this ]("http://forums.macrumors.com/showthread.php?t=599134")thread on the net for someone with the same problem on the same DVD and it appears to be a decoding problem.  That thread is for a MAC and mentions a program there to use first, then use Handbrake on the output.  Perhaps k9copy will do that for me - I'll give it a try.  BTW - a responder in that MAC thread says that Handbrake exits the encoding like that when there is a decoding problem.

---

### Post by carl4926 on 2013-08-25
Good luck
Let us know what transpires

---

### Post by squakie on 2013-08-25
Hummmmm, no k9copy in the repositories for 13.04.  Found a link to launchpad, but the only pre-built is a .deb for 64-bit and I'm running 32-bit.  Hummmmmmmmm.

Going to try looking around for other programs - maybe a linux equivalent to the MAC program mentioned in the other thread.

---

### Post by squakie on 2013-08-25
Installed and tried dvd:rip since it seems to be mentioned on the web.  It encountered a problem on the rip almost immediately - said there is something wrong with the libdvdread installation, so obviously this weird decoding problem persists for this single DVD even in dvd:rip.

I'll keep looking - maybe I'll have to try compiling k9copy from source (oh the joy!).

---

### Post by carl4926 on 2013-08-25
There are also
DVD95
OGMRip

Is libdvdcss2 present on your machine

---

### Post by squakie on 2013-08-25
Yep - have had that installed long before I ever started this project.  Thanks though!

I installed AcidRip - it will decode the movie, but there are problems:  on playback it stalls every 5 seconds or so for about 2 seconds, and right from the start the audio and video are out of sync.

I think for now it may just have to be a movie I keep on DVD for playback, though the idea of the media center was to get rid of the "pile".

Thanks again - let me know if you find anything and I'll keep this posted if I try something else or everntually have success.

---

### Post by squakie on 2013-08-25
Success!!!!  I downloaded and installed makemkv and ran the disk through it.  It reported several errors in some of the video_ts .ifo (?) files when it scanned.  When it finished I let it go ahead and create the mkv file.  After it finished, I used the largest mkv file as input to HandBrake and it all works great now!  It apparently can get around some things that Handbrake can't, at least initially.  Handbrake encoded it to m4v (mpeg4) which also shrunk the size from the 6+gig of the .mkv file to a 773meg .m4v file.  The resulting file seems to play fine.

In researching this on the net, it would appear to be a problem with decoding (perhaps the "damaged" ifo files?) that causes Handbrake to complete so quickly, and it's also been reported on some box set DVD's.  Makemkv prior to Handbrake solved this problem for me.

---

### Post by carl4926 on 2013-08-26
> **squakie said:**
> Success!!!!  I downloaded and installed makemkv and ran the disk through it.  It reported several errors in some of the video_ts .ifo (?) files when it scanned.  When it finished I let it go ahead and create the mkv file.  After it finished, I used the largest mkv file as input to HandBrake and it all works great now!  It apparently can get around some things that Handbrake can't, at least initially.  Handbrake encoded it to m4v (mpeg4) which also shrunk the size from the 6+gig of the .mkv file to a 773meg .m4v file.  The resulting file seems to play fine.

In researching this on the net, it would appear to be a problem with decoding (perhaps the "damaged" ifo files?) that causes Handbrake to complete so quickly, and it's also been reported on some box set DVD's.  Makemkv prior to Handbrake solved this problem for me.

WOW well done

---

### Post by squakie on 2013-08-27
Interesting - I just ran into this same problem with the Season 1 DVD set for the old television show "Cheers".  Had to follow the same process.  To top it off, makemkv couldn't process the last episode - kept saying i/o error, yet Handbrake was able to process THAT one.  Weird stuff.  I know squat about video so it beats me - just as long as I can get my stuff loaded I'm happy!

---

