---
title: "How do you use the command line to join video files"
date: 2016-06-24
forum: General Help
---

### Post by jacatone on 2016-06-24
If I use Avidemux to split a video file into edited segments how would I use the command line to join those segments into one file again?

---

### Post by timgood on 2016-06-24
A few multimedia containers (MPEG-1, MPEG-2 PS, DV) allow to join video files by merely concatenating them. But not all formats support this. If they are supported you can simply:

```
cat test test1 test2 > test3
```

Google is your friend on this.

---

### Post by jacatone on 2016-06-27
This what I got:

cat: test: No such file or directory

Does that mean I need to create a test file first?

---

### Post by nerdtron on 2016-06-27
> **jacatone said:**
> This what I got:

cat: test: No such file or directory

Does that mean I need to create a test file first?


Because the file "test" is not on existing. You should specify the folder and file name of the videos you want to try.
For example, you have video1.mp4 and video2.mp4 on your /home/username/Videos folder, then you can join them to make the "finalvideo.mp4":
```
cat /home/username/Videos/video1.mp4 /home/username/Videos/video2.mp4 > /home/username/Videos/finalvideo.mp4 
```

---

