---
title: "get-iplayer file size"
date: 2024-05-01
forum: General Help
---

### Post by phatton1 on 2024-05-01
I know this has been asked before in the forum, and have tried the suggestions.
I've also googled this but most only apply to older versions.

I've added get-iplayer v 3.36 via snap.
It works but, as an example, a one hour programme downloads as a 2.5gb file

I ran get-iplayer --help and tried each of the options from --tvquality but they don't seem to make any difference to the filesize.

Can anyone help and tell me what I'm doing wrong and point me to reduce the size?

TIA

---

### Post by tea for one on 2024-05-01
> **phatton1 said:**
> It works but, as an example, a one hour programme downloads as a 2.5gb file
Just offering info because I always allow get-iplayer to use default settings.
> Configuring recording quality
It is recommended that you use default settings unless you want to restrict recording to lower-quality streams. You may wish to do so if, for example:
    HD TV requires 2GB+ storage per hour of video, which may be too much for your needs
    You may feel that 320kbps is unnecessary if you only record speech radio programmes
Info above from here [https://github.com/get-iplayer/get_iplayer/wiki/quality](https://github.com/get-iplayer/get_iplayer/wiki/quality)
The link offers suggestions for cli parameters.

If I remember correctly, the last time I downloaded a 60 min BBC TV programme, the file size was 1.9-2.0GB
This was using using snap version 3.35

As a comparison, a commercial DVD (film or concert), a 120 min performance is often 4.5GB

---

### Post by phatton1 on 2024-05-01
Thanks tea for one, but I've tried the default settings, and it still results in 2.5gb
It used to be less than 1gb &#128542;

---

### Post by tea for one on 2024-05-01
> **phatton1 said:**
>  but I've tried the default settings, and it still results in 2.5gb
Yes, as I mentioned, the default settings rendered me a file approx 2.0GB for one hour of TV.

---

### Post by ActionParsnip on 2024-05-01
You can use commands and such, to reduce quality and therefore file size.
Something like this
[https://www.baeldung.com/linux/video-downsample-lower-resolution#:~:text=Using%20MEncoder&text=We%20can%20use%20the%20MEncoder,video%20to%20a%20lower%20resolution.&text=Here%2C%20we%20are%20specifying%20the,lavc%20for%20downsampling%20the%20video](https://www.baeldung.com/linux/video-downsample-lower-resolution#:~:text=Using%20MEncoder&text=We%20can%20use%20the%20MEncoder,video%20to%20a%20lower%20resolution.&text=Here%2C%20we%20are%20specifying%20the,lavc%20for%20downsampling%20the%20video).
Set a lower bitrate

Bit of a work around but should fly

---

### Post by phatton1 on 2024-05-01
Thanks ActionParsnip, but this seems to cover everything except get-iplay

---

### Post by phatton1 on 2024-05-06
I've figured out that if I add the TV quality option to the end of the get-iplayer command, it works and file size is much better.
But running get-iplayer --tvquality=sd doesn't write to a conf file as it used to.
Anyone know how to get it to a) create a conf file and then to write to it?
TIA

---

### Post by phatton1 on 2024-05-09
Finally sorted. 
Earlier versions created a Prefs file, 3.36 doesn't.
It's necessary to add --tvquality= 
To the command, then it works as it used to.
Quality settings can be found with get-iplayer --help 
Thanks anyway everyone for the suggestions

---

