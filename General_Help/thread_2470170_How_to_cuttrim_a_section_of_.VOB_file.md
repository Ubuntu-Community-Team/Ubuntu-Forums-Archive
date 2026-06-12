---
title: "How to cut/trim a section of .VOB file"
date: 2021-12-21
forum: General Help
---

### Post by satimis on 2021-12-21
Hi all,

Please advise how to cut a section of .VOB file?  Say e.g. after the start from 5 min of .VOB file (video) and end at 20min, i.e. duration=15 min.

Following command line works for me```

$ ffmpeg -i imput.VOB -t 00:02:00 -c copy output-2min.VOB

```

To cut/trim a section at the start of the .VOB file (video) for 2 min.

But I haven't figure out the command line cutting/trimming a section for 2 min after starting from 10 min (for example) of the video.

Please help.  Other solutions are also welcome.

Thanks

Regards

---

### Post by schragge on 2021-12-21
[-ss]("https://www.mankier.com/1/ffmpeg#-ss")? [-itsoffset]("https://www.mankier.com/1/ffmpeg#-itsoffset")?

---

### Post by satimis on 2021-12-21
> **schragge said:**
> [-ss]("https://www.mankier.com/1/ffmpeg#-ss")? [-itsoffset]("https://www.mankier.com/1/ffmpeg#-itsoffset")?
Hi,

Could you please explain in more detail?  Thanks

I found following thread
(using Copy and Input Seeking)
[https://ottverse.com/trim-cut-video-using-start-endtime-reencoding-ffmpeg/](https://ottverse.com/trim-cut-video-using-start-endtime-reencoding-ffmpeg/)

Tried their suggestion as follow, replacing .mp4 with .VOB

1)
$ ffmpeg -ss 00:00:15 -i inputVideo.VOB -to 00:00:25 -c:v copy -c:a copy outputVideo.VOB

2)
$ ffmpeg -i inputVideo.VOB -ss 00:00:15 -to 00:00:25 -c:v copy -c:a copy outputVideo.VOB

Both complained```

[mpeg2video @ 0x55753b87d500] Invalid frame dimensions 0x0

```

Regards

---

### Post by yetimon_64 on 2021-12-21
I've been doing a bit of video trimming lately with ffmpeg. I would do your task in 2 parts...

**1.** Trim the first [s]2 minutes (120 seconds)[/s] 5 minutes (300 seconds)...
```
ffmpeg -i "input-file.VOB" -ss 300 -vcodec copy -acodec copy "outfile-1.VOB"
```

**2.** Then I'd take the output file (outfile-1.VOB) from that first command and use it as the input in the next command.
     If you wish to cut the file to 15 minutes then the next command uses "900" (seconds) for the final length...
```
ffmpeg -ss 0 -i "outfile-1.VOB" -t 900 -c copy "output-file-2.VOB"
```

**Edit:** just noted the first post stated 5 minutes trimmed at the start. I adjusted the first command.
There is probably an simpler "one off" command for this but this is how I've been managing to trim my video files lately.
I've tried without success to "do it in one run".
**Edit 2: **"output-file-2.VOB" should give you the final result you mention in the first post.

Good luck, yeti.

---

### Post by satimis on 2021-12-21
> **yetimon_64 said:**
> I've been doing a bit of video trimming lately with ffmpeg. I would do your task in 2 parts...

**1.** Trim the first [s]2 minutes (120 seconds)[/s] 5 minutes (300 seconds)...
```
ffmpeg -i "input-file.VOB" -ss 300 -vcodec copy -acodec copy "outfile-1.VOB"
```

**2.** Then I'd take the output file (outfile-1.VOB) from that first command and use it as the input in the next command.
     If you wish to cut the file to 15 minutes then the next command uses "900" (seconds) for the final length...
```
ffmpeg -ss 0 -i "outfile-1.VOB" -t 900 -c copy "output-file-2.VOB"
```

**Edit:** just noted the first post stated 5 minutes trimmed at the start. I adjusted the first command.
There is probably an simpler "one off" command for this but this is how I've been managing to trim my video files lately.
I've tried without success to "do it in one run".
**Edit 2: **"output-file-2.VOB" should give you the final result you mention in the first post.

Good luck, yeti.
Hi,

Thanks for your advice.

