---
title: "Converting only audio from a Video file"
date: 2017-03-01
forum: General Help
---

### Post by linuxyogi on 2017-03-01
Hi,

Source file filename.mkv

Video Codec: H264 - MPEG-4 AVC (part 10) (avc1)

Audio Codec: Opus Audio (Opus)

My TV has an USB port but it doesnt support Opus. AFAIK it supports only mp3 as audio.

Can someone help me ... I have tried Avidemux but it has no support for Opus.

---

### Post by Perfect Storm on 2017-03-01
Try:
```
ffmpeg -i input_file.mkv -f mp3 output_file.mp3
```

---

### Post by SeijiSensei on 2017-03-01
I was curious to see how that worked with multilingual Matroska files.  Turns out it will re-encode the first audio track it finds and quits. Otherwise it's a great solution, and one that avoids using mkvextract to get the audio file first.

---

### Post by linuxyogi on 2017-03-01
> **Artificial Intelligence said:**
> Try:
```
ffmpeg -i input_file.mkv -f mp3 output_file.mp3
```

I want the output file in h.264 format with mp3 as audio format. In other words I want to keep the video in its current format and change the audio track to mp3.

Thanks.

---

### Post by Perfect Storm on 2017-03-01
I don't know the command for that. But I'm sure you can archive it through a video-editing app like pitivi etc.

---

### Post by SeijiSensei on 2017-03-01
```
ffmpeg -i input.mkv -vcodec copy -acodec mp3 output.mkv
```
Worked for me; kept the subtitle track, too.

---

### Post by linuxyogi on 2017-03-01
> **SeijiSensei said:**
> ```
ffmpeg -i input.mkv -vcodec copy -acodec mp3 output.mkv
```
Worked for me; kept the subtitle track, too.

It worked. Thanks at lot.

---

