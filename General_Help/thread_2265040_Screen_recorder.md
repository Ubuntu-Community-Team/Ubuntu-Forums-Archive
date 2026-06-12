---
title: "Screen recorder"
date: 2015-02-12
forum: General Help
---

### Post by imuolian on 2015-02-12
Hi there,

I'am a guy who used to make tutorials on web designing, developing, programming etc on my website. Some time ago i shifted to ubuntu from win 8. But i didn't find any good screen recorder here. All i found is some recorders having good reviews from you all but the problem lies they tool a lot of time in encoding the file. I can't wait that much. Is there any recorder that takes no time or less time?

---

### Post by carl4926 on 2015-02-12
I use VLC

---

### Post by ajgreeny on 2015-02-12
Try the simple-screen-recorder from the PPA at [https://launchpad.net/~maarten-baert/+archive/ubuntu/simplescreenrecorder](https://launchpad.net/~maarten-baert/+archive/ubuntu/simplescreenrecorder)

It works better and more simply than anything else I have seen so far.

---

### Post by imuolian on 2015-02-12
does it take time for encoding at the last?

---

### Post by imuolian on 2015-02-12
What's the size after making a 10:00 mins video?
& is it efficient enough to record? Since it's not for recording.

---

### Post by ajgreeny on 2015-02-12
To whom are those two last posts addressed?

Are you asking about vlc or SSR?

---

### Post by monkeybrain20122 on 2015-02-12
Kazam is by far the best in my experience. Many screencaster cannot handle composting. [https://launchpad.net/~kazam-team/+archive/ubuntu/unstable-series?field.series_filter=trusty](https://launchpad.net/~kazam-team/+archive/ubuntu/unstable-series?field.series_filter=trusty)

---

### Post by imuolian on 2015-02-13
I'm asking about SSR!

---

### Post by ajgreeny on 2015-02-13
> **imuolian said:**
> I'm asking about SSR!
That will depend very much on the SSR settings you choose.

You can use a scaled down %age resolution of your whole screen if you want, eg screen res of 1440x900, SSR output resolution of 50%, ie 720x450, which is what I sometimes use, and which depending on the output file-type can give an output file of about 3MB per minute using a mkv matroska file.

---

### Post by carl4926 on 2015-02-14
I'm running it (VLC) now.
It creates a pretty tidy file. Not too big at all. I also use the convert and save feature to work on video footage from Cell Phones and the like which are usually massive.
I'll drop this un-edited to my drop box. Size again, as above, can vary depending on the settings, I just used the default .mp4 for capture.
[https://dl.dropboxusercontent.com/u/10573557/Ubuntu/screen_vlc.mp4](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/screen_vlc.mp4)

---

### Post by ajgreeny on 2015-02-14
Hi carl4926.
 Just to satisfy my curiosity, how on earth do you manage to get vlc to record your desktop?

I have searched, and I've tried several ways that are suggested, but so far not one of them has managed to produce and capture a video that is saved to my filesystem.

I don't actually ***need*** to use it, as I think simple-screen-recorder is brilliant at the job; it's just that I don't like being beaten by something that you obviously find easy to do.

---

### Post by monkeybrain20122 on 2015-02-14
> **ajgreeny said:**
> Hi carl4926.
 Just to satisfy my curiosity, how on earth do you manage to get vlc to record your desktop?

I have searched, and I've tried several ways that are suggested, but so far not one of them has managed to produce and capture a video that is saved to my filesystem.

I don't actually ***need*** to use it, as I think simple-screen-recorder is brilliant at the job; it's just that I don't like being beaten by something that you obviously find easy to do.

Start vlc, click Media > Convert/Save , go to the Capture Device tab and choose Desktop from the dropdown (adjust  framerate, the default 1fps is too low) then click Save/Convert **where you can choose the output destination**. Then click Start to start recording. To stop just click the stop play button on vlc and a captured video is saved to the destination you chose. The video is smooth (using 20 fps)and it handles composting properly but it doesn't record any audio, will need to look into profile more closely. 

Haven't tried SSR, but so far kazam is the best and it is very easy to use, captures both video and audio (only thing is that the .mp4 videos produced by kazam for some reasons don't play in vlc (or Smplayer?) with vdpau enabled)

---

### Post by ajgreeny on 2015-02-14
Thanks for that info. I think convert  the one thing I didn't try as it did not occur to me that I was converting anything, and there was nothing yet to convert.
I will try it out and report back  as soon as I'm back with my xubuntu install, not this android tablet.

---

### Post by carl4926 on 2015-02-14
> **ajgreeny said:**
> Hi carl4926.
 Just to satisfy my curiosity, how on earth do you manage to get vlc to record your desktop?

I have searched, and I've tried several ways that are suggested, but so far not one of them has managed to produce and capture a video that is saved to my filesystem.

I don't actually ***need*** to use it, as I think simple-screen-recorder is brilliant at the job; it's just that I don't like being beaten by something that you obviously find easy to do.

This might help
[https://dl.dropboxusercontent.com/u/10573557/Ubuntu/vlc_convert_and_save.pdf](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/vlc_convert_and_save.pdf)

---

### Post by ajgreeny on 2015-02-15
Yes thanks.

I have just tried this and all seems to work OK for the video side, but as monkeybrain20122 says, there is no audio.

SSR records both with no problem.

---

