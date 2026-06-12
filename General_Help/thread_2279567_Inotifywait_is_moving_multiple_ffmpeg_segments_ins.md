---
title: "Inotifywait is moving multiple ffmpeg segments instead of one at a time."
date: 2015-05-24
forum: General Help
---

### Post by timsdeepsky on 2015-05-24
Hello,,
I have come to a dead end looking for a solution on my own and will ask for your help please.... 
Thanks for all info you may have....
I capture 30 second segments of video and write to a folder in sequence with this ffmpeg code....(this works perfectly)
```
ffmpeg -f video4linux2 -input_format yuyv422 -i /dev/video0 -vf "drawtext=fontfile=/usr/share/fonts/truetype/ubuntu-font-family/Ubuntu-R.ttf:text='TIM_CLINE_METEOR_CAM_%{localtime\:%F_%T}': r=30/1: x=(w-tw)/2: y=h-(1*lh): fontcolor=white: fontsize=16: box=1: boxcolor=0x00000999,format=yuv420p" -map 0 -c:v libx264 -preset veryfast -crf 22 -c:a libfdk_aac -vbr 3 -threads 4 -g 300 -f segment -segment_time 30 -reset_timestamps 1 /home/tim/uhvo_replacement_test_2/meteors_%06d.mp4
```
Then i have "inotifywait" running in terminal to move files to a different folder after they are written....
```
while inotifywait -e close_write /home/tim/uhvo_replacement_test_2; do mv /home/tim/uhvo_replacement_test_2/*.mp4 /home/tim/uhvo_replacement_test_2/moved_file; done
```
This does in fact work,,except it moves 2 .mp4 segments at the same time instead of one....And the second segment will even finish writing itself after being moved with the first segment to the new folder(odd)....I need it to move only one segment at a time because farther down the line i run other processes on these segments....
I believe the ```
inotifywait -e close_write
```option is supposed to make it only follow one file being written to at a time....When that file is done being written to it should move it and then move on to the next mp4 segment after it is finished being written to....
Seems to me perhaps the second segment starts being written before the first segment is moved and confuses "inotifywait"...I have tried all the options here with no success....http://[linux.die.net/man/1/inotifywait]("http://linux.die.net/man/1/inotifywait")....
Thanks again for any info....

Kernel		: Linux 3.13.0-34-generic (x86_64)
Distribution	: Ubuntu 14.04.2 LTS
inotify-tools       :3.14-1 ubuntu1

---

