---
title: "Is there a GUI utility to merge two or more MPEG-4 video files into a single file?"
date: 2018-01-16
forum: General Help
---

### Post by AbleTassie on 2018-01-16
I have used Handbrake to convert .VOB video files to MPEG-4 video files. But I would like to merge (or join) two or more of these MPEG-4 files into a single MPEG-4 file. I do not see any way to do this using Handbrake. 

QUESTION: Is there a way to merge two or more MPEG-4 video files into a single file with a utility that has a GUI? Can it be done with Handbrake?

Thanks,

A.

---

### Post by monkeybrain20122 on 2018-01-16
I think winff can do that.

---

### Post by mastablasta on 2018-01-17
openshot or kdenlive should be able to do it quite easily. you can also setup transitions between videos etc.
[https://www.openshot.org/](https://www.openshot.org/)
[https://kdenlive.org/](https://kdenlive.org/)

---

### Post by sudodus on 2018-01-17
+1 for openshot

---

### Post by Juhele on 2018-01-17
I think Avidemux can also do this using the Append file option and then save it using "Copy" mode for audio and video if you do not want to recode the video and audio. But it requires all videos with same parameters, codec etc.

BTW if the source is standard DVD Video then Avidemux often after loading first .VOB offers to add also the others and load it as one file.

---

### Post by AbleTassie on 2018-01-17
Thanks to everybody for their suggestions. I will give one or more of these utilities a try and see how they work.

A.

---

### Post by AbleTassie on 2018-01-17
As an update, I installed openshot, but it is taking a very long time to merge two mpeg4 video files into a single mpeg4 video file. So it may not be practical because of the time constraint. Maybe I can do something to make it take less time; I'm not sure. 

I have installed kdenlive and winff, but Avidemux is not in the Lubuntu Software Repos, so I am reluctant to install it.

Any comments anybody has will be welcomed.

Thanks,

A.

---

### Post by mastablasta on 2018-01-18
for video processing you need to have plenty of RAM and good CPU. what these do is basically separate video into frames and then merge them back together. i would also say to look at some instructional videos on how to do it online. perhaps you missed a setting. it also depends a lot on how long the videos are and their recording quality (HD, 4K...) & size.

if you have a weaker CPU you could also queue the jobs and then let them run overnight.


it is still way easier and less risky  than gluing the film together.

---

### Post by lisati on 2018-01-18
If you're looking to putting the merged MP4 files on to DVD, you might want to look at DVDstyler, which I've seen in *nix and Windows versions.

---

### Post by Juhele on 2018-01-18
I think I have Avidemux installed from GetDeb:
[http://www.getdeb.net/updates/Ubuntu/17.04/?q=avidemux](http://www.getdeb.net/updates/Ubuntu/17.04/?q=avidemux)

This link is for 17.04 Zesty but you can change *buntu version in drop down menu on the top of the page.

---

### Post by Habitual on 2018-01-18
audacity ?

---

### Post by AbleTassie on 2018-01-18
I was playing around with this last night and it appears that the main problem is the amount of time it takes to splice two separate videos together with OpenShot.The files are each about 250MB and both are MPEG-4 video. It seems to take a very long time even if the two files to be spliced and the output file are the same type, MPEG-4, and I choose low definition for the outputted file. The instructions for OpenShot for splicing do not really seem all that clear or intuitive. Maybe something online would help if I could find it. 

I'm looking at Kdenlive and there are instructions, maybe the instructions for it will be clearer to me. I don't really see instructions for WinFF, just a website featuring Big Matt.  

The original files are from a DVD that I just copied to my hard drive as .VOB files. I converted them to MPEG4 files using Handbrake, because I wanted to look at them on a large screen TV. But I noticed that Handbrake does not automatically convert all of the VOB files in a particular folder, let alone automatically splice them. And in addition, it does not appear I can merge or splice using Handbrake even if I intentionally try. I was kind of hoping I could splice the original VOB files when they were being converted to MPEG4 files, but I don't see how to do this. And there really are no instructions for Handbrake, I just get a blank webpage at [http://trac.handbrake.fr/wiki/HandBrakeGuide](http://trac.handbrake.fr/wiki/HandBrakeGuide) when I try to access the instructions for Handbrake.

Is Avidemux more intuitive, easier or faster? Is installing from GetDeb safe?

Any other comments will be welcomed.

Thanks to everybody,

A.

---

### Post by AbleTassie on 2018-01-19
> **Habitual said:**
> audacity ?

Audacity is a great utility, but I think Audacity is strictly for audio files, not video.

Thanks,

A.

---

### Post by spjackson on 2018-01-19
> **AbleTassie said:**
> And there really are no instructions for Handbrake, I just get a blank webpage at [http://trac.handbrake.fr/wiki/HandBrakeGuide](http://trac.handbrake.fr/wiki/HandBrakeGuide) when I try to access the instructions for Handbrake.

This link [https://handbrake.fr/docs/en/1.0.0/](https://handbrake.fr/docs/en/1.0.0/) works. However, under the section "What HandBrake does not do" it says "HandBrake does not... combine multiple video clips into one". So that may not help you.

---

### Post by mastablasta on 2018-01-19
> **AbleTassie said:**
> 
Is Avidemux more intuitive, easier or faster? Is installing from GetDeb safe?
.

getdeb is safe. Avidemux is with less features, simpler interface. since you do not plan on getting the videos to the movie academy awards it might just do. :)

another one you could try is Shotcut. i used it on Core i3 (win10, 6th gen, intel GPU, 4 GB ram) to mix 3 files of similar size to yours and when i was done i think it took a few minutes (5-10, maybe 15) to put it all together. only i added osme effects and such. in any case it wasn't all that long.

i think Kdnelive should also be a good option. i used the older version for doing something like that. but it was a year ago and i don't remember the time it took on the old Celeron E3300.

since you are not actually transcoding it should take that long. transcoding of files with such size should be about 15, 20 minutes on Core i3. maybe even less.

---

### Post by Yellow Pasque on 2018-01-19
I know you said GUI, but it may be worth using ffmpeg directly to see how long it takes.
[https://stackoverflow.com/questions/7333232/concatenate-two-mp4-files-using-ffmpeg#11175851](https://stackoverflow.com/questions/7333232/concatenate-two-mp4-files-using-ffmpeg#11175851)

> It seems to take a very long time even if the two files to be spliced and the output file are the same type, MPEG-4, and I choose low definition for the outputted file. 

Are you sure that they're the same video/audio codec (and that Openshot isn't doing any reencoding)? Check the files (and the output file) with mediainfo. People get confused and think all *.mp4 files are the same, but mp4 is a container and can hold different A/V codecs .

---

### Post by dragonfly41 on 2018-01-19
I really don't know if this fits the requirement
but some time back I installed ffDiaporama
to explore video editing.


[http://ffdiaporama.tuxfamily.org/](http://ffdiaporama.tuxfamily.org/)

---

### Post by AbleTassie on 2018-01-20
> **Temüjin said:**
> I know you said GUI, but it may be worth using ffmpeg directly to see how long it takes.
[https://stackoverflow.com/questions/7333232/concatenate-two-mp4-files-using-ffmpeg#11175851](https://stackoverflow.com/questions/7333232/concatenate-two-mp4-files-using-ffmpeg#11175851)


Are you sure that they're the same video/audio codec (and that Openshot isn't doing any reencoding)? Check the files (and the output file) with mediainfo. People get confused and think all *.mp4 files are the same, but mp4 is a container and can hold different A/V codecs .

Temüjin,

Thanks, I checked the files with Mediainfo and the input files are similar, but the output file (combination file) appears different. I've attached mediainfo screenshots from the two inputs and the single output. The two inputs are MPEG-4 (Base media/version2) but each have one video stream that is AVC and one audio stream that is AAC. The output is MPEG-4 (Base media) but has one video stream that is MPEG-4 visual and one audio stream that is MPEG-4 audio. So maybe there really is transcoding being done.

Screenshots of mediainfo for the two inputs and single output for Openshot are attached below.

I cannot see anyway to use the drop down menu selections to make the Openshot output video and audio streams to match the input audio and video streams.

Thank you,

A.

P.S. The outputs in Handbrake are limited to either Matroska AV format or MPEG-4 AV Format. So I don't see an easy way that I can change the two inputs to Openshot (each of which is an output from Handbrake) to make them match a potential merged output from Openshot.

[ATTACH=CONFIG]278246[/ATTACH][ATTACH=CONFIG]278247[/ATTACH][ATTACH=CONFIG]278248[/ATTACH]

---