My request is to trim a section in the .VOB file, not from the beginning, but after the video having run 10 min (for example) as the starting point.  Then trim the video from the starting point until 20 min which will be the end point and save the trimmed section of the video to the output file, say output.VOB

Regards

---

### Post by ajgreeny on 2021-12-21
This is the text of a small file I created a while ago to show how to do exactly what you want.  My only uncertainty is the .VOB file and as I have no working DVD drive I can't easily find one to test this.
It looks very much like a version of the way you tried.
> Command to cut video with ffmpeg

ffmpeg -i file.mp4 -ss 00:23:40 -t 02:01:00 -acodec copy -vcodec copy output.mp4

-i file			= input file
-ss			= start time, Hrs, Mins, Secs.
-t			= total time length of output file.
-acodec & vcodec copy	= copy codecs, ie do not re-encode; this speeds up process but you can set alternative codecs if you need to.
output.mp4		= Output filename.

You can cut a video into many parts or simply use this to remove a part.

---

### Post by satimis on 2021-12-21
> **ajgreeny said:**
> This is the text of a small file I created a while ago to show how to do exactly what you want.  My only uncertainty is the .VOB file and as I have no working DVD drive I can't easily find one to test this.
It looks very much like a version of the way you tried.

Tried your command line;

$ ffmpeg -i input.VOB -ss 00:23:40 -t 02:01:00 -acodec copy -vcodec copy output-1.VOB

warning:```

[svcd @ 0x558956e60380] VBV buffer size not set, using default size of 230KB
If you want the mpeg file to be compliant to some specification
Like DVD, VCD or others, make sure you set the correct buffer size
```

output-1.VOB  0 bytes

Following command line worked for me previously;
$ ffmpeg -ss 00:00:03 -i imput.VOB -to 00:00:08 -c:v copy -c:a copy output-2.VOB

but following warning popup.```

[svcd @ 0x55d11141bac0] VBV buffer size not set, using default size of 230KB
If you want the mpeg file to be compliant to some specification
Like DVD, VCD or others, make sure you set the correct buffer size
```

output-2.VOB  4.6 MB

How to fix the warning ?

Regards

---

### Post by TheFu on 2021-12-21
```
$ ffmpeg -i imput.VOB -t 00:02:00 -c copy output-2min.VOB
```

I'd use mkvmerge because it handles all the captions and subtitles in the clips automatically, unlike all other tools.

```
$ mkvmerge -o output-15min.mkv --split parts:02:00.0-20:00.0 input.VOB
```
This results in the VOB copy, no transcoding, and simply puts the clip into an mkv container. All the audio tracks, captions, subtitles and video tracks in that range are clipped too.  If you don't want an mkv container, you can pull the tracks out as you like using mkvextract.  There is a GUI for all the mkv tools, **mkvtoolnix-gui**. It is just a GUI in front of the CLI commands, so expect to type in the cut points by frame or times.  If you want frames, use the "--split frames=" option in mkvmerge.  IF you have automation creating accurate cuts for you, cutting by frame is the most accurate, assuming mpeg2 video.  Other media file types only allow cutting at keyframes, so the tools aren't frame-accurate without transcoding.

Another option:
BTW, if you want to transcode at the same time and have just 1 clip, handbrake can cut beginning and end parts off any video file supported.  On the main page of handbrake, there is a "Range:Chapters" pulldown. Change that to "Range:Seconds" and fill in the start/end time. 02:00.0 and 20:00.0 in your example. Then  choose the other transcode options and "Start". If you want multiple audio tracks and subtitle tracks, be certain to visit those tabs to ensure the tracks you want are included. By default, no subtitles/captions are typically included and only the first audio track.

Another option: 
**LosslessCut-linux.AppImage**  This is a GUI tool that creates ffmpeg commands. It is pretty simple, though I find it cumbersome to use. It accepts a few different EDL file input types or you can use the GUI to set different cut/clip areas. There is a snap version too, but it doesn't work for me due to failed snap package dependencies.  **This is probably the answer that most people would like**.  This program has trouble with some input files, which I don't know why. It did work for me initially, though I found the interface a little clumsy. Perhaps over time, my fingers will get better?  I get really frustrated when developers think everyone only uses a mouse.  Mice are slow, especially when the target for a client is tiny.

