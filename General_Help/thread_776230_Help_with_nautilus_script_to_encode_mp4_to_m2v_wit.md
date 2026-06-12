---
title: "Help with nautilus script to encode mp4 to m2v with ffmpeg"
date: 2008-04-30
forum: General Help
---

### Post by papafreebird on 2008-04-30
Hello, 
I'm needing help with scripting a nautilus zenity script.  I am trying to create a nautilus script for use in encoding mp4 files to mpeg2 elementary video (m2v).  I can do a basic script in terminal and it works fine
```

for i in *.mp4 ; do

ffmpeg -i "$i" -pass 1 -passlogfile "$i.log" -b 1800k -minrate 0 -maxrate 8500k -bufsize 8224k -vcodec mpeg2video -s 352x480 -r 25.00 -aspect 4:3 -an "foo.m2v" && \
rm foo.m2v  && \
ffmpeg -i "$i" -pass 2 -passlogfile "$i.log" -b 1800k -minrate 0 -maxrate 8500k -bufsize 8224k -vcodec mpeg2video -s 352x480 -r 25.00 -aspect 4:3 -an "p2_$i.m2v" 
done

```

However my nautilus script with basically the same format just isn't working.  The popups allowing me to select my output directory, bitrates, and fps are working fine but then nothing happens.  
```

#! /bin/bash

 location=$(zenity --file-selection --directory --title="Select Output Directory")
 	
      	
	 
	 BITRATE=$(zenity --title="Video AVG Bitrate" --entry)
	 
	MAXBITRATE=$(zenity --title="Max Video Bitrate" --entry)

	 FPS=$(zenity --title="Frame Rate" --entry)

for i in *.mp4 
do 
xterm -bg white -fg black +hold -T "Converting" -e ffmpeg -i "$i" -pass 1 -passlogfile "$i.log" -b $BITRATE -minrate 0 -maxrate $MAXBITRATE -bufsize 4224k -vcodec mpeg2video -s 352x480 -r $FPS -aspect 4:3 -an "$ifoo.m2V" 
rm foo.m2V
for i in *.mp4
do
xterm -bg white -fg black +hold -T "Converting" -e ffmpeg -i "$i" -pass 2 -passlogfile "$i.log" -b $BITRATE -minrate 0 -maxrate $MAXBITRATE -bufsize 4224k -vcodec mpeg2video -s 352x480 -r $FPS -aspect 4:3 -an "$location/p2_$i.m2V"

done

```
When prompted to enter the bitrates for ffmpeg I do enter the k after the number ie 1800k so as to keep the proper syntax.

What am I doing wrong?

---

