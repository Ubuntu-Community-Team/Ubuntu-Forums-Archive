---
title: "I can't config properly my screen and nvidia on Ubuntu"
date: 2018-10-14
forum: General Help
---

### Post by menzuberranzan on 2018-10-14
I'm a little bit tired and desperate, is for that reason for what I'm writing this. I believe in free software and their benefits, BUT sometimes this issues could be stressing.

I got a fresh install of Ubuntu 18.04 LTS also I'm a neophyte using linux but I tried and tried config my screen, an Asus VX228H is perfectly compatible at 1920x1080 at 60Hz But after the installation and the reboot the system put it in 1024x768 76hz. 

Also I'm trying to config my nvidia drivers, I got a NVIDIA GTX 750 and the drivers for that video card are 390.87. I install the 390 drivers properly using the sofware screen but WHY in the name of GODS after the reboot Ubuntu convert that in llvmpipe (LLVM 6.0, 256 bits)!!!! And WHERE I can find a solution for this.

I try to play videogames with my actual configuration and after a 5 or 10 minutes playing the screen crash frozen and when y reboot a black screen says 
error hwach 
error no video mode activated.

There's Hope for my or I need to return to the horrible Windows OS

Please help me and thanks by the advance.

---

### Post by NM5TF on 2018-10-14
post the output of

```
inxi -G
```

and this one

```
xrandr
```

and this one

```
cvt 1920 1080
```

they might look something like this screenie

tommy

---

### Post by menzuberranzan on 2018-10-14
one@nuke:~$ inxi -G

Graphics:  Card: NVIDIA GM107 [GeForce GTX 750]
           Display Server: x11 (X.Org 1.19.6 )
           drivers: fbdev,nouveau (unloaded: modesetting,vesa)
           Resolution: 1024x768@76.00hz
           OpenGL: renderer: llvmpipe (LLVM 6.0, 256 bits)
           version: 3.3 Mesa 18.0.5

one@nuke:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected primary 1024x768+0+0 0mm x 0mm
   1024x768      76.00* 

one@nuke:~$ cvt 1920 1080

# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
one@nuke:~$ 

Don't work, sorry it remanis the same...

---

### Post by NM5TF on 2018-10-14
you say that you installed the 390.87 nvidia driver....but inxi -G shows it is using fbdev & nouveau.....

something wrong there....

did you use the Software & Updates screen + the Additional Drivers screen to install the driver ???
if so, did you reboot after to have the change take effect ???

here is something to try.....open a terminal & type

```
sudo apt install nvidia-driver-390.87
```

after the driver installs, reboot to enable nvidia-prime

```
sudo shutdown -r now
```

check to see if it is now using nvidia 390.87 driver

```
sudo lshw -c display
```

hopefully it is,,,,

tommy

---

### Post by menzuberranzan on 2018-10-15
Okey Tommy I's tart again from the beginning. I Install again Ubuntu. I made a Upgrade and Update and try to install the specific version for my video nvidia card 750, they say that the drivers are 390.87

sudo apt install nvidia-driver-390.87
Leyendo lista de paquetes... Hecho Reading list of packages (Done)
Creando árbol de dependencias       Creating...
Leyendo la información de estado... Hecho Reading information ..
E: No se ha podido localizar el paquete nvidia-driver-390.87 It can't be found the package ....
E: No se pudo encontrar ningún paquete usando «*» con «nvidia-driver-390.87» There's no using package 
E: No se pudo encontrar ningún paquete con la expresión regular «nvidia-driver-390.87» I can't find any package

 but when I try to install from console using this command because I already download from the web site the drivers 390.87 the system says: 

sudo sh ./NVIDIA-Linux-x86_64-390.87.run
sh: 0: Can't open ./NVIDIA-Linux-x86_64-390.87.run

The misterious package that the systems never found BUT the Nvidia permits to download hahah... No seriously, any ideas?

Thanks for the Help.

---

