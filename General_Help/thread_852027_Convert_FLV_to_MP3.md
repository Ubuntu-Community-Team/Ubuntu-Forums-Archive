---
title: "Convert FLV to MP3?"
date: 2008-07-07
forum: General Help
---

### Post by ForksHolder on 2008-07-07
Hello,

Do you know how can i convert FLV to MP3?

Thanks.

---

### Post by BLTicklemonster on 2008-07-07
Good luck. The only salvation I found was installing freez flv to avi mpeg wmv converter in wine. Convert, then edit in avidemux.

---

### Post by SpEcIeS on 2008-07-07
Try using FFMPEG it makes this sort of thing very easy. That is if you like command line. :)

---

### Post by BLTicklemonster on 2008-07-07
I tried that and got errors on all kinds of different things like bitrate and video size so I gave up, gave in, and put a free windows program in wine.

NOW THAT REALLY SUCKS, but ya gotta do what ya gotta do. (I just hope someone somewhere is sufficiently embarrassed by this and takes action to correct it. I would, but I don't know nuttin' about no codin' )

---

### Post by Hubi17 on 2008-07-07
I normally use the pytube script. So far never had any problems

---

### Post by FakeOutdoorsman on 2008-07-07
FFmpeg from the repository is not compiled to support restricted formats such as mp3.  You can use a third-party repository such as Medibuntu, compile ffmpeg yourself, or use another program such as mencoder.

The basic command:
```
ffmpeg -i inpuvvideofile.flv outputaudiofile.mp3
```
By default this will create a 64 kb/s file.  You can declare the audio bitrate with -ab:
```
ffmpeg -i inpuvvideofile.flv -ab 128k outputaudiofile.mp3
```
If the flv already has mp3 audio, then there is no need to re-encode.  You can just copy the audio stream.  This will preserve the audio quality and will be much quicker since there is no re-encoding:
```
ffmpeg -i inpuvvideofile.flv -acodec copy outputaudiofile.mp3
```
Don't know what the audio is?  Just ask ffmpeg:
```
ffmpeg -i inputvideo.flv
```
Along with some other information, ffmpeg will provide file details with the above command:
```
Stream #0.0: Video: flv, yuv420p, 320x240, 29.97 tb(r)
Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 56 kb/s
```

---

### Post by necromantula on 2008-07-07
> **FakeOutdoorsman said:**
> FFmpeg from the repository is not compiled to support restricted formats such as mp3.  You can use a third-party repository such as Medibuntu, compile ffmpeg yourself, or use another program such as mencoder.
```
ffmpeg -i inpuvvideofile.flv outputaudiofile.mp3
```
By default this will create a 64 kb/s file.  You can declare the audio bitrate with -ab:
```
ffmpeg -i inpuvvideofile.flv -ab 128k outputaudiofile.mp3
```

I would reccomend this, but not encoding to 128k, as youtube FLV files encode their audio at 64kb. Upcoding like this will not increase quality, merely file size. Other flvs from other sites may contain higher quality audio however.

---

### Post by ForksHolder on 2008-07-08
> **FakeOutdoorsman said:**
> FFmpeg from the repository is not compiled to support restricted formats such as mp3.  You can use a third-party repository such as Medibuntu, compile ffmpeg yourself, or use another program such as mencoder.
```
ffmpeg -i inpuvvideofile.flv outputaudiofile.mp3
```
By default this will create a 64 kb/s file.  You can declare the audio bitrate with -ab:
```
ffmpeg -i inpuvvideofile.flv -ab 128k outputaudiofile.mp3
```


Thank you very much :)

Sloved.

---

