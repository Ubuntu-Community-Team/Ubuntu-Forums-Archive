---
title: "Audio file won't start playing until 20+ second after press 'play button'"
date: 2023-03-05
forum: General Help
---

### Post by xanizen on 2023-03-05
This problem arose after I encountered the following scenario of not being able to access the login screen due to fstab referring to non-existent partition, and having to physically disconnect a hard drive with mirrored Ubuntu system/installation files, created with Clonezilla.
[https://ubuntuforums.org/showthread.php?t=2484592](https://ubuntuforums.org/showthread.php?t=2484592)

While in emergency mode, I recall the prompt asking me if I wanted to delete 40 MB of 'unused/unneeded files, I wasn't of what to do, then 15 seconds later, it went aheads and selected the default, Y/yes, and presumably deleted it.

Also I had to re-install Firefox; all the cookie files and website bookmarks were gone.

Sometimes, the audio will take 3 seconds to start playing instead of 20+ seconds. Problem happened with Strawberry (Clementine fork) and SMPlayer (MPV engine).

**Edit**: This also happens when I pause the song, for say 5+ minutes and then attempt to resume it; it won't resume playing. I tried opening the same song with a different program, SMPlayer/Mpv/VLC and it won't start playing. In the case of VLC, the progress bar moves but there is no audio. **2 to 3 minutes later it started playing**.

**Edit**: Also happens with .webm and .mp4 video file, first .265 seconds is played (2/10ths of second), and video stops. I also had to re-install the video drivers, due to flickering screen. I'll try to purge the codecs.

I uninstalled the ubuntu-restricted-extras & x265 codecs using 'Synaptic package manager' and the problem persists, also on v.redd.it (reddit.com) videos as well.

---

### Post by kingpenguin on 2023-03-28
I am not saying this is a solution at all but if you are willing to try, you can use ffmpeg to see if it is something with the software you are using or if it is the operating systems. [https://askubuntu.com/questions/750754/how-to-play-video-using-ffmpeg-on-ubuntu](https://askubuntu.com/questions/750754/how-to-play-video-using-ffmpeg-on-ubuntu). Also with the different formats that you are talking about, are they the same encoding under the different extensions?

---

