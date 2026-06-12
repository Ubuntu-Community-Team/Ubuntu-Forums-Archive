---
title: "How can I join two webm videos whilst keeping the same quality?"
date: 2015-08-04
forum: General Help
---

### Post by Rytron on 2015-08-04
Hi.

How can I join two webm videos whilst keeping the same quality?

Thanks.

---

### Post by TheFu on 2015-08-04
1 solution - 
* Put both into mkv files using mkvmerge.
* Then use mkvmerge to append one into the other.
```

mkvmerge -o file1.mkv file1.webm
mkvmerge -o file2.mkv file2.webm
mkvmerge -o joined_file1_2.mkv file1.mkv file2.mkv
```

These commands take the amount of time a file copy takes. No transcoding needed.  There are some requirements. Both files mush have the same codec settings for video and audio.

mkvmerge will retain any text files, subtitles, captioning, etc.... in the original files too. It is an amazing tool. Oh - and there is a GUI too - sorry, I don't know the name of that program.

Option 2 - get a version of ffmpeg or avconv that has webm support compiled in. Probably best to use the PPA for this - compiling these programs yourself can be ugly.  There is a PPA that installs fairly recent versions into /opt/

---

### Post by Vladlenin5000 on 2015-08-04
> **TheFu said:**
> Oh - and there is a GUI too - sorry, I don't know the name of that program.

The GUI is MKVMerge GUI (who would have thought?) :lolflag:
Available at the Ubuntu repositories (version 7.3.0-1 in Ubuntu 15.04). Just search MKV in the Ubuntu Software Center.

---

### Post by TheFu on 2015-08-04
> **Vladlenin5000 said:**
> The GUI is MKVMerge GUI (who would have thought?) :lolflag:
Available at the Ubuntu repositories (version 7.3.0-1 in Ubuntu 15.04). Just search MKV in the Ubuntu Software Center.

Probably helpful for 85% of the users. Thanks.

However, for accuracy, that is NOT the actual name of the program - it is mmg ([https://www.bunkus.org/videotools/mkvtoolnix/doc/mkvmerge-gui.html](https://www.bunkus.org/videotools/mkvtoolnix/doc/mkvmerge-gui.html)). mmg is what you'd run from the shell, without a menu.  Those words are the "title" and if you don't use "software center" or synaptic it is of ZERO use. For example, if you have a headless server, it is possible you don't want any GUI tools loaded on it.

The real package name is mkvtoolnix-gui - that is what you'd use with aptitude or apt-get.
For the shell versions, the package is mkvtoolnix. ;)

---

### Post by nerdtron on 2015-08-05
So you just want to join the two video files? I haven't tried it but I think "cat" command can do this. [http://unix.stackexchange.com/questions/116035/interactively-concatenate-video-files](http://unix.stackexchange.com/questions/116035/interactively-concatenate-video-files)

---

### Post by TheFu on 2015-08-05
> **nerdtron said:**
> So you just want to join the two video files? I haven't tried it but I think "cat" command can do this. [http://unix.stackexchange.com/questions/116035/interactively-concatenate-video-files](http://unix.stackexchange.com/questions/116035/interactively-concatenate-video-files)

Concatenation should work only for simple stream files that don't have complex headers. I wouldn't expect it to work for webm - but it doesn't hurt to try.

---

### Post by HermanAB on 2015-08-05
Just to give an example for others who google this thread.

Using ffmpeg with two mpeg4 snips of different sizes, merging works like this:

ffmpeg -i snippet1.mp4 -i snippet2.mp4 -filter_complex \
"[0:v]setpts=PTS-STARTPTS, pad=iw*1.2:ih[bg]; \
[1:v]setpts=PTS-STARTPTS[fg]; [bg][fg]overlay=w" merged.mp4

For videos with the same aspect ratio, you just leave the padding command out.

---

### Post by Rytron on 2015-08-06
Thanks guys. The mkvmerge GUI worked fine.  ):P

---

