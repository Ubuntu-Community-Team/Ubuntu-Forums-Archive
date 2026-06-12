---
title: "the output of an Mpeg PS (A+V) in Avidemux was just a bunch of text files.."
date: 2007-02-25
forum: General Help
---

### Post by billdotson on 2007-02-25
I don't really know anything about avidemux other than how to cut things out of video and put filters on it.  I don't know how it works and if it is supposed to output an mpeg as just a bunch of text.  Although when I saved my video as an avi and ogm it had the picture of the first frame of the video.. these were just text files.  I have read the documentation and that didn't really help me.. at all because I am not familiar with all the multimedia jargon.

---

### Post by chewearn on 2007-02-26
I have successfully encode some video files from DVD VOB to Xvid avi.  Perhaps, if you could describe the exact thing you are trying  to do, the steps you made, etc?

---

### Post by billdotson on 2007-02-26
I cut out the commericals set the output to mpeg ps (a+v) and chose DVD (lavc) as the video codec and copy for audio.  Then I told it to save.

---

### Post by chewearn on 2007-02-26
Ok, I tested my system with a short mpeg2 clip, using the same settings as you do:

1. if I simply select DVD (lavc) for video, Copy for audio and MPEG PS A+V as output, Avidemux hung up; I have to force quit
2. But if using the same settings, but I click on the configure button (after selecting DVD lavc), then the save button,...  the encoding dialog pop-up; a few minutes later, the new video file is encoded.

So, I am unable to reproduce your problem.

btw, do you open up the text files; is there any relevant info in them (maybe error messages)?  Just a shot.

---

### Post by billdotson on 2007-02-26
ok I guess it messed up or something because I did it again and one of those 'text' files later turns into the mpeg file.  

Oh yeah "Back to the Future" final output as mpeg PS (A+V) was 3.2GB.  

I hear people talking about .avi vs. mpeg alot and I have recently heard of .ogm.  
What the advantages/disadvantages of them and what codecs should I use with each one.  Generally I want to get my files as small as they can possibly be while still keeping quality so I can play them on my 2nd monitor using dual screen setup.  In avidemux how do you tell it what file size to put out and how do you know what the quality will be as an end result?? Thanks.

---

### Post by chewearn on 2007-02-26
> **billdotson said:**
> I hear people talking about .avi vs. mpeg alot and I have recently heard of .ogm.  
What the advantages/disadvantages of them and what codecs should I use with each one.  Generally I want to get my files as small as they can possibly be while still keeping quality so I can play them on my 2nd monitor using dual screen setup.  

avi is an AV file container, which I belief, originated by Microsoft.  Inside avi, you can have many different streams encoded in divx, xvid, etc.  The advantage of avi is compatibility.  The disadvantage is it is an old format with some limitations.

mpeg is more of a transport; it's a way to combine multiple video and audio streams into one, for "transportation".  Officially, the mpeg transport stream is usually described in part 1 of its ISO/IEC standard.

ogm is an open source file container, has better features compared to avi.


Which format to use depends on your specific situation.  I can give you example of my own:
1. For home-made video that I distribute to my family members (some who are non-tech savvy), I create standard compliant DVD-Video.  I still use Windows XP for this task, as I have not started trying out video editing software in Linux.

2. For colleagues and friends, I usually encode the videos in XviD/avi; many recent set-top DVD players, which has DivX capability, can playback XviD as well.  In addition, properly encoded XviD can be 6-7 times smaller in file size, compared to DVD.


> In avidemux how do you tell it what file size to put out and how do you know what the quality will be as an end result?? Thanks.

You can enter the quality factor in the codec configuration (Configure button), or use the Calculator button.  I use this rule of thumb for the Calculator:
For DVD, you can put one to two hours into one disc (4.2GB).  You simply select DVD5 in the medium list.
For XviD/avi. I set the video bitrate to between 800kbps to 1000kbps (depending on video duration and the file size I am targeting).  800kbps will allow two hours to fit into one 700MB CD.
 When you click Apply, the calculation will show the results, and put the bitrate into the codec configuration automatically.

Judging the final video quality is more an art than science; I mostly go by trial and error; after an initial trial by the rule of thumb above (using a short few minute clip), I adjusted the bitrate if necessary, then go for the full encoding.  Then, check the final file size and quality at few random scenes; adjust bitrate and reencode if necessary.

---

