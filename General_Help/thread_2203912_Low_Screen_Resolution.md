---
title: "Low Screen Resolution"
date: 2014-02-05
forum: General Help
---

### Post by twaelbroeck on 2014-02-05
The max I can set my resolution currently is 1024x768, but my laptop's native resolution is 1920x1080. I've always been able to set it to 1920x1080 without issue, but since I broke my video driver (I installed 'nvidia-current' which broke my display, see [this thread]("http://askubuntu.com/questions/414713/how-to-fix-lubuntu-gui")) I haven't been able to get above the aforementioned 1024x768.

I've tried the instructions from [this thread]("http://ubuntuforums.org/showthread.php?p=8595940&mode=linear#post8595940") and [this wiki]("https://wiki.ubuntu.com/X/Config/Resolution") but haven't made any progress.

```
travis@travis-ThinkPad-W510:~$ lscpi |grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GT216GLM [Quadro FX 880M] (rev a2)
```

```
travis@travis-ThinkPad-W510:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0  
   848x480         0.0  
   640x480        60.0  


```

Any suggestions?

---

### Post by sudodus on 2014-02-06
Do you want to get back your built-in graphics driver (it is probably nouveau for your nvidia graphics)?

If you have a current and updated version of Ubuntu, you should be able to run

```
sudo apt-get remove nvidia-current
```

and reboot

---

