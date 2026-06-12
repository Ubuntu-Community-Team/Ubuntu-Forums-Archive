---
title: "No displayport audio over nvidia graphics card"
date: 2015-12-05
forum: General Help
---

### Post by yapsuper on 2015-12-05
Hi all,

I have a nvidia gtx 760 graphics card installed on my ubuntu 14.04 LTS computer. I successfully installed the proprietary drivers and disabled the onboard graphics and audio controllers. However, I now have a problem where the audio is not working. I've opened the audio settings and there is no option to select my monitor as the audio output. I've installed pulse audio controller; the gui says that my HDMI / DisplayPort is unplugged which it obviously isn't. I plugged the HDMI port on the GPU to my TV and I can confirm that immediately sound works out of the HDMI port. 

I've tried the suggestions at these links already:

[http://askubuntu.com/questions/529911/hdmi-with-nvidia-propietary-drivers-on-14-04-1](http://askubuntu.com/questions/529911/hdmi-with-nvidia-propietary-drivers-on-14-04-1) 
[http://askubuntu.com/questions/512621/unable-to-get-audio-through-hdmi-connection-to-tv-with-ubuntu-14-04](http://askubuntu.com/questions/512621/unable-to-get-audio-through-hdmi-connection-to-tv-with-ubuntu-14-04)  

This link: [ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html#_verify_your_eld_is_valid](ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html#_verify_your_eld_is_valid) 
lead me to find this line in my dmesg
> [  325.472951] sound hdaudioC0D0: HDMI: invalid ELD data byte 88

I also found 
> eugene@olympus:~/Downloads$ cat /proc/asound/card0/eld#0.*
monitor_present		0
eld_valid		0
monitor_present		0
eld_valid		0
monitor_present		0
eld_valid		0
monitor_present		0
eld_valid		0

Can anyone help me? 

Summary:

GTX 760 
Connected via DisplayPort
Monitor is 3440 x 1440 Dell 3415 (I suspect this is important)
Prop Nvidia drivers loaded

Problem: Does not seem to detect that sound is available through Displayport, but does work over HDMI to TV with 1080p resolution.


Update: I reverted to the open source display drivers and audio has returned. So I'm guessing the problem is with the nvidia drivers. Anyone have a thought on something I should try? Wouldn't mind getting the nvidia drivers to work and get sound.

---

