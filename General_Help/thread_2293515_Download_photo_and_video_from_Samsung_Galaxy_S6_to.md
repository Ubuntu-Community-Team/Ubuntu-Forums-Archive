---
title: "Download photo and video from Samsung Galaxy S6 to PC"
date: 2015-09-05
forum: General Help
---

### Post by satimis on 2015-09-05
Hi all,


I want to download Photos/Video taken on Samsung Galaxy S6 mobile phone to PC.

Can Samsung Smart Switch be installed on Ubuntu 14.04
If Yes please advise how to do it?
If No, please advise its substitute?

Thanks

Regards
satimis

---

### Post by HermanAB on 2015-09-05
You will likely have more luck transferring files over Bluetooth than over USB.  Alternatively, you can install a SSH program on your phone (if you rooted it) and then use scp.

---

### Post by SeijiSensei on 2015-09-05
I have used a USB cable, Wifi File Transfer Pro, Acrosync, and AndSMB to communicate with my server or client machines.  Some info on these options in the link in my signature.

---

### Post by satimis on 2015-09-05
> **SeijiSensei said:**
> I have used a USB cable, Wifi File Transfer Pro, Acrosync, and AndSMB to communicate with my server or client machines.  Some info on these options in the link in my signature.
Hi,

After connecting Samsung Galaxy S6 to computer the former is automatically mounted.  Photo and video are stored on Gallery but I couldn't find this item on computer.

satimis

---

### Post by efflandt on 2015-09-06
When you connect your phone by USB (when not screen locked) does the file viewer come up or something else? If the file viewer comes up, photos or videos you take with the phone would typically be under DCIM/Camera/ (DCIM is a pretty standard path for photos/videos on any camera). Although, if you downloaded photos or videos from web or e-mail attachments you likely have to look in other paths.

I don't know if there is something different about MTP with the S6 vs. my S3. But when I could not get MTP to work at all in 12.04 I installed ConnectBot (ssh client), AndFTP (sftp client), and SSHServer apps on my phone, so I could scp or sftp from either end when connected to local WiFi (using my Linux openssh keys). But MTP works for my S3 in Ubuntu 14.04 (and worked in 13.10).

---

### Post by satimis on 2015-09-06
> **efflandt said:**
> When you connect your phone by USB (when not screen locked) does the file viewer come up or something else? If the file viewer comes up, photos or videos you take with the phone would typically be under DCIM/Camera/ (DCIM is a pretty standard path for photos/videos on any camera). Although, if you downloaded photos or videos from web or e-mail attachments you likely have to look in other paths.

I don't know if there is something different about MTP with the S6 vs. my S3. But when I could not get MTP to work at all in 12.04 I installed ConnectBot (ssh client), AndFTP (sftp client), and SSHServer apps on my phone, so I could scp or sftp from either end when connected to local WiFi (using my Linux openssh keys). But MTP works for my S3 in Ubuntu 14.04 (and worked in 13.10).
Hi,

Thanks for your advice.

Connected phone to USB with screen unlocked

Found 3 files on;
DMIC/Camera
20150826_215716.mp4
20150829_092352.mp4
20150903_094353.mp4

None of them can be played

```

An error occurred
The movie could not be read
[OK]

```

Shall I download them first?


But on Gallery of the phone there are 4 video


Edit:
Download 1 video.  It can be played but rotated 90deg counter-clockwise/

Regards
satimis

---

### Post by satimis on 2015-09-06
Hi all,

I found out the cause of my problem.  It is due to taking the video in portrait (holding the phone vertically).  The video player can't play it in landscape.  Any solution?  Use Openshot?

satimis

---

### Post by SeijiSensei on 2015-09-06
SMPlayer has a "rotate" menu option that should work for playback.  It uses the corresponding "-vf rotate" option in mplayer or "--video-rotate" in mpv.  If you want to rotate the file then save it, you can use [ffmpeg]("https://ffmpeg.org/ffmpeg-filters.html#rotate").

---

### Post by satimis on 2015-09-06
> **SeijiSensei said:**
> SMPlayer has a "rotate" menu option that should work for playback.  It uses the corresponding "-vf rotate" option in mplayer or "--video-rotate" in mpv.  If you want to rotate the file then save it, you can use [ffmpeg]("https://ffmpeg.org/ffmpeg-filters.html#rotate").
Hi,

My problem is taking the video with the phone in vertical position.  On playback the video player plays the video in landscape position (horizontally).  Unless I rotate the monitor to vertical position then I can view the video correctly.


ffmpeg can't help.  I have tried

satimis

---

### Post by SeijiSensei on 2015-09-08
If you play the video back with SMPlayer, you can rotate it to portrait mode.

---

### Post by FakeOutdoorsman on 2015-09-08
> **satimis said:**
> ffmpeg can't help.  I have tried

What have you tried? The command and complete console output will be informative.

---

### Post by satimis on 2015-09-08
> **SeijiSensei said:**
> If you play the video back with SMPlayer, you can rotate it to portrait mode.
Hi,

Thanks for your advice.

I sorted out my problem on;
Rotate Video Online
[http://rotatemyvideo.net/](http://rotatemyvideo.net/)

just a few click.

satimis

---

### Post by efflandt on 2015-09-09
One thing that I have noticed is that I cannot "open" files (images or videos) on the USB connected phone from Ubuntu. I have to copy them over to Ubuntu first.

---

### Post by satimis on 2015-09-09
> **efflandt said:**
> One thing that I have noticed is that I cannot "open" files (images or videos) on the USB connected phone from Ubuntu. I have to copy them over to Ubuntu first.
Hi,

It is the same happened here before.  Another problem is that the video taken in .mp4 with portrait (holding the phone vertically to shoot) will be played back in landscape.  I couldn't rotate it with ffmpeg/openshot/avconv.  Finally following website helped me to rotate it 90deg;

Rotate Video Online
[http://rotatemyvideo.net/](http://rotatemyvideo.net/)

satimis

---