Of course, there is a Windows option ... VideoRedo. This is a commercial tool that is deceptively simple, but optimized for handling these types of clip/cutting. Some people have it working under WINE, but not me.  I'm just a happy customer for about the last decade.  This tool is one of the reasons I still have Windows around today. I've been trying to replace it with Linux-based video editors for a very long time. The keyboard shortcuts on it are amazing and well-thought-out.  Getting frame-accurate locations for clips is very fast.  The project files with cut locations are something that other Linux-based tools like comskip support/generate.  The batch mode is a little clunky, but I have a script that takes the VPrj project file and takes the clip/cut marked locations from it, then generates an mkvmerge command that cuts the parts I'm not interested in.  For stuff that doesn't need perfect cuts, I'll just use mplayer to quickly create an EDL file, then feed that into a slightly different script which generates an mkvmerge command (again). My fingers are crazy fast with editing using these tools.  Sadly, mpv doesn't have the same EDL creation file capability and mpv decided they'd improve (i.e. drop) on the mplayer EDL file format.

Having a script that generates another script is called meta programming.  It isn't very difficult, especially if we just want to take the poorly formatted output from 1 command and re-format it for another command.

---

### Post by satimis on 2021-12-21
Hi all,

Following command line works for me seamlessly.

$ ffmpeg -i input.VOB -target pal-vcd -ss 00:02:10 -to 00:03:18 -c:v copy -c:a copy output-10.VOB

-ss 00:02:10 is the starting time to trim
-to 00:03:18 is the ending time to stop trimming
(this is the section of video which I need to trim)

-target pal-vcd  = buffer size

No complaint.

Now another question is "How to find the starting and the ending times"?  I found them by testing.  But this is not the correct way ?

Regards

---

### Post by TheFu on 2021-12-21
> **satimis said:**
>  Now another question is "How to find the starting and the ending times"?  I found them by testing.  But this is not the correct way ?

What criteria do you use to determine the start and end times?  That would determine the best way.  What level of accuracy is needed? A human can press a key with 0.2sec accuracy, which can be used to set the start and end times if there are a few seconds (or more) between them.

A little script that can create an EDL file while viewing a video using mplayer.  It shows the times in the upper left corner. Normal keyboard controls work ... jump forward, backwards and press "i" to start and stop cut markers. Those are written to the EDL file.  The last output is the mplayer command to playback the video, using the EDL file to show only the parts marked to be viewed.

```
#!/bin/bash

IN="$1"
EDLFILE="${IN%.*}".edl
mplayer -osdlevel 3  -edlout "$EDLFILE" "$IN" 

echo "Play using:
mplayer -osdlevel 3  -edl \"$EDLFILE\" \"$IN\"
```

The edl file would look something like this (those are seconds): 
```
3007.354000     3063.076000     0
3205.302000     3319.065000     0
3345.825000     3353.750000     0
...

```

There are plenty of other methods, but this is a quick way to get a 12GB video down to 200MB for finer editing, if needed.  Then I feed that EDL file into a script that generates an mkvmerge command to put the clips into a new file. That mkvscript is about 90 lines long - mainly to convert from seconds into hh:mm:ss.ssss for each time from the EDL. It isn't hard, just work. If I'd used a module instead of creating the conversion/parsing manually, my code would be smaller, but it would have an external dependency.  

For those that wonder why?  I create summary clips of sporting events.  Taking a 3 hour event and cutting it down to 10 minutes of highlights is the goal. Doing that as quickly as possible, perhaps 30 seconds total per event is about all the time I'd want to spend.  Imagine trying to clip a pole vault competition with 10 participants, but you only care about 2 of them. the first few rounds are longer, but if you know the order of the vaulters and that each attempt is about 60 seconds, you can jump close to the vaults that are of interest.

It just happens that these same scripts/techniques can be used to quickly remove commercials from recorded TV too.  Commercial blocks are usually 2-3 minutes, which means that skipping forward 2 minutes at a time will seldom miss a commercial block. Backup a bit, see the start of a commercial, drop a cut marker there, jump forward 2 min .. then move forward 15s at a time ... hard to explain how quickly this can happen once your fingers have the forward/backward jumps memorized, drop another cut-marker and start skipping forward to the next commercial block.

---

### Post by Dennis N on 2021-12-21
> Other solutions are also welcome.
You can also do this with with Openshot. No commands to learn.

---

