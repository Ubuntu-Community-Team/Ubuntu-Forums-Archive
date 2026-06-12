---
title: "Trying to get my NVIDIA optimus card working, Please help"
date: 2016-10-02
forum: General Help
---

### Post by booster.goat on 2016-10-02
I have a dell l502x laptop with the infamously screwed up hybrid graphics card system (NVIDIA GT540m and Integrated Intel GC)  
I have a freshly installed ubuntustudio 16.4.01 LTS running dual boot  with windows 10; After installing the proprietary, tested NVIDIA driver  361- recommended at the 'Additional Drivers' tab, a reboot gives a  blank screen with the mouse stuck at the top right corner, and nothing  works but a forced reboot via long-pressing the main power button.
  I have tried all the different driver versions and all the different  PPA repositories (xorg-edgers, graphics-drivers etc), the same issue  persists. 
  The system however reboots successfully if the 'intel' card is selected by the command
      sudo prime-select intel

  when the NVIDIA card is selected
      glxgears
  gives the following error
      ```
Error: couldn't get an RGB, Double-buffered visual
  
```
command 
      
```
lspci -k | grep -EA2 'VGA|3D'
  gives
  00:02.0 VGA compatible controller: Intel Corporation 2nd Generation  Core Processor Family Integrated Graphics Controller (rev 09)     Subsystem: Dell 2nd Generation Core Processor Family Integrated  Graphics Controller
  Kernel driver in use: i915
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 540M] (rev ff)     Kernel modules: nvidiafb, nouveau, nvidia_361
```
       

```
dkms status
  bbswitch, 0.8, 4.4.0-38-lowlatency, x86_64: installed nvidia-361, 361.42, 4.4.0-38-lowlatency, x86_64: installed
```
      
```

glxinfo | grep OpenGL
  Error: couldn't find RGB GLX visual or fbconfig
```



I have tried bumblebee as well, but it also gives the same error, when a program is run through the optirun command

---

