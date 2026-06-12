---
title: "Lost video portion of videos in any video player (VLC, Videos)"
date: 2019-01-26
forum: General Help
---

### Post by fr33z0n3r on 2019-01-26
I just installed Steam, on my pretty new Ubuntu 18.04 install, a couple of days ago, as well as installing a new AMD video card ,  which calls for the proprietary video drivers from AMD.  I installed this without any issue.    I did switch from the onboard video adapter (DVI) to the GPU HDMI port.  But I continue to have a single monitor only.

But I just noticed that when I play any mp4 video (possibly ANY video format) that no video portion is present (just a black window), and I only hear audio.

As I installed VLC as a snap, I'm guessing that means it actually relies on OS features it isn't installing.  Which seems to be kind of pointless, but whatevs.

Anyone have ideas on how to troubleshoot and resolve this?

FYI,  I have just tried to install "ubuntu-restricted-extras",  but after logging out and back in there is no difference.

---

### Post by SeijiSensei on 2019-01-26
```

sudo apt update
sudo apt install smplayer mpv

```

Try playing them with SMPlayer. First go to Options > Preferences > General and make sure mpv is selected as the "Multimedia engine."  Then see how well they play.

---

### Post by fr33z0n3r on 2019-01-27
I managed to get past the issue.  I found a post on AskUbuntu which described my issue and the "fix" there partially worked for me.

**How I fixed it:**.

[LIST=1]
[*]Uninstalled the amdgpu-pro video driver.  This restored the video partially (the colors were way off - bright psychedelic) 
[*]Uninstalled the package mentioned at  [https://askubuntu.com/a/1030823/918128](https://askubuntu.com/a/1030823/918128) 
[/LIST]
   ```
sudo apt-get remove gstreamer1.0-vaapi
```

---

