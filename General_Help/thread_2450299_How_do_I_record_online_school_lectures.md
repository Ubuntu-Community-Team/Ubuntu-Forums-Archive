---
title: "How do I record online school lectures?"
date: 2020-09-10
forum: General Help
---

### Post by Old Jimma on 2020-09-10
Brothers and Sisters of Ubuntu:

At a ripe old age, I've gone back to school.... to find that all of the lectures are prerecorded online lectures.

I want to listen to them at my leisure, pausing them, and repeating things I don't understand.

So, I want to make a video/audio recording of the lecture and use VLC to watch it and review it. 

Lectures are anywhere form 30 to 60 minutes in length.

Can somebody please steer me into Ubuntu open source software that will record the audio/video of the lecture broadcast to my computer monitor?

Ideally, I'd like to be able to start the recording a moment before I start the online lecture, and program the software to stop recording after "X" minutes, the published number of minutes that the video runs.

Ubuntu "Audio recorder"  does this for recording audio. I am hoping software that is similarly SIMPLE and easy to use that records an broadcasted audio/video stream.

Thank you!

Old Jimma from the old Country

---

### Post by CelticWarrior on 2020-09-10
It depends. Unfortunately some may not be intended for download.
For those that can be dowoaded it should be as simple as right-click > Save video as...

---

### Post by Old Jimma on 2020-09-10
Hi Celtic Warior,

The lectures and web site were created in a short period of time, by people who are not web experts. They are teachers. There isn't any way to right click and download. 

THis is the reason why I need to record them.

Thanks for your reply.

Old JImma

---

### Post by CelticWarrior on 2020-09-10
What do show up when you right-click the video? Usually at the bottom of the list it shows the software used.

---

### Post by Old Jimma on 2020-09-10
Hi Celtic Warrior:

The list includes:
Open in new window
...
Save link as
..
inspect
...

Celtic... there is no indication of softare used, or ho to download a file. I've checked this thoroughly.

That is the reason I'm requesting for help to use open source softare  to record the stream while I play it.. I need it for my on personal study in the class and no other purpose.

Can you recommend softare to record audio/video that is broadcast on a computer monitor?

Thank you!
Old Jimma

---

### Post by HermanAB on 2020-09-11
Howdy,

