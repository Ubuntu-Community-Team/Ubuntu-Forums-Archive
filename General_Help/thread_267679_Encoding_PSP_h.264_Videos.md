---
title: "Encoding PSP h.264 Videos"
date: 2006-09-28
forum: General Help
---

### Post by euxneks on 2006-09-28
***********
Edit:
I found my solution! it's only MPEG4 but at least it's working! hahahah
```

ffmpeg -i file.avi -title "Title" -s 320x240 -b 512 -ar 24000 -ab 64 -r 29.970030 -f psp output.MP4
[CODE]
Now, bear in mind, I had to install ffmpeg with other options like in:
http://ubuntuforums.org/showthread.php?t=108255

I originally thought I had done that, but I've been up late for many days so I guess I could have forgotten to do this. =)

Anyway, I have video on my psp now - it could also have been the encoding tut on 
http://ubuntuforums.org/showthread.php?t=114946
as well.. =)

***********


Hello all, I just recently bought a PSP and upgraded to the latest firmware to download some google videos and play on my PSP.  Well, that part works fine, however, I would also like to encode my own videos to watch on my psp.

Here are the following things I've tried that _don't_ work (at least, as far as I can tell, I may be just completely amateur at this ](*,)  
[CODE]
ffmpeg -i {input} -acodec aac -ab 128 -vcodec mpeg4 -b 1200 -ar 24000 -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -s 368x192 -r 30000/1001 -title {title} -f psp {output}

mencoder -oac copy -ovc lavc -lavcopts vcodec=mpeg4 -o {output} {input}

ffmpeg -i {input} -title {title} -s 368x208 -b 512 -ar 24480 -ab 64 -r 29.97 -f psp {output}

ffmpeg -i {input} -f psp -r 29.970 -s 320x240 -b 768 -ar 24000 -ab 32 {output}

ffmpeg -i {input} -acodec aac -ab 128 -vcodec mpeg4 -b 1200 -ar 24000 -mbd 2 -flags +4mv+trell -aic 2 -cmp 2 -subcmp 2 -r 23.976-s 368x192 -r 30000/1001 -title {title} -f psp -y {output}

```

I've also tried Vive, pspvc, installing psp video 9 on wine ( that failed miserably ), installing pspenc on wine ( that didn't work either )

I've also even rebooted into windows to install psp video 9 on windows and started encoding a video only to have the m*****f***** restart in the middle of the encoding due to updates. (made me remember why it's collecting digital dust on my HDD)

PSPVC works fairly nicely, but the thing is, when I try to encode a certain video, it just makes a thumbnail and then doesn't even bother to start encoding.. =)

Is there a way I can look at the headers or something of the files that _do_ work, and. based upon that, build a video..?  I can look at the videos that google uses and it looks like they have avc for the video codec and aac for the audio codec, 48 KHz sampling frequency, 300x240 Resolution... 

 - Or - 

Has anyone been able to encode video for your PSP with firmware 2.81 on ubuntu easily? Please tell me yes.

Basically I'm just tired of fighting with this as I'm sure someone out there has done this before.  I think all this stuff I've gone through should be good enough of a payment to allow me to ask for some help from someone with higher knowledge of the subject ;P ( I don't like asking questions unless it becomes a major obstacle for me )

I look forward to enlightenment!

---

