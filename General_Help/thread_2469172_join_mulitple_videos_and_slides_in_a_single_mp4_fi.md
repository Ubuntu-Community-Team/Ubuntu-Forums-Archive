---
title: "join mulitple videos and slides in a single mp4 file"
date: 2021-11-22
forum: General Help
---

### Post by atux on 2021-11-22
i have an ubuntu server 20.04 (no Gui) and i have a series of mp4 and powerpoint slides that i would like to join in a particular order. eg slide1, 1.mp4, slide2, 2.mp4, slideN, N.mp4
The slides are currently png files.
No re-encoding. simply join the file.
is there an easy way to join all these files in a single file from command line, please?

---

### Post by atux on 2021-11-22
i have seen the ffmpeg tool but i cannot find how i could join a sinlge png file and a mp4 file to a single mp4 output
input.png+input.mp4=output.mp4

---

### Post by ajgreeny on 2021-11-22
I'm pretty sure ffmpeg can do that though not totally certain about those PowerPoint slides.

With no GUI how will you check the output as it happens?

---

### Post by Holger_Gehrke on 2021-11-22
To be able to join files without reencoding using ffmpeg the files have to use the same codecs and be of the same dimensions and the same frame rate. So I'd first check the video files whether they are identical in that respect. If the videos have the same dimensions and framerate and use the same codecs for video and audio and the images have the same dimensions convert the images to video clips ('ffmpeg -loop 1 -framerate **the_framerate_of_the_videos** -t **length_of_the_video_to generate_from_the_image_in_seconds** -i **png_file** **outputfile.mp4**'). Replace the bold parts with values that fit your requirements. You might have to add some options there to set the right video codec. Once all the files are video files, you can follow the answer to this [stack overflow question]("https://stackoverflow.com/questions/49371422/how-to-merge-two-videos-without-re-encoding").

Holger

---

### Post by KBar on 2021-11-22
**cat** should do the trick:
```
cat slide* > slide_final 
```

---

### Post by dragonfly41 on 2021-11-22
Another thought is to embed in markdown files.

[https://stackoverflow.com/questions/46273751/how-to-add-local-video-file-in-markdown-md-file](https://stackoverflow.com/questions/46273751/how-to-add-local-video-file-in-markdown-md-file)

Use pandoc.

---

### Post by ActionParsnip on 2021-11-22
Possibly with imagemagic
```

convert -delay 1 image-*.jpg output.mp4

```
[https://askubuntu.com/questions/610903/how-can-i-create-a-video-file-from-a-set-of-jpg-images](https://askubuntu.com/questions/610903/how-can-i-create-a-video-file-from-a-set-of-jpg-images)

---