### Post by thomasaaron on 2008-08-18
Here's a good way to do it...
[http://vixy.net/](http://vixy.net/)

---

### Post by paulmerchant on 2008-08-18
Avidemux.

With many FLV files, you can rip the audio stream quickly and easily. Just File | Open the FLV and then Audio | Save... the MP3. Just make sure your Audio setting is set to copy unless you have to convert it from another type of stream.

---

### Post by mike1234 on 2008-08-18
[https://addons.mozilla.org/en-US/firefox/addon/3006](https://addons.mozilla.org/en-US/firefox/addon/3006)

 Don't forget to set it up in "preferences". Works great! (Need ffmpeg installed too in synaptic).

M.

---

### Post by mb_webguy on 2008-08-18
You can also transcode files with VLC.  Just open the file and then select Wizard from the File menu.  Choose "Transcode/Save to File", then "Existing Playlist Item" and select the file.  Check to transcode the audio and video, and select your codecs and bitrates.  Select your container format, then specify the filename (and be sure to use the appropriate file extension for the container format chosen, since it won't add it for you AFAIK).  When you click finish, it will begin transcoding the file.  All you'll see is the seek bar moving across, so don't get impatient and click stop or anything until it's done.

Alternatively, if you're grabbing videos off of YouTube or another video website using Flash videos, you can install the [Video DownloadHelper]("https://addons.mozilla.org/en-US/firefox/addon/3006") extension for Firefox, which will let you easily download and convert videos from the website.

---

### Post by mkarnicki on 2008-08-26
This is why I love linux. (Particularly Ubuntu, which I am using). Now I know at least 3 ways to convert flv 2 mp3, and it took me a minute or so to google it and again land on ubuntuforums. Cheers. (Help mods, mark as SOLVED).

Bye!

---

### Post by whitethorn on 2008-08-26
I use ffmpeg and here are the codes I use.  One for .mp3 and one for .ogg

```
ffmpeg -i Some_youtube_video.flv -f mp3 -vn -acodec copy /destination/name.mp3
```

```
ffmpeg -i Some_YouTube_Video.flv -acodec vorbis -aq 60 -ac 2 Just_The_Audio.ogg
```

---

### Post by BLTicklemonster on 2008-08-27
> **mkarnicki said:**
> This is why I love linux. (Particularly Ubuntu, which I am using). Now I know at least 3 ways to convert flv 2 mp3, and it took me a minute or so to google it and again land on ubuntuforums. Cheers. (Help mods, mark as SOLVED).

Bye!

Hey, top of the page, click on thread tools, and you can mark it solved.

---

### Post by mkarnicki on 2008-08-29
> **BLTicklemonster said:**
> Hey, top of the page, click on thread tools, and you can mark it solved.

Thanks ;) , but I know how to do that. I wanted the author of the post do mark it solved. "Help mods" meant "Please help the moderators" ;)

---

### Post by BLTicklemonster on 2008-08-29
[IMG]http://ejcross.com/wp-content/uploads/2007/12/homer_simpson_doh_02.gif[/IMG]

---

### Post by TransitMan on 2008-08-30
You can also use WinFF with ffmpeg as the backend to convert.
I've used this without a problem.

WinFF download page - [http://www.winff.org/index.php?option=com_content&view=category&layout=blog&id=34&Itemid=60](http://www.winff.org/index.php?option=com_content&view=category&layout=blog&id=34&Itemid=60)

Install ffmpeg from the repos.

---

### Post by jumboshrimp11 on 2008-08-30
This website does the trick: [http://media-convert.com/](http://media-convert.com/)

---

### Post by mb_webguy on 2008-08-30
> **jumboshrimp11 said:**
> This website does the trick: [http://media-convert.com/](http://media-convert.com/)

Um... right.  First of all, I personally don't like the idea of passing my files through a website like that, as there's no guarantee that what I get back will be what was sent and *only* what was sent.  Not that we have to worry much about it on Linux, but that smells like a wonderful way to distribute viruses.

Second, the max file size on that site is 150MB.   I don't know about anyone else, but most of the videos I deal with are +300MB.  Granted, the OP is specifically talking about converting flv files, which are typically fairly small, but still...

Third, While the site does support an impressive number of file formats (to include documents and archives), it doesn't support the mkv container, or h.264 video -- either as an input or output.  While I suppose avi-xvid-aac is currently the most popular video format, I prefer mkv-x264-mp3.

True, the latter two reasons are basically personal preference, but the first is enough for me to avoid it.  Maybe I'm just paranoid...  but that doesn't mean people aren't out to get us.

---

### Post by TWO on 2008-11-10
Hello

I don't know if anyone is still interested in the topic, but I personally find that sometimes, a method that doesn't involve using the Terminal/Konsole is a better option, particularly for newcomers.

[http://sourceforge.net/project/downloading.php?groupname=utube&filename=utube_1.7-1_i386.gtk.deb&use_mirror=garr](http://sourceforge.net/project/downloading.php?groupname=utube&filename=utube_1.7-1_i386.gtk.deb&use_mirror=garr)

Is a link to download the .deb of the program uTube Ripper. Simply enter the URL of the YouTube video you desire, wait for the download to finish then convert the file to mp3. You will have to name the .mp3 file correctly with a tag editor though.

---

### Post by mybunche on 2008-12-03
I have tried utube ripper it does work but it wouldn't convert anything after about 3 files. Researching on google brought me to here, and one post above said use avidemux, which I had already installed. Avidemux can do other things as well so you don't need utube ripper, it's actually quicker.

1. Start Avidemux, Open, navigate to where your flash video is.
2. Click Audio, then Save, enter your file name with .mp3 extension.
   On left pane, leave Audio and Video as Copy. Should be as default anyway. 
3. In seconds, your mp3 file will be saved to your desktop (default location).

---

### Post by s.fox on 2008-12-03
I do it from terminal.  Try this

```
mplayer -dumpaudio nameofinput.flv -dumpfile nameofoutput.mp3
```

If you are getting your FLV files from youtube you could directly convert them to mp3 using a program called Pytube.  I believe it is in the synaptic package manager.

hope this helps

---

### Post by mybunche on 2008-12-03
Yea, I tried using ffmeg as well, which works, but I didn't I didn't I'm too lazy to paste the file name in, and too much typing. As well as I am not familiar with Avidemux so if I can learn that too, that's good. But command line, yea, have multiple ways of doing it.

---

### Post by BLTicklemonster on 2008-12-03
> **mybunche said:**
> I have tried utube ripper it does work but it wouldn't convert anything after about 3 files. Researching on google brought me to here, and one post above said use avidemux, which I had already installed. Avidemux can do other things as well so you don't need utube ripper, it's actually quicker.

1. Start Avidemux, Open, navigate to where your flash video is.
2. Click Audio, then Save, enter your file name with .mp3 extension.
   On left pane, leave Audio and Video as Copy. Should be as default anyway. 
3. In seconds, your mp3 file will be saved to your desktop (default location).

That's exactly what I do. Simple as pie!!!

---

### Post by bovier on 2009-01-19
I tried to save the audio file of my flv with ffmpeg -i flashvideo.flv -acodec copy  song.mp3 like somebody (thanks!) mentioned on the first page of this forum, and it worked, but the only problem was that for some strange reason the song was copied for eight times in a row... Doesn't matter, cause i like the song, but still quite strange...!

---

### Post by techphets on 2009-05-04
Someone said they love Ubuntu because they can find three ways to do something in a few minutes.  Well... 

I tried avidemux.  I tried mplayer.  I tried VLC.  Fail. Fail. Fail.

Something about MPEG audio layer 1/2/3 missing. 

Tried recompiling ffmpeg using [these]("http://symbiotix.net/articles/compiling-ffmpeg-mp3-ubuntu-revised-ubuntu-gutsy-server") instructions. 

Tried all three again.  Fail. Fail. Fail. 

I installed the Firefox VideoDownloader plug-in.  Fail. 

"Conversion requires an external application that appears to be missing on your system." 

.mp3 files do play. 

A few things I had to change when recompiling ffmpeg: 
apt-get install libmp3lame-dev instead of liblame-dev
added --enable non-free 
removed --disable-vhook 
removed --enable-liba52

Any ideas on what I should try next?

---

### Post by FakeOutdoorsman on 2009-05-04
Those instructions are out-dated.  I wrote a guide that I try to keep up to date for several Ubuntu versions:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

If you don't feel comfortable with the above guide or want a quicker solution:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

Now for the command (assuming the input.flv has mp3 audio):
```
ffmpeg -i input.flv -acodec copy output.mp3
```

---

### Post by PTSnoop on 2009-05-07
FFmpeg works for me for some .flv files, but for others I just get a message about an unsupported codec and then an empty file. Can anyone help? Is this something to do with "assuming the input.flv has mp3 audio"?

---

### Post by FakeOutdoorsman on 2009-05-07
Show the output of:
```
ffmpeg -i input.flv
```

---

### Post by PTSnoop on 2009-05-07
```
[flv @ 0xb7f7e110]Unsupported video codec (7)
```
...repeated 1017 times, followed by:
```

Input #0, flv, from 'ToxicJazz.flv':
  Duration: 00:05:02.6, start: 0.000000, bitrate: N/A
  Stream #0.0: Video: 0x0007, 1000.00 fps(r)
  Stream #0.1: Audio: 0x000a, 44100 Hz, stereo
Must supply at least one output file

```

---

### Post by FakeOutdoorsman on 2009-05-07
You didn't include the FFmpeg version information.  What version of Ubuntu are you using?  Is the video available for download?

---

### Post by PTSnoop on 2009-05-08
I'm using Hardy, and the ffmpeg version from the repositories (that's version "3:0.cvs20070307-5ubuntu7.3+medibuntu1", apparently).

And the video is [http://www.youtube.com/watch?v=sxNmeMklFk8](http://www.youtube.com/watch?v=sxNmeMklFk8) , downloaded using the DownloadHelper Firefox addon.

---

### Post by FakeOutdoorsman on 2009-05-08
Johnathan Coultan is great.  I once saw him play for a small venue without knowing who he was.  This looks like a flv container with h264 video and aac audio.  That's usually bad form, but I didn't know YouTube is providing these type of files.  I can confirm that Medibuntu's FFmpeg doesn't work with this video; however it works fine with a recent self-compiled FFmpeg, and I would assume it would work with Jaunty Jackalope's repository FFmpeg:
```
ffmpeg -i /tmp/FlashTAx7jp -acodec libmp3lame output.mp3
```
or
```
ffmpeg -i /tmp/FlashTAx7jp -acodec copy output.aac
```
Maybe someone can come up with an alternate solution, but it will work if you use a recent FFmpeg:

[HOWTO: Install and use the latest FFmpeg and x264](http://ubuntuforums.org/showthread.php?t=786095)

---

### Post by PTSnoop on 2009-05-08
No luck with either of the two codes, either as written or with the input changed from /tmp/FlashTAx7jp to the actual name of the file on my hard disk.

I've got up to step 4: Install FFmpeg on the howto, and I get 
```
svn: Can't connect to host 'svn.ffmpeg.org': Connection timed out
```. When I try to download from the Nightly Snapshots, I get a 404. Maybe it's just server problems: I'll try again tomorrow.

EDIT: I've found the right file; it's installed and seems to be ok. But it's almost 4 in the morning, so I think I'll get some sleep before I find out whether it'll convert properly.

EDIT2: Or maybe I won't. Yay, it's worked fine! Thanks, FakeOutdoorsman!

---

### Post by jeterfan1 on 2010-06-06
THANKS!!!! wonderful!

---

### Post by anarki13 on 2010-07-09
> **FakeOutdoorsman said:**
> FFmpeg from the repository is not compiled to support restricted formats such as mp3.  You can use a third-party repository such as Medibuntu, compile ffmpeg yourself, or use another program such as mencoder.

The basic command:
```
ffmpeg -i inpuvvideofile.flv outputaudiofile.mp3
```
By default this will create a 64 kb/s file.  You can declare the audio bitrate with -ab:
```
ffmpeg -i inpuvvideofile.flv -ab 128k outputaudiofile.mp3
```
If the flv already has mp3 audio, then there is no need to re-encode.  You can just copy the audio stream.  This will preserve the audio quality and will be much quicker since there is no re-encoding:
```
ffmpeg -i inpuvvideofile.flv -acodec copy outputaudiofile.mp3
```
Don't know what the audio is?  Just ask ffmpeg:
```
ffmpeg -i inputvideo.flv
```
Along with some other information, ffmpeg will provide file details with the above command:
```
Stream #0.0: Video: flv, yuv420p, 320x240, 29.97 tb(r)
Stream #0.1: Audio: mp3, 22050 Hz, mono, s16, 56 kb/s
```

Thanks a million boss, problem solved!

---

### Post by Rolandmaffia on 2011-01-30
> **paulmerchant said:**
> Avidemux.

With many FLV files, you can rip the audio stream quickly and easily. Just File | Open the FLV and then Audio | Save... the MP3. Just make sure your Audio setting is set to copy unless you have to convert it from another type of stream.
great, I've been looking for this information! thanks!

---

### Post by karpay on 2011-02-21
Hi!

I tried what you have wrote in this thread however, I did not seem to work for me.

I write down the code below:

```

ffmpeg -i os3Qg05R05g.flv

```

Then the resuling info appeared on the screen:

```

[flv @ 0x90e0420]Estimating duration from bitrate, this may be inaccurate
Input #0, flv, from 'os3Qg05R05g.flv':
  Metadata:
    duration        : 265
    starttime       : 0
    totalduration   : 265
    width           : 320
    height          : 240
    videodatarate   : 39
    audiodatarate   : 105
    totaldatarate   : 152
    framerate       : 25
    bytelength      : 5058701
    canseekontime   : true
    sourcedata      : BADC20524HH1298272218387507
    purl            : 
    pmsg            : 
  Duration: 00:04:25.31, start: 0.000000, bitrate: 147 kb/s
    Stream #0.0: Video: h264, yuv420p, 320x240 [PAR 1:1 DAR 4:3], 39 kb/s, 25 tbr, 1k tbn, 50 tbc
    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16, 107 kb/s
At least one output file must be specified

```

And when I type the command below:

```

ffmpeg -i os3Qg05R05g.flv -acodec copy out.mp3

```

what appears on the screen is written below:

```

[flv @ 0x8360420]Estimating duration from bitrate, this may be inaccurate
Input #0, flv, from 'os3Qg05R05g.flv':
  Metadata:
    duration        : 265
    starttime       : 0
    totalduration   : 265
    width           : 320
    height          : 240
    videodatarate   : 39
    audiodatarate   : 105
    totaldatarate   : 152
    framerate       : 25
    bytelength      : 5058701
    canseekontime   : true
    sourcedata      : BADC20524HH1298272218387507
    purl            : 
    pmsg            : 
  Duration: 00:04:25.31, start: 0.000000, bitrate: 147 kb/s
    Stream #0.0: Video: h264, yuv420p, 320x240 [PAR 1:1 DAR 4:3], 39 kb/s, 25 tbr, 1k tbn, 50 tbc
w    Stream #0.1: Audio: aac, 44100 Hz, stereo, s16, 107 kb/s
File 'out.mp3' already exists. Overwrite ? [y/N] y
Output #0, mp3, to 'out.mp3':
  Metadata:
    TSSE            : Lavf52.64.2
    Stream #0.0: Audio: aac, 44100 Hz, stereo, 107 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
Press [q] to stop encoding
size=    3392kB time=265.89 bitrate= 104.5kbits/s    
video:0kB audio:3391kB global headers:0kB muxing overhead 0.000950%

```

What does this supposed to mean?

It is not converting my .flv file into an .mp3 file.

Any kind of help is kindly appreciated.

Regards.

---

### Post by FakeOutdoorsman on 2011-02-21
Your input file contains AAC audio. You can either copy this into a container format that will work with AAC:
```
ffmpeg -i os3Qg05R05g.flv -acodec copy -vn out.mp4
```
...or re-encode it to MP3:
```
ffmpeg -i os3Qg05R05g.flv -acodec libmp3lame -aq 4 out.mp3
```
You may need to enable the MP3 encoder in your FFmpeg. See:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by karpay on 2011-02-22
Thank you Fake Outdoorsman. It worked :)

---

### Post by wh1zz0 on 2011-11-12
If you're like some who don't like the command line you can download WinFF which is the GUI version.

---

### Post by oldos2er on 2011-11-12
Closed, please don't bump old threads.

---

