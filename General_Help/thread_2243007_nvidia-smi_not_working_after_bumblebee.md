---
title: "nvidia-smi not working after bumblebee"
date: 2014-09-05
forum: General Help
---

### Post by Paul_Cambal on 2014-09-05
Hi everyone,
Well, pretty much everything is in the title. I just installed bumblebee, rebooted, and launched optirun chromium-browser
To check if it was really running with my nvidia card, I tried running nvidia-smi, but the console told me "command not found" :(. That's weird because it worked before installing bumblebee. So I checked if the command still existed , and yeah, it's still there at /usr/lib/nvidia-331/bin. OK I googled a bit and found that: [http://askubuntu.com/questions/407012/gather-discrete-gpu-temperature-optimus](http://askubuntu.com/questions/407012/gather-discrete-gpu-temperature-optimus). So I input this in the console: ```
sudo ln -s /usr/lib/nvidia-331/bin/nvidia-smi /usr/bin/nvidia-smi.
```
Worked fine.
But then :
```
yhu420@N53SM:~$ nvidia-smi
NVIDIA-SMI couldn't find libnvidia-ml.so library in your system. Please make sure that the NVIDIA Display Driver is properly installed and present in your system.
Please also try adding directory that contains libnvidia-ml.so to your system PATH.
```
:mad:
First reflex: 
```
yhu420@N53SM:~$ lspci | grep -i nvidia
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 630M] (rev a1)
```

Mmmh... whaaaaaa daaaa fak!?

Do I have to reinstall something? Thanks for every of your answers :p

EDIT:
```
yhu420@N53SM:~$ locate libnvidia-ml.so/usr/lib/nvidia-331/libnvidia-ml.so
/usr/lib/nvidia-331/libnvidia-ml.so.1
/usr/lib/nvidia-331/libnvidia-ml.so.331.38
/usr/lib32/nvidia-331/libnvidia-ml.so
/usr/lib32/nvidia-331/libnvidia-ml.so.1
/usr/lib32/nvidia-331/libnvidia-ml.so.331.38

```

---

### Post by chapkin on 2014-09-07
same issue here (14.04, nvidia 304), most interesting is that that library does exist, and when added to the PATH - nothing changed.
cannot find
when I run in with optimus - optirun nvidia-smi
it says 
[ 6204.211555] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0.  Please

[ 6204.211657] [ERROR]Aborting because fallback start is disabled.

---

### Post by Paul_Cambal on 2014-09-08
> [COLOR=#000000][ 6204.211555] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA GPU at PCI:1:0:0. Please[/COLOR]

I think that's because you use the X.org drivers. I think using the nvidia drivers would be a better thing. To do so go to setting, under system -> software and updates -> additional drivers, and select the option on the top.

That doesn't solve the problem though :/

Do you guys think I should reinstall the driver?

---

### Post by ale15 on 2015-05-05
Hi, 
I had the same error, with bumblebee, same drivers, and ubuntu 14.04. 
In the probable case we share the same configuration, this is what worked for me:

1) sudo update-alternatives --config x86_64-linux-gnu_gl_conf 

=== this is my output ===
There are 3 choices for the alternative x86_64-linux-gnu_gl_conf (providing /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf).


  Selection    Path                                       Priority   Status
------------------------------------------------------------
  0            /usr/lib/nvidia-331/ld.so.conf              8604      auto mode
* 1            /usr/lib/nvidia-331-prime/ld.so.conf        8603      manual mode
  2            /usr/lib/nvidia-331/ld.so.conf              8604      manual mode
  3            /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf   500       manual mode
==================

and I choose 1, and enter. 

2) optirun nvidia-smi

If it does not work, try it again with sudo

2') sudo optirun nvidia-smi

If it works, you will probably not need sudo anymore if you want to run it again, unless you reboot.

Hope it helps.

 



> **Paul_Cambal said:**
> I think that's because you use the X.org drivers. I think using the nvidia drivers would be a better thing. To do so go to setting, under system -> software and updates -> additional drivers, and select the option on the top.

That doesn't solve the problem though :/

Do you guys think I should reinstall the driver?

---

