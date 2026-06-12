---
title: "Using avconv"
date: 2017-05-01
forum: General Help
---

### Post by anon_private on 2017-05-01
I am trying to convert an mp4 file to flv.

I would just like a straight conversion.

I typed avconv -i file.mp4 file.flv

The conversion occurred but the video is blocky.

I have looked at info avconv, in terminal, but can't see the best method.

Advice please.

---

### Post by Autodave on 2017-05-01
In the past, I have used *handbrake *for doing that. You may want to d-l that and take a look.

---

### Post by mc4man on 2017-05-01
You might want to post some info on source mp4's (video size, audio & video codecs, ect.) & what is it you're trying to accomplish.
The flv encoder is probably pretty crappy in general & by default does about 200k bitrate for video which may be ok if your vids are holiday postage stamp size..

---

### Post by sonicwind on 2017-05-01
The command I've been using for this, using your example, is:

avconv -i file.mp4 -codec copy file.flv

This does a straight format change without re-encoding (lossless).

I've had great success with this for repairing videos that won't play by changing them to another format.

Hope this helps.

---

### Post by anon_private on 2017-05-02
> **sonicwind said:**
> The command I've been using for this, using your example, is:

avconv -i file.mp4 -codec copy file.flv

This does a straight format change without re-encoding (lossless).

I've had great success with this for repairing videos that won't play by changing them to another format.

Hope this helps.

I have a large mp4 file that I would like to reduce in size as much as possible, but without too much loss of quality. An suggestions welcome.

Where did you find the avconv examples?

Thanks

---

### Post by anon_private on 2017-05-02
> **Autodave said:**
> In the past, I have used *handbrake *for doing that. You may want to d-l that and take a look.


I have downloaded Handbrake from the kubuntu muon repository.

It looks like I can only recode to mkv. I don't know much about this format. Is it much smaller than mp4? I was surprised not to see a variety of formats.

---

### Post by #&amp;thj^% on 2017-05-02
I remember getting a lecture from an older user here around 2008 anyway... Both mp4 and mkv are "container" formats. This means that they can include video/audio/subtitle streams of different types,
Just some more clarity:
so if a 7GB file is a Bluray rip, chances are it will have the original HD DTS audio, which can be up to a third of the file size. If the MP4 version has two channel AAC then the difference can be substantial. Video bitrate is the other large factor. While it is a fair supposition to make regarding the larger file probably having higher quality, there are a number of factors that come into play when encoding that could mean the difference is not as large as you might think (the type of content being encoded), or factors with playback that mean the difference in quality is not as apparent (lower quality TV or upscaler etc.). So the actual difference will vary from file to file, and the difference it makes to the end viewer will be very subjective. 

MKV supports a lot of different formats (including AC3 aka Dolby Digitall and VobSub DVD subtitles). Correct me if I'm wrong, but to my knowledge you can't put 5.1 AC3 into MP4 without transcoding to AAC or some other "mp4 codec" first
afaik ac3 is the main reason, and i think there is still no 'standard' way to store ac3 in mp4.

---

### Post by sonicwind on 2017-05-02
> **anon_private said:**
> Where did you find the avconv examples?


I'm no expert. I just learned by Googling. I believe I found the example I used above on this forum. I just needed something to change an M2TS file to MP4.

Try these:

[http://www.tecmint.com/avconv-command-examples/](http://www.tecmint.com/avconv-command-examples/)

[http://roxlu.com/2013/002/converting-video-audio-using-avconv](http://roxlu.com/2013/002/converting-video-audio-using-avconv) (large number of examples)

---

### Post by leunam12 on 2017-05-02
Try winff

---

### Post by anon_private on 2017-05-03
> **Autodave said:**
> In the past, I have used *handbrake *for doing that. You may want to d-l that and take a look.

Did you get your version of Handbrake for the Handbrake website?

Did you notice major differences between the two versions?

---

### Post by anon_private on 2017-05-03
Why do some people have such a low opinion of the flv format?

---

### Post by Yellow Pasque on 2017-05-03
It would help if you ran mediainfo on one of the files so we can see what audio and video codecs you use. *.mp4 files can contain different formats, much like mkv.

> I have a large mp4 file that I would like to reduce in size as much as possible

So why are you trying to put it in an flv container?

---

