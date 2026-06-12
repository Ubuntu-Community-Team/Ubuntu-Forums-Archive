---
title: "Custom resolution for the TTY console for raspberry pi ubuntu latest 22.04"
date: 2022-06-21
forum: General Help
---

### Post by anarchy89 on 2022-06-21
I just got a small LCD screen. The resolution is 1920x500 over hdmi.

I have installed ubuntu server with no GUI. On my 1080p monitor, the resolution appears normal, but when i plug it into this monitor, its at 640x480 stretched. 

When I plugin my windows pc into this monitor I am able to get 1920x500.

I tried to modify the /boot/firmware/config.txt to include the following lines,

```

hdmi_cvt=1920 500 60 6
hdmi_group=2
hdmi_mode=65
hdmi_drive=2

```

It still looks the same. I have attached what it looks like.

Just to be clear, I am trying to change the resolution of the TTY console. How do I change the resolution?

---

### Post by Holger_Gehrke on 2022-06-21
Not surprising that it doesn't work. According to the [reference for config.txt at raspberrypi.com]("https://www.raspberrypi.com/documentation/computers/config_txt.html#custom-mode") mode 65 is the custom mode in group 1. For group 2 you could try mode 87.

Holger

---

