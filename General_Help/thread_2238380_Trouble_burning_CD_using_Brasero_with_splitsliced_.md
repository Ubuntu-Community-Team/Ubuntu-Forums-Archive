---
title: "Trouble burning CD using Brasero with split/sliced track"
date: 2014-08-07
forum: General Help
---

### Post by AbleTassie on 2014-08-07
I am having trouble burning a CD using Brasero after I slice a single track file into multiple equal length tracks (each smaller track 180 seconds long). I get the following error messages:

   [B]Ejecting medium
[/B]
**Error while burning**
**GStreamer encountered a general stream error.**

I am able to burn a CD using the single track file if I do not slice the single track up. And this CD works fine -- I can listen to it. But I would like to slice up the track so I can start or stop the CD midway while listening to it and then go back to it.

Any idea what I could do to overcome the problem?

Thanks,

R.

---

### Post by slooksterpsv on 2014-08-08
Mmmk, a few questions here:
1. When splitting the track - what format are you splitting it to? MP3, OGG, MP4, WMA, etc.
2. How many tracks are you putting on the CD? 5 10 50 100?

It looks like the issue may be with how you're splitting the tracks. That's why I'm curious about the audio format.

---

### Post by AbleTassie on 2014-08-08
> **slooksterpsv said:**
> Mmmk, a few questions here:
1. When splitting the track - what format are you splitting it to? MP3, OGG, MP4, WMA, etc.
2. How many tracks are you putting on the CD? 5 10 50 100?

It looks like the issue may be with how you're splitting the tracks. That's why I'm curious about the audio format.

The track (file) starts as MP3 and is split into 10 or 11 MP3 tracks. For splitting I select "[LEFT][COLOR=#333333][FONT=sans-serif]Split track in parts with a fixed length[/FONT][/COLOR][/LEFT]
." I set the track length to 180 seconds for the track length of each split track. The playing time of the original MP3 track is about 30 minutes. The playing time of each split track is 3 minutes (180 seconds).  

I can burn one single small 3 minute track onto a CD and it works. But I cannot burn two single consecutive tracks onto a CD.

Thanks,

R.

---

### Post by AbleTassie on 2014-08-08
For what it is worth, here is the Brasero session log for a session that failed:

Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1739)
BraseroNormalize called brasero_job_get_action
BraseroNormalize called brasero_job_get_action
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_action
BraseroNormalize called brasero_job_get_session_output_size
BraseroNormalize Output set (AUDIO) image = /tmp/brasero_tmp_EOTMKX.cdr
BraseroNormalize called brasero_job_get_session_output_size
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_tag_lookup
BraseroNormalize Analysing track file:///home/name/GreatCoursesCSLewis/TGC_297_Lect01_LifeWritingsCSLewis.mp3
BraseroNormalize Creating new pipeline
BraseroNormalize called brasero_job_set_current_action
BraseroNormalize New decoded pad linked
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize called brasero_job_get_tracks
BraseroNormalize Setting track peak (0.679976) and gain (-1.400000)
BraseroNormalize called brasero_job_tag_lookup
BraseroNormalize Analysing track file:///home/name/GreatCoursesCSLewis/TGC_297_Lect01_LifeWritingsCSLewis.mp3
BraseroNormalize Creating new pipeline
BraseroNormalize New decoded pad linked
BraseroNormalize gstbaseparse.c(3188): gst_base_parse_loop (): /GstPipeline:pipeline6/GstDecodeBin:decodebin6/GstMpegAudioParse:mpegaudioparse8:
streaming stopped, reason error
BraseroNormalize called brasero_job_error
BraseroNormalize finished with an error
BraseroNormalize asked to stop because of an error
    error        = 1
    message    = "GStreamer encountered a general stream error."
BraseroNormalize stopping
Session error : GStreamer encountered a general stream error. (brasero_burn_record brasero-burn.c:2856)

---

### Post by AbleTassie on 2014-08-08
It looks like I may have been mistaken: the smaller single split track I can burn onto a CD is a .wav file, not an MP3 file. On the other hand the larger (parent) file that is split is an MP3 file.

I am not sure what this means.

R.

---

### Post by slooksterpsv on 2014-08-09
Try converting the wav files to mp3 files. You can use XFCA to do the conversion (batch conversion as well), you may need to install additional software like lame or ffmpeg for the mp3 coding. I know lame for sure, not sure about ffmpeg.

---

### Post by AbleTassie on 2014-08-09
> **slooksterpsv said:**
> Try converting the wav files to mp3 files. You can use XFCA to do the conversion (batch conversion as well), you may need to install additional software like lame or ffmpeg for the mp3 coding. I know lame for sure, not sure about ffmpeg.

Thanks slooksterpsv,

What is XFCA? Is it an application? It does not appear to be in the software center. How do I get it?

R.

---

### Post by slooksterpsv on 2014-08-09
I always do that, it's xcfa not xfca - I always spell that one wrong, so yeah its called:
**X C**onvert **F**ile **A**udio - XCFA - I'm typing it a lot so I remember haha - XCFA xcfa xcfa I think I got it now for how to spell it.

---

### Post by AbleTassie on 2014-08-09
Thanks slooksterpsv, 

I installed XCFA and ffmpeg, can't find lame in the download center, however. It looks like it is available elsewhere though. Any suggestions as to how to download & install lame?

R.

---

### Post by Dennis N on 2014-08-09
> **RMcGinnis said:**
> I installed XCFA and ffmpeg, can't find lame in the download center, however. It looks like it is available elsewhere though. Any suggestions as to how to download & install lame?

Install lame from the Ubuntu repositories with either Synaptic Package Manager, or the terminal:

```
sudo apt-get install lame
```

---

### Post by AbleTassie on 2014-08-22
I was not able to process tracks that were generated by splitting using Brasero, because there was no way to save or export the tracks after they were generated.  So I could not use XCFA or anything else for that matter. I could not even use Brasero to burn those multiple tracks onto a CD.    

I recently upgraded from Lubuntu 13.10  to Lubuntu 14.04.1 LTS and suddenly I was able to burn multiple tracks to a CD using Brasero-- but there were some problems. The first track was placed last on the CD -- rather awkward. In addition, I could only split the large mp3 file using the "Split track in a fixed number of parts," I could not use  "Split track in parts with a fixed length," as I had been able to do before with Lubuntu 13.10 & Brasero. So it appears Brasero has some bugs.  

Anyway, I finally just gave up on splitting a large audio file, e.g., mp3, with Brasero. I tried using Audacity, and I could split files, but I found it was too cumbersome with Audacity. Maybe if I used Audacity more it would have become less so. But I looked around and found this link [http://askubuntu.com/questions/27574/how-can-i-split-a-mp3-file/27575#27575](http://askubuntu.com/questions/27574/how-can-i-split-a-mp3-file/27575#27575)  , which recommends both  mp3splt and mp3DirectCut running in WINE.   I just tried mp3splt (notice this is mp3splt, not mp3split with an "i"); mp3splt is in the Repos; mp3splt seems to work well, I can easily add (or import) the mp3splt generated split tracks into Brasero in the correct order and burn a CD, and the tracks on the CD are in the right order and seem to play fine. So I am going to mark this thread as SOLVED. 

 Thanks to everybody,  

R.

---

