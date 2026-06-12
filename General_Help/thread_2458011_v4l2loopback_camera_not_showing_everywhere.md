---
title: "v4l2loopback camera not showing everywhere"
date: 2021-02-14
forum: General Help
---

### Post by dorpapst on 2021-02-14
Hello friends,
I have installed v4l2loopback on a new computer, wanting to create a virtual camera (inserting a virtual background by myself, but that doesn't matter :).

When I list my devices with
```
v4l2-ctl --list-devices
```
I will get the following results:
```
OBS Video Source (platform:v4l2loopback-000):
    /dev/video10

UVC Camera (046d:081b) (usb-0000:07:00.3-2):
    /dev/video0
    /dev/video1

```

video0 is the origin and video10 is the virtual one.

The interesting thing is that video10 only shows up in particular programmes. I can choose it on Jitsi-Websites in Firefox and also use it in Discord.
But it does not show up in Zoom and Skype at all, it only lets me choose video0, which will be black (the latter one makes sense to me)

Is there any reason why this could be the case?
lsmod | grep -i v4l2loopback says that the module is loaded properly.

I am using the following settings:
```
options v4l2loopback video_nr=10 card_label="OBS Video Source" exclusive_caps=1
```

Is there anyone having an idea on how to solve that?

Many greetings and thank you.
Lukas

---

### Post by deadflowr on 2021-02-14
Do you know which package versions of skype and zoom are installed?
(Are they deb packages or snap packages?)

---

### Post by dorpapst on 2021-02-14
Thank you for your answer.
I installed Skype that way:
```
wget [https://go.skype.com/skypeforlinux-64.deb](https://go.skype.com/skypeforlinux-64.deb)
sudo apt install ./skypeforlinux-64.deb
```

Zoom got installed the same way by downloading it and then running apt:
```
sudo apt install ./zoom_amd64.deb
```

---

### Post by dorpapst on 2021-02-15
Update: I got a hint from a friend and it works now.
The solution for me was to not install v4l2loopback-dkms via apt, but building it myself via the GitHub-project.
[https://github.com/umlaeute/v4l2loopback](https://github.com/umlaeute/v4l2loopback)

---

