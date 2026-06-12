---
title: "batch convert flv to mp4"
date: 2019-03-05
forum: General Help
---

### Post by atux on 2019-03-05
Hi. I have load of flv files that i would like to convert them to mp4 files.
At the moment i managed to convert a single file with the following command
```
ffmpeg -i input.flv -vcodec copy -acodec copy output.mp4
```
So far so good.

The problem is when i am trying to script the process to convert all files in the folder and delete the already converted flv.
here is my job.
```
#!/bin/bash
ls -f /home/whatever/files/*.flv | while read -r file;
do
#-- get just the file name --#
name="${file%.*}"
ffmpeg -i $name.flv -vcodec copy -acodec copy $name.mp4
done

```

two issues:
[LIST]
[*]it takes only the folder specified, but i would like it to take all the files in current folder
[*]it executes ffmpeg, but it does not convert anything. it pops the following error ```
/home/whatever/files/.: No such file or directory

```
[/LIST]
ANy ideas on how to fix that please?

---

### Post by atux on 2019-03-05
i 've taken another approach ```
#!/bin/bash
for f in *.flv; do ffmpeg -i "$f" "${f%.flv}.mp4" -vcodec copy -acodec mpeg4; done
```
It successfully creates an mp4 file, but the audio is not synced to  video and the video is choppy.

---

### Post by ajgreeny on 2019-03-05
Why the change from **-acodec copy** which apparently worked to **-acodec mpeg4** which is now giving you the sync problem?

---

### Post by atux on 2019-03-06
Hi. The command ```
[COLOR=#E45649][FONT=inherit]ffmpeg[/FONT][/COLOR][COLOR=#383A42] [/COLOR][COLOR=#E45649][FONT=inherit]-i[/FONT][/COLOR][COLOR=#383A42] [/COLOR][COLOR=#E45649][FONT=inherit]input[/FONT][/COLOR][COLOR=#986801][FONT=inherit].flv[/FONT][/COLOR][COLOR=#383A42] [/COLOR][COLOR=#E45649][FONT=inherit]-vcodec[/FONT][/COLOR][COLOR=#383A42] [/COLOR][COLOR=#E45649][FONT=inherit]copy[/FONT][/COLOR][COLOR=#383A42] [/COLOR][COLOR=#E45649][FONT=inherit]-acodec[/FONT][/COLOR][COLOR=#383A42] [/COLOR][COLOR=#E45649][FONT=inherit]copy[/FONT][/COLOR][COLOR=#383A42] [/COLOR][COLOR=#E45649][FONT=inherit]output[/FONT][/COLOR][COLOR=#986801][FONT=inherit].mp4
[/FONT][/COLOR]
``` it works finaly.
How can i make it a nice script to convert all the flv files in a folder.

---

### Post by ajgreeny on 2019-03-07
I do not have any .flv files to check on but the following script I use to change all **video.ts** transport streams (from a PVR) certainly works to change them all to mp4 format which I need to get them streamable via Plexmediaserver.

Run it from the folder containing all the .flv files you want to change, of course, not from your home folder.
```
#!/bin/sh

toname="./mp4/#"$1"/"$( echo $file | cut -f1 -d.)"_"$1".mp4"
for f in *.*; do ffmpeg -i "$f" -acodec copy -vcodec copy "${f%.*}.mp4"; done
done
```
See if that works for you to change your .flv videos, though you may need to edit it to get it to work as you want.

---

### Post by ajgreeny on 2019-03-10
I have just found several .flv files on another machine I use very little but also with Lubuntu 18.04 as OS and the script I show in post #5 certainly worked for that folder.

Give it a try and if all is well, please mark as SOLVED from the Thread Tools menu up-top. It is a great help to users searching the forum.

---

