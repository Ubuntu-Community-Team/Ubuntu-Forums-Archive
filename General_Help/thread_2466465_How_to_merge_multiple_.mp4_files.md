---
title: "How to merge multiple .mp4 files"
date: 2021-08-28
forum: General Help
---

### Post by satimis on 2021-08-28
Hi all,

Please advise how to merge/concatenate multiple .mp4 files running command lines.

I found following link;
How to merge multiple (more than two) videos on Ubuntu?
[https://newbedev.com/how-to-merge-multiple-more-than-two-videos-on-ubuntu](https://newbedev.com/how-to-merge-multiple-more-than-two-videos-on-ubuntu)

You can do it using ffmpeg:```

ffmpeg -i concat:"input1.mp4|input2.mp4" output.mp4

```

It didn't work for me, input2.mp4 not added.  Both .mp4 files are in the same folder.

Regards

---

### Post by dragonfly41 on 2021-08-28
Use [OpenShot GUI]("https://www.openshot.org/en/download/") ?

---

### Post by HermanAB on 2021-08-28
I can recommend kdenlive to edit and splice the files.  However, when all else fails, you can try using ordinary cat to concatenate the files.  This will result in a fault at the join, but usually, a video player will skip the errors and keep going.

---

### Post by satimis on 2021-08-28
> **dragonfly41 said:**
> Use [OpenShot GUI]("https://www.openshot.org/en/download/") ?
Hi,

Thanks for your advice.

In the past I usually did it in this way including editing the video.  I'm now looking for a command line solution.

Regards

---

### Post by philhughes on 2021-08-28
Try:

```
ffmpeg -i "concat:input1.mp4|input2.mp4" -c copy output.mp4
```

Note the position of the quotation marks.

Official documentation:

[https://trac.ffmpeg.org/wiki/Concatenate](https://trac.ffmpeg.org/wiki/Concatenate)

---

### Post by satimis on 2021-08-28
> **HermanAB said:**
> I can recommend kdenlive to edit and splice the files.  However, when all else fails, you can try using ordinary cat to concatenate the files.  This will result in a fault at the join, but usually, a video player will skip the errors and keep going.
Hi.

$ cat file1.mp4 file2.mp4 file3.mp4 > output.mp4

It didn't work.  I suppose it works on .txt files

Regards

---

### Post by dragonfly41 on 2021-08-28
Another link then ..

[https://ottverse.com/3-easy-ways-to-concatenate-mp4-files-using-ffmpeg/](https://ottverse.com/3-easy-ways-to-concatenate-mp4-files-using-ffmpeg/)

---

### Post by satimis on 2021-08-28
> **philhughes said:**
> Try:

```
ffmpeg -i "concat:input1.mp4|input2.mp4" -c copy output.mp4
```

Note the position of the quotation marks.


Still failed.  input2.mp4 not added

---

### Post by philhughes on 2021-08-28
The documentation does say it only works for certain streams, so may be mp4 is not one of them. You will have to try one of the other methods described.

---

### Post by TheFu on 2021-08-28
If the input files all have identical codec settings, then you can merge them using **mkvmerge**.  
```
$ mkvmerge -o output.mkv         file1.mp4 + file2.mp4 + file3.mp4 + file4.mp4
```
This will get all the video, audio, srts, ass, subs, and other information from the files and append them perfect.

If they **do not** have the same codec settings (or have different resolutions, track ordering, etc), the only answer is to transcode them each into a single output.  I'd do that with 

```
$ cat files*mp4 | ffmpeg -i -   {some settings}   output.mp4
```

---

### Post by satimis on 2021-08-29
> **TheFu said:**
> If the input files all have identical codec settings, then you can merge them using **mkvmerge**.  
```
$ mkvmerge -o output.mkv         file1.mp4 + file2.mp4 + file3.mp4 + file4.mp4
```
This will get all the video, audio, srts, ass, subs, and other information from the files and append them perfect.
- snip -

All .mp4 files have identical codec settings

Performed following steps;

1)
On Terminal
$ sudo apt-get update -y
$ sudo apt-get install -y mkvtoolnix
$ which mkvmerge```

/usr/bin/mkvmerge

```

2)
On same Terminal run;
$ mkvmerge -o output.mkv file_1.mp4 + file_2.mp4 + file_3.mp4```

mkvmerge v45.0.0 ('Heaven in Pennies') 64-bit
Error: The file 'file_1.mp4' could not be opened for reading: open file error.

```

Regards

---

### Post by dragonfly41 on 2021-08-29
There are some clues found here ..

[https://gitlab.com/mbunkus/mkvtoolnix/-/issues/2680](https://gitlab.com/mbunkus/mkvtoolnix/-/issues/2680)

and did you try the several options in link in post#7 ?

---

### Post by satimis on 2021-08-29
> **dragonfly41 said:**
>  - snip -
and did you try the several options in link in post#7 ?
post#7 is similar to```

Create a file files.txt with all the files you want to have concatenated in the following form (lines starting with a # are ignored):

```
of link;
[https://newbedev.com/how-to-merge-multiple-more-than-two-videos-on-ubuntu](https://newbedev.com/how-to-merge-multiple-more-than-two-videos-on-ubuntu)

I have tried that but fail.  All 3 .mp4 files are in the same folder.  On Terminal I ran ffmpeg command on the same folder.

---

### Post by satimis on 2021-08-29
Further to my previous posting

Following link can merge .mp4 files but the output .mp4 file without sound.

How to merge many mp4 videos with FFMPEG in a few seconds
[https://www.dandandin.net/how-to-merge-many-mp4-videos-with-ffmpeg-in-a-few-seconds/](https://www.dandandin.net/how-to-merge-many-mp4-videos-with-ffmpeg-in-a-few-seconds/)

On Terminal performed following steps:-
$ cd to the folder where .mp4 files stored

$ ls```

file_1.mp4 file_2.mp4 file_3.mp4

```

$ find *.mp4 | sed 's:\ :\ :g'| sed 's/^/file /' > list.txt

$ ffmpeg -safe 0 -f concat -i list.txt -c copy video-merge.mp4

$ ls```

list.txt video-merge.mp4 file_1.mp4 file_2.mp4 file_3.mp4

```

---

### Post by TheFu on 2021-08-29
> **satimis said:**
>  
 ```

mkvmerge v45.0.0 ('Heaven in Pennies') 64-bit
Error: The file 'file_1.mp4' could not be opened for reading: open file error.

``` 

file_1.mp4 is corrupt or has a permissions problem.

---

### Post by dragonfly41 on 2021-08-29
Perhaps, as a test, try concatenating several clones of a single "good" file.
Repeat test with clones of the suspect file.

---

### Post by satimis on 2021-08-29
> **dragonfly41 said:**
> Perhaps, as a test, try concatenating several clones of a single "good" file.
Repeat test with clones of the suspect file.
I found out the cause of problem without sound.  It is because file_1.mp4 without sound/audio, not corrupted.  I tested those 3 .mp4 files separately running VLC.  All of them work without problem.

So the command lines on #14```


$ find *.mp4 | sed 's:\ :\ :g'| sed 's/^/file /' > list.txt

$ ffmpeg -safe 0 -f concat -i list.txt -c copy video-merge.mp4

```
work in combination seamlessly.

Would it be possible including file_1.mp4 and retaining audio of other 2 .mp4 files?

Regards

---

### Post by TheFu on 2021-08-29
> **satimis said:**
>  Would it be possible including file_1.mp4 and retaining audio of other 2 .mp4 files?

As already said, either the codecs used are 100%, exactly, the same with all settings, resolutions, tracks matching
or
transcode all of them.

---

### Post by dragonfly41 on 2021-08-29
Another thread found ..

[https://stackoverflow.com/questions/46057412/ffmpeg-concat-multiple-videos-some-with-audio-some-without](https://stackoverflow.com/questions/46057412/ffmpeg-concat-multiple-videos-some-with-audio-some-without)

---

### Post by Tadaen_Sylvermane on 2021-08-29
The main issue is the mp4. Run them through Handbrake to get mkv's. Then it's easy as linux works with open formats easily. mkvtoolnix or mkvmerge will work just fine then. If you want to go back to mp4 then go for it.

---

### Post by satimis on 2021-08-29
I suppose it would be easier for me adding file_1.mp4 to the output.mp4 file running OpenShot.  I still need running OpenShot adding subtitles, narration, background music etc, to the output.mp4 file

Regards

---

### Post by TheFu on 2021-08-29
> **satimis said:**
> I suppose it would be easier for me adding file_1.mp4 to the output.mp4 file running OpenShot.  I still need running OpenShot adding subtitles, narration, background music etc, to the output.mp4 file

Regards

Openshot **always** transcodes everything, so there isn't any more loss to be added. Just use that tool with the different clips.

---

### Post by HermanAB on 2021-08-30
Regarding simple use of cat: I have done exactly that many times.  It also depends on the quality of your player and its ability to handle errors though.

---

