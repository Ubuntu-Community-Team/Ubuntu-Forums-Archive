---
title: "Chat about OBS and a couple problems"
date: 2021-07-15
forum: General Help
---

### Post by irv on 2021-07-15
I like OBS and use it for all my podcasts. I am not a Windows user, but I keep it on my desktop for testing. I have OBS installed on Ubuntu and Windows and had to do a test today.
Here is what was happening. I have been having a problem with my desktop computer just powering off in the middle of recording a video using OBS. I can make it happen at any time just by recording. So I switch to Windows and tried it, but it did not power off with the Windows version of OBS.
I had installed the PPA for OBS and was running version 27.0.1, the latest version under Ubuntu. I removed the PPA and installed the one from the snap store which is version 27.0.0. The problem went away. I wanted to report this as a bug in OBS, but I can find where or how to do this?
I am posting this here because it is not really a Ubuntu problem.
I noticed one other problem. OBS will not recognize my USB Webcam until I run another program that uses it. For example, Zoom. If I run Zoom it finds it, then I exit out of Zoom and start OBS and it finds the webcam right away. Even unplugging it and plugging it back in does not help. I can live with this annoyance but the crash thing is not good.

---

### Post by DuckHook on 2021-07-15
Given that you are an old Linux hound, you've probably heard this before, but it's a good idea to avoid PPAs whenever possible unless no other option exists and, even then, only if you know and trust implicitly the PPA's author.

Is there a functionality in 27.0.1 that you absolutely need that is not in 27.0.0? If not, then I would suggest sticking with the snap. An apt search also brings up the following (for Focal): ```
duckhook@Zeus:~$  apt search obs-studio
Sorting... Done
Full Text Search... Done
obs-studio/focal 25.0.3+dfsg1-2 amd64
  recorder and streamer for live video content

```&#8230;an older version, but one "tested" to work with Focal, since it was included in the repos only presumably after stress testing and being packaged with all needed dependencies.

If the latest and greatest via the PPA is a must&#8209;have, then make sure you have all dependencies installed. I don't use OBS, but [the installation site]("https://obsproject.com/wiki/install-instructions#ubuntumint-installation") mentions the following dependencies that you must install on your own: ```
sudo apt install ffmpeg
sudo apt install v4l2loopback-dkms
```Also, make sure you are using the right PPA: ```
sudo add-apt-repository ppa:obsproject/obs-studio
sudo apt update
sudo apt install obs-studio
```
The issue with your webcam is an odd one and I'm out of my depth there.

As for reporting bugs, it appears that OBS has its own [ecosystem with Discord, Forums, Wiki, etc]("https://obsproject.com/help"). You can probably get pointed to the right place from the old timers there. You might also try posting your issues on their forums. They are likely to have more OBS&#8209;specific experience there than on a general forum like ours.

EDIT

I've also moved the thread to General Help, as it touches on actual technical help that may be relevant to other Forum Members.

---

