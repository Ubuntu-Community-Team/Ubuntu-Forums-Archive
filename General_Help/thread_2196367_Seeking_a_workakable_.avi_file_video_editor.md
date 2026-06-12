---
title: "Seeking a workakable .avi file video editor"
date: 2013-12-29
forum: General Help
---

### Post by Richard_York on 2013-12-29
I'm running Ubuntu 12.04, and gradually learning to drive more of it.
I loaded an .avi video, about 1 minute long, from my camera. (Don't usually take vid's, so it's not a familiar medium to play with for me.) It's about 50Mb as it stands.  I'd like to put it on Facebook, for family & friends. I'm told Youtube would be the easiest way, but don't want to share it with the world, which I believe is the only way there (Never done that either!) At present if I ask Fbook to upload it it just sits there for ages, with nothing apparently happening, and no signs of activity on my system monitor display. I assume it's just too big as it stands.

Is there workable, friendly software which can reduce the size, perhaps by scaling down the image size? I searched "Video Edit" and "avi edit" in the Software Centre, but all the reviews on those listed stress how often they crash, how unworkable, how stressing to use...

Any help welcome, please - I've been really impressed by how helpful this forum is in the few months since becoming a Linux user!

Thanks.

---

### Post by sotiris2 on 2013-12-29
What is the file size?  Also youtube appears to have an 'unlisted' option which i presume means it won't show up in search results. It also has a private setting , although I think its affiliated with google plus but it does have an option to input e-mail addresses (it will probably send them a link/password).

---

### Post by 3rdalbum on 2013-12-29
Well yeah, video editors on Linux have traditionally been a bit crashy, but earlier this year when I did a simple video edit I noticed that Openshot was very stable.

Openshot and Kdenlive are certainly capable of compressing your video; for best results, choose one of the preset output settings. You could also try FFMPEG on the command-line:

```
ffmpeg -i <input file> -b 576k -s 320x240 -vcodec mpeg4 -r 25 -ab 192k -ar 44100 -ac 2 -acodec aac -strict experimental <output file>
```

(substitute <input file> and <output file> for the actual file paths of the input file and the new output file to create. The output file must have the extension ".mp4".)

You can tweak these values too. See the FFMPEG manual for more details on what these options are.

---

### Post by vanadium on 2013-12-29
ffmpeg or avconv are the fastest and best options for such task. winff is a gui for avconv, that may make the process easier.

---

### Post by kurja on 2013-12-29
Youtube has the option to not show your video in any search results, so only anyone with a link provided by you can find it. Just set privacy to "unlisted". So it's not exactly protected but any casual web surfer isn't going to find it.

---

### Post by Richard_York on 2013-12-29
Thanks all for these replies - plenty of things to try here! I understand about YouTube having a restricted setting option, though I haven't ever posted there, but if I can simply reduce the file size myself I'll try that first, looking at these suggestions to do so.
Thanks again,
Richard.

---