### Post by yetimon_64 on 2021-12-21
> **satimis said:**
> ....Please advise how to cut a section of .VOB file?  Say e.g. after the start from 5 min of .VOB file (video) and end at 20min, i.e. duration=15 min....

Regards

> **satimis said:**
> Hi,

Thanks for your advice.

My request is to trim a section in the .VOB file, not from the beginning, but after the video having run 10 min (for example) as the starting point.  Then trim the video from the starting point until 20 min which will be the end point and save the trimmed section of the video to the output file, say output.VOB

Regards
My first command...
```
ffmpeg -i "input-file.VOB" -ss 300 -vcodec copy -acodec copy "outfile-1.VOB"
```
...starts copying the original file from the 5 minute (300 second) mark, "**-ss**" is the **starting point** of the copying process, and copies everything after the 5 minute mark to the end of the file.

The second command using the trimmed output from the first command...
```
ffmpeg -ss 0 -i "outfile-1.VOB" -t 900 -c copy "output-file-2.VOB"
```
...saves the first 15 minutes (900 seconds) of the cropped file (first five minutes of the source file has been removed by the first command).

The final file "output-file-2.VOB" is a copy of the original file from the 5 minute mark to the 20 minute mark as per the first quote above from your opening post.

I have been using these 2 commands to trim the start and end of video files including with VOB files. Cheers, yeti.

---

### Post by TheFu on 2021-12-21
> **Dennis N said:**
> You can also do this with with Openshot. No commands to learn.

Openshot takes much longer to learn than mkvmerge.  Probably 20x longer, IMHO.

Full featured GUIs like openshot provides are hardly intuitive.  There are 20-part youtube videos on using Openshot. One guy redoes all his videos every 2-4 yrs because the program changes enough in that time that re-learning it is needed.

---

### Post by yetimon_64 on 2021-12-21
> **satimis said:**
> ...Please advise how to cut a section of .VOB file?  Say e.g. after the start from 5 min of .VOB file (video) and end at 20min, i.e. duration=15 min....

Give this next command a try out, I just managed to crop a VOB file at a starting point in the file and to a set length (five minutes in my test case). It seems I have managed to combine my usual 2 commands into one...

```
ffmpeg -ss 300 -i "input.VOB" -t 900 -c copy "output.VOB"
```
This command should start copying your file from the 5 minute mark to the 20 minute mark and save as "output.VOB" in one command. I tested here on a VOB file removing the first 17 seconds of the source and copied only 5 minutes of an 11 minute VOB file. Good luck, hope this works for you as well.

My command that worked successfully here for a VOB file on my desktop...
```
ffmpeg -ss 17 -i "VTS_02_1.VOB" -t 300 -c copy "test1.VOB"
```

**Edit:** I repeated my testing with your timing style "00:15:00" etc ...
```
ffmpeg -ss 00:00:17 -i "VTS_02_1.VOB" -t 00:05:00 -c copy "test2.VOB"
```
... and this worked as well.

For your command example from your first post I'd try...
```
ffmpeg -ss 00:05:00 -i "input.VOB" -t 00:15:00 -c copy "output.VOB"
```

**Edit 2:** re TheFu's post next. I missed that post # 9 sorry for any confusion created here.

---

### Post by TheFu on 2021-12-21
satimis found the OP solution in post #9 above and asked a different question - which really should be a different thread to prevent the sort of confusion happening now.

Best to close this thread as "SOLVED" and start a new one with the new question.

---

### Post by satimis on 2021-12-22
> **TheFu said:**
> satimis found the OP solution in post #9 above and asked a different question - which really should be a different thread to prevent the sort of confusion happening now.

Best to close this thread as "SOLVED" and start a new one with the new question.
Yes you're right

Just have mplayer version 2:1.3.0-8build5 installed.

It is very strange that there is no sound playing the video.  Besides there is no button on the screen.  Neither I know how to stop playing the video.  Please refer to attached screenshots;
screenshot_mplayer-1.png
screenshot_mplayer-2.png

On OpenShot Video Editor
Also I found there is an indication of running time there above timeline at the left corner.
Please refer to attached screenshots;
screenshot_openshot.png

Regards

---

### Post by TheFu on 2021-12-22
> **satimis said:**
>  
Just have mplayer version 2:1.3.0-8build5 installed.

