---
title: "Sooooooo close! (iPod videos)"
date: 2008-01-11
forum: General Help
---

### Post by FRuMMaGe on 2008-01-11
Ever since I installed Gutsy, I have not been able to encode videos for iPod because of an unknown AAC codec (I tried everything). I finally managed to fix it by upgrading my ffmpeg with the one in the medibuntu repositories.

I can now encode videos for iPod, but when I transfer them to the iPod, there is no audio track.

I have tried with both gtkpod and amarok, but it only ever transfers the video track.

I have played the videos on my laptop and they seem fine.

What is wrong? And how can I fix it?

---

### Post by kostkon on 2008-01-11
Yes, you did the right thing that you installed *FFmpeg* from the *Medibuntu* repository. I would reccomend you to try to find a GUI frontend for *FFmpeg*, like [*WinFF*]("http://biggmatt.com/winff/"). This is the one that I use and I encode videos for iPod that play just fine.

---

### Post by articpenguin on 2008-01-11
go here
[https://wiki.ubuntu.com/ffmpeg]("https://wiki.ubuntu.com/ffmpeg")

---

### Post by FRuMMaGe on 2008-01-11
> **kostkon said:**
> Yes, you did the right thing that you installed *FFmpeg* from the *Medibuntu* repository. I would reccomend you to try to find a GUI frontend for *FFmpeg*, like [*WinFF*]("http://biggmatt.com/winff/"). This is the one that I use and I encode videos for iPod that play just fine.

I am already using WinFF. I have tried others, but it seems to be the best

Still no audio when it's on the iPod though :(

---

### Post by FRuMMaGe on 2008-01-14
Gtkpod no longer works with mp4. It says they are not a valid mp4 file.

Could this be the problem?

---

### Post by ellgor on 2008-01-14
> **FRuMMaGe said:**
> Ever since I installed Gutsy, I have not been able to encode videos for iPod because of an unknown AAC codec (I tried everything). I finally managed to fix it by upgrading my ffmpeg with the one in the medibuntu repositories.

I can now encode videos for iPod, but when I transfer them to the iPod, there is no audio track.

I have tried with both gtkpod and amarok, but it only ever transfers the video track.

I have played the videos on my laptop and they seem fine.

What is wrong? And how can I fix it?

Hi,

Try Thin Liquid Film, as the title suggests its for transferring to ipod,yea, anyway give it a shot and hope it helps.

Regards, Ellgor.

---

### Post by FRuMMaGe on 2008-01-14
> **ellgor said:**
> Hi,

Try Thin Liquid Film, as the title suggests its for transferring to ipod,yea, anyway give it a shot and hope it helps.

Regards, Ellgor.

Is there a deb for it?

I've tried to compile it on a number of occasions but it keeps requiring me to find more libraries.

I keep installing them but it always needs more

---

### Post by ironwolfe on 2008-01-15
I am having the same problem.  I think it has something to do with the AAC encoder, but I am not all that great at troubleshooting...

here is another thread that is talking about the same thing:
[http://ubuntuforums.org/showthread.php?t=530067](http://ubuntuforums.org/showthread.php?t=530067)

I will let you know if anything works.  I am using floola to move videos - the sound works when I play the file (located on the ipod harddrive) using the desktop floola app - the file seems fine - seems the ipod may not like the aac...

---

### Post by FRuMMaGe on 2008-01-15
AAARGH!

I finally managed to sort out gtkpod so it doesn't come up with the error when importing mp4's, but there is still no sound!

What is wrong!!!

---

### Post by ironwolfe on 2008-01-15
I am noticing that there might be a commonality between the cases I have seen... out of curiousity did you use floola?

---

### Post by FRuMMaGe on 2008-01-15
> **ironwolfe said:**
> I am noticing that there might be a commonality between the cases I have seen... out of curiousity did you use floola?

No, but floola is a gui for gtkpod anyway I think

I think it is due to gtkpod-aac being broken in Gutsy.

Can anyone on Gutsy confirm that their mp4 files are working?

---

### Post by articpenguin on 2008-01-15
when i was on gutsy i got mp4 files encoded for my psp using ffmpeg. But in hardy (alpha version of ubuntu) my ffmpeg wont compile.

---

### Post by ironwolfe on 2008-01-15
Ok I have isolated the problem.

I transcoded the same file using videora under windows.  I then transferred this H264 file to my linux machine and used floola to transfer the file to the ipod.

It works with audio.

I can now say with certainty that it is the AAC encoding used by ffmpeg.

What can I do to fix this - I don't want to go to my windows virtual machine everytime I want to encode a video for my ipod.

Any ideas?  I have heard about Nero's codec, but I have no idea how to install it let alone how to get ffmpeg to use it.

Any linux jedi's out there?

---

### Post by ironwolfe on 2008-01-15
I should also say that I have installed:

FAAC 1.25-0.1
libfaad2-0
faad 2.0.0
ffmpeg 3:0.cvs20070307-5ubuntu4+medibuntu3
gstreamer0.10-plugins-bad-multiverse 0.10.5-1
as well as most of the gstreamer plugins and ubuntu restricted extras
aacplusenc 0.12-0medibuntu1 (added this thinking it would solve the problem)

I have used:
floola
TLF
avidemux
ffmpeg with bash script

nothings works except doing encoding in Windows

---

### Post by FRuMMaGe on 2008-01-15
> **ironwolfe said:**
> Ok I have isolated the problem.

I transcoded the same file using videora under windows.  I then transferred this H264 file to my linux machine and used floola to transfer the file to the ipod.

It works with audio.

I can now say with certainty that it is the AAC encoding used by ffmpeg.

What can I do to fix this - I don't want to go to my windows virtual machine everytime I want to encode a video for my ipod.

Any ideas?  I have heard about Nero's codec, but I have no idea how to install it let alone how to get ffmpeg to use it.

Any linux jedi's out there?

Great find!

This will help alot.

Do you think it is a problem with ffmpeg or the AAC library?

Should we try it with mencoder?

---

### Post by FRuMMaGe on 2008-01-15
Well guys, I took into account the help from ironwolfe.

I have good news and bad news.

The bad news is that I have tried literally every suggestion from every forum and over 5 hours of googling and I still don't know how to fix ffmpeg or faac.

The good news is that I have found a fully working alternative! There is a windows application called  MediaCoder that works perfectly in WINE! In fact, it even has "Linux with Wine" listed as one of the compatible operating systems.

I have tried and tested it and every video I have encoded so far has turned out perfectly!

[HERE IS MEDIACODER]("http://mediacoder.sourceforge.net/")

---

### Post by ironwolfe on 2008-01-15
I hate doing things in wine, but until FAAC is fixed I think it is the best option... 

I am reading up on how to use Nero's AAC encoder but it seems to be a little tough, and may require wine anyway - can anyone confirm this? or know how to replace FAAC with the Nero encoder?

Any other alternatives to FAAC?

Thanks - I will let you know if it works for me, I am installing firefox for wine as I type...

---

### Post by ironwolfe on 2008-01-16
Thanks for the advice on MediaCoder - works great!

I will post updates if I can get an AAC encoder working in ubuntu

---