With ffmpeg, it is a one liner to record the desktop:
[https://trac.ffmpeg.org/wiki/Capture/Desktop](https://trac.ffmpeg.org/wiki/Capture/Desktop)

Just make a little script of it.

There is also program called *istanbul*:
[https://wiki.gnome.org/Projects/Istanbul](https://wiki.gnome.org/Projects/Istanbul)

---

### Post by dragonfly41 on 2020-09-11
I have just installed this from scratch (via command: **sudo install simplecreenrecorder**)
[simplescreenrecorder]("https://www.maartenbaert.be/simplescreenrecorder/")

and it seems to work fine .. mkv recording saved in $HOME/Videos/

---

### Post by Old Jimma on 2020-09-11
Hi Dragonfly,

Thanks for your suggestion!!! I tried it and it works.

I found small design problem with **simplesreenrecorder**: the 3rd page has a problem... specifically once you record the the lesson, you must save it.. DO NOT HIT PAUSE that deletes what you saved.  Could be wrong about that ,  but I spent a hour not understanding that

I'm going to try **vokosreen**, and will report on it here.

Old Jimma

---

### Post by Autodave on 2020-09-11
One other possibility that might work: there is an addon for Firefox called "Ant"/  That may or may not record the video.  Won't cost you anything to try it but a couple minutes of time.

---

### Post by sdsurfer on 2020-09-11
Screen cap is a bit of a workaround because you're recording something already recorded. If content is being deployed to your browser, it is in the code. You will have to dig in a little, but if you do it once the rest are easy. Unless it is in Flash, which is unlikely these days.

> 
The list includes:
Open in new window
...
Save link as
..
inspect
...


If you right-click the video element, select ***inspect*** here. This will open the developer's panel and show the page code with the element you clicked highlighted. Look in the toolbar for the options that allow you to open this as a floating "page" instead of being docked and cramped all in one window. Move around in the inspector page and see how it highlights areas in the actual page.

Most often the video play area/canvas is wrapped by page elements. Keep opening up the page element sections designated by the open-arrow triangle. Eventually you will see a URL with a path that ends in, most likely, .mpg or mp4 or something like that. Click this path and it will highlight, right-click and select copy, then paste it in a new browser tab. One of two things will happen: it will display in the browser or you will be prompted to download. 

This method has never failed on sites that don't build in a download or intentionally break the save as function.

---

### Post by Old Jimma on 2020-09-11
Hi SDSurfer:

Thank you for your suggestion.

I studied the inspect element material yyou suggested, opening every line with a triangle to look for the file/link type you instructed.

THere was not one there. 

You wrote:

> This method has never failed on sites that don't build in a download or intentionally break the save as function. 

SDsurfer, I know this page pretty well. There is not a way to download the file. I must recored it. Recording it is the only option

SDsurfer, can you suggest opensource software from the Ubuntu repos that will allow me to record the lecture as it is broadcast on my computer monitor?

[B]I tried simplescreenrecorder: nice video, no audio.
[/B]
Thank you,
Old JImma

---

### Post by SeijiSensei on 2020-09-11
Can you post a URL so we can see what we're dealing with?

---

### Post by Old Jimma on 2020-09-12
The app **simplescreenrecorder** available on the Ubuntu repositories does this well.... just by using all of the default settings.

As of this writing version 0.4.2 is not available on the Ubuntu repositories, but has additional features that students who need to record online lessons will want, specifically, to stop recording after a specified number of minutes.

That version is available at [https://www.videohelp.com/software/SimpleScreenRecorder]("https://www.videohelp.com/software/SimpleScreenRecorder").

Also, youtube videos about **simplescreenrecorder** are available at [https://www.youtube.com/results?search_query=SimpleScreenRecorder&page=&utm_source=opensearch]("https://www.youtube.com/results?search_query=SimpleScreenRecorder&page=&utm_source=opensearch")

There are other apps out there. **simplescreenrecorder** works well for me.

Old Jimma

---

### Post by TheFu on 2020-09-12
I use SSR, SimpleScreenRecorder, sometimes.
You can also buy a hardware recording device for about $70. This is better for games which need to fully use the GPU and CPU during play. [https://www.amazon.com/Capture-Recorder-Compatible-Nintendo-Support/dp/B00VM4J4Y6/](https://www.amazon.com/Capture-Recorder-Compatible-Nintendo-Support/dp/B00VM4J4Y6/) is one.

A few weeks ago, I virtually attended DebConf by scheduling which URL to download for how long.  The script is:
```
#!/bin/bash

# No error checking performed
DUR="$1"  # in minutes
TITLE="$2" # for the filename
DATE=`date "+%F-%H%M%S"`
TIMEOUT=/usr/bin/timeout

if [ "X$DUR" = "X" ] ; then
 echo "$0 duration(min) Prog_Name
E.g.: $0  60 Lecture-101"
 exit 1;
fi

# Do something with TITLE?
if [ "X$TITLE" == "X" ] ; then
   TITLE="DebConf"
fi

# download a URL for DUR minutes.  The timeout command kills the youtube-dl.
#    wget or any other working download tool can be used.
$TIMEOUT ${DUR}m youtube-dl   rtmp://sfo1.live.debconf.org/front/main_high

# Rename to the desired name
mv main_high* "$2-debconf-2020.flv"
```
The flaw is that the rtmp URL is static, so changing it for different classes is left as an exercise for the reader.  My TV recording script works almost the same way with HD-Homerun network tuners.

The starting of the script at a specific time, use 'at'
Placement of the output file is controlled by the CWD. That can be controlled through output settings for the downloader or the 'mv' at the end.

---

### Post by dragonfly41 on 2020-09-12
Be aware that when "mining" online content such as lectures there is the option of reconstructing the content as an HTML5 slidedeck using Reveal,js.
Pandoc can create this quite easily.
Markdown is used to prepare the content and each page can (if required) have segments of video clips and audio clips embedded.
Simplescreenrecorder can still create the page by page clips
The advantage is that a presentation can be stepped through at leisure.
[Some examples here]("https://github.com/hakimel/reveal.js/wiki/Example-Presentations").  The creator of Reveal.js created slides.com

---

### Post by Old Jimma on 2020-09-13
Dear Dragonfly,

Thank you for your interesting reply. 

I must apologize and confess: I don't understand what you wrote. I apologize. Not trying to antagonize you. I just don't know alot.

Never the less, thank you for your reply.

Sincerely,
Old Jimma from the Old Country

---

### Post by dragonfly41 on 2020-09-13
> I must apologize and confess: I don't understand what you wrote.

That brings me down to earth with a bump. I will try to create an example. Might take some time though.

It would help if you could cite just one subject matter you are learning online.

---

### Post by Old Jimma on 2020-09-13
Hi Dragonfly,

I know how to use apps, and have been grateful for the forms since 2005 for help I've gotten to get them to work on Ubuntu. I am not schooled in computer science. Your remark only landed on ignorant ears, not unenthusiastic or interested ears.

So, I appologize. It is my fault, not your. I don't know enough about things to understand what you were driving at.

Old Jimma

---

### Post by Old Jimma on 2020-09-13
Dragonfly asked me to say what I'm learning in school: I'm learning music. My focus is jazz. Currently, I'm studying music theory, ear training, and guitar. I've been required to attend concerts... but in these COVID times, they've specified online concerts that are acceptable. I've used **audio recorder** to record those concert that are online and listen to them with **VLC**.

In all of these activities, I've used Ubuntu open source apps that include: **Musecore**, **Lillypond** and **Rosegarden**, **Tux Guitar**, **Audacity**, **VLC**, **simplestreamrecorder**, **audio recorder**, **Cheese**, **Libre Office**, **ffmpeg**, and probably a few other apps that I don't remember now.

I'm required to make videos of myself singing solfege over 3 or 4 classical music segments each week. I use **Muscore** to notate the music, and **Cheeze** to sing each piece. Then I use ffmpeg to stitch the video segments together. 

[B]I get help all the time from the Ubuntu Forums on how to use these apps.
[/B]
Music students pay big $$ to buy the proprietary versions of each of these apps. Because of Ubuntu, opensource software, and the Ubuntu forums, I ve been able to do well without the proprietary software.

I don't recommend music school unless you are already employed well. There are many, many unemployed or severely underemployed musicians (some walk dogs for a living). Better to be payed as a computer guy as the thinking, logic, and creativity is quite similar, but the $ **MUCH** better.

Old Jimma from the Old Country

---

### Post by Old Jimma on 2020-09-13
HI SeijSensi,

The URLS are accessible only with access to university school of music web site for students who are enrolled in coursework and making progress in a degree program. If you are enrolled in course work, you can get access the the online instructional  materials (including URLS) using your student ID and a password. If one doesn't have a student ID or password, access is not possible.

SeijSensi, sorry about this reply. However, please accept my sincere thanks for all of the advice you've given me in the  past.

Old Jimma

---

### Post by dragonfly41 on 2020-09-13
Post #19 I can relate to. In another forum I talked through a user to write Lilypond music notation in Markdown.
This is the same "Markdown" I refer to in post #15.
Basically one starts by installing an editor such as [Atom]("http://atom.io").
An excellent package markdown-preview-enhanced does the magic of converting Lilypond music notation (or just markdown text)
into different formats such as HTML, PDF .. and as I tried to explain Reveal.js slides using [Pandoc]("https://pandoc.org/MANUAL.html").
A companion package to explore for publishing such music notation is Scribus (in the Ubuntu repo). I advise trying the daily build scribus-ng.

---

### Post by Old Jimma on 2020-09-13
Hi Dragonfly,

I am so busy this semeter. Hope I can get to your suggestion after the semester.

Old Jimma.

---

### Post by mastablasta on 2020-09-14
if videos use flash or html 5 and if they are saved on website, they might be able to be downloaded using download helper plugin in in firefox. you just select the plugin icon and then download the video.

or are videos streaming live? if so, it might be good if school offered a version that can be watched outside of regular hours.

---

### Post by NM5TF on 2020-09-14
> **Old Jimma said:**
> Hi SDSurfer:

Thank you for your suggestion.

I studied the inspect element material yyou suggested, opening every line with a triangle to look for the file/link type you instructed.

THere was not one there. 

You wrote:



SDsurfer, I know this page pretty well. There is not a way to download the file. I must recored it. Recording it is the only option

SDsurfer, can you suggest opensource software from the Ubuntu repos that will allow me to record the lecture as it is broadcast on my computer monitor?

[B]I tried simplescreenrecorder: nice video, [COLOR="#FF0000"]no audio.[/COLOR]
[/B]
Thank you,
Old JImma

you have to enable audio recording in the drop down menu....have used this app for several years now...it is a resource hog, but works quite well

---

### Post by hk42 on 2020-09-14
There are two very nice extensions to Firefox:
"Adblocker for you tube" and " Video download helper"
Worth a try IMHO.
Also VLC can record while displaying but it no more works for some streams.

---