It is very strange that there is no sound playing the video.  Besides there is no button on the screen.  Neither I know how to stop playing the video.  Please refer to attached screenshots;
screenshot_mplayer-1.png
screenshot_mplayer-2.png 

That is expected with mplayer. It is a GUI-less tool.  It accepts keyboard inputs, based on the keyboard setup you create (or use the defaults which are documented in the manpage for mplayer).

right arrow skips forward.  - I think the default is 10 seconds.
left arrow skips backwards.
up/down arrows skip farther - I think the default is 1 minute.
spacebar pauses/starts playback.
"j" changes the subtitle/caption track.
"#" changes the audio track.

All of those can be modified as you like.  Volume up/down are 9/0.  There are a few other keyboard controls, but for a long time, I used just those.  mpv uses the same ones for the most part, but it lacks the EDL creation capability - last time I looked. Plus, I dislike the complex EDL file format used by mpv.

There are different modes.  I've never used smplayer, but I think that's a GUI over mplayer. Don't know anything about it. Sorry.

My script with EDLFILE inside shows the mplayer options that allow creating an EDL file using the 'i' key to mark start/end points.  I don't recall if these are for cuts or clips, since the resulting EDL file is fed into another script that does what I need. It is all muscle memory now for me.

If mplayer isn't causing any audio output, then I'd guess the pulseaudio setup on the box isn't correct. Open a new thread for help with that specific thing.
Actually, for help with mplayer editing, open a new thread.  It isn't 'exact', just close enough editing.  I find the OSD (on screen display) is handy for when I miss a marker location and need to rewind and try to get it the next time.

BTW, just running **mplayer** without any CLI arguments isn't very useful.  **Pass in the name of the videos.**
```
mplayer ./video.file.mkv
```

---

### Post by satimis on 2021-12-22
> **TheFu said:**
> That is expected with mplayer. It is a GUI-less tool.  It accepts keyboard inputs, based on the keyboard setup you create (or use the defaults which are documented in the manpage for mplayer).

right arrow skips forward.  - I think the default is 10 seconds.
left arrow skips backwards.
up/down arrows skip farther - I think the default is 1 minute.
spacebar pauses/starts playback.
"j" changes the subtitle/caption track.
"#" changes the audio track.

- snip -


Hi,

Thanks for your further advice.  I need to config skin and to install driver before I can have sound on mplayer.  

Since I found OpenShot can do the same job.  I won't use mplayer.

Regards

---

### Post by TheFu on 2021-12-22
Openshot does 10,000x more things when compared to mplayer. The memory, CPU, GPU and storage requirements should be sufficient for why.

You don't need any "skin" for mplayer audio to work. It is a pulseaudio issue. Nothing wrong with mplayer.

But some people need more that what mplayer provides, which is 100% fine. But if you just want to quickly mark clip/cut points, I doubt any tool is faster than mplayer.  By the time Openshot starts, I'd be halfway through an hour long TV show marking all the commercial locations to be removed in a "close-enough" way.

Choosing the right tool for the right job is all we hope for you.

---

### Post by Kanehekili on 2022-04-27
Hi, an easy way to cut chunks out of a large video is to use [Videocut]("https://github.com/kanehekili/VideoCut") which I've written for Linux. Using an improved muxer (based on ffmpegs libavcodec library) it can be downloaded from my [ppa]("https://launchpad.net/~jentiger-moratai/+archive/ubuntu/mediatools"). The cutting is lossless, since I do not touch the packages. 
The interface is supposed to be simple (I don't seem to be able to share a picture...)

Runs on bionic,focal and jammy

---

### Post by TheFu on 2022-04-27
> **Kanehekili said:**
> Hi, an easy way to cut chunks out of a large video is to use [Videocut]("https://github.com/kanehekili/VideoCut") which I've written for Linux. Using an improved muxer (based on ffmpegs libavcodec library) it can be downloaded from my [ppa]("https://launchpad.net/~jentiger-moratai/+archive/ubuntu/mediatools"). The cutting is lossless, since I do not touch the packages. 
The interface is supposed to be simple (I don't seem to be able to share a picture...)

Runs on bionic,focal and jammy

No Bionic version in the PPA. I hope this is an oversight and can be corrected. Support for 18.04 Ubuntu Desktop has another year of support.

BTW, necro-posting here isn't usual.

---

