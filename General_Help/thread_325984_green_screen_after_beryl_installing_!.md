---
title: "green screen after beryl installing !"
date: 2006-12-26
forum: General Help
---

### Post by F.N.D on 2006-12-26
Hello guys,

I'm newbie with beryl, i just install it following this instructions 
[http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/nVIDIA)

I already upgrade my nVIDIA card which is (GeForce FX Go5200) BTW

after i done from installing using apt
```
sudo apt-get install beryl emerald emerald-themes
```
then I reboot my laptop

an issues came with screen i took a screen-shot and i attached it

you may see my /etc/X11/xorg.conf settings: 
[http://paste.uni.cc/12493](http://paste.uni.cc/12493)

and this is info may help you to help me :)
> 
oem@ubuntu:~$  glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: GeForce FX Go5200/AGP/SSE2
oem@ubuntu:~$ uname -a
Linux ubuntu 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux
oem@ubuntu:~$ cat /var/log/Xorg.0.log | grep "Composite"
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
    

Thanks in advance 

Best of Regards,
Faisal

---

### Post by tntc1978 on 2006-12-29
I had the same problem. Instead I followed this guide: [http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl+green](http://ubuntuforums.org/showthread.php?t=263851&highlight=beryl+green) with great luck. I think it might be due to the default depth. Look at what is written just before step 5:

Please ensure that your defauldepth is at 24!!! not 16!!!

It helped me. Hope It'll help you too.

---

