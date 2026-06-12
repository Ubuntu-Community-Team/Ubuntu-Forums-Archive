---
title: "beryl,on edgy what is happening"
date: 2007-01-08
forum: General Help
---

### Post by STREETURCHINE on 2007-01-08
trying to install beryl on edgy using this guide

     [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL)

i tried 
               glxinfo | grep direct

and got

                direct rendering: Yes

so of i go i followed the guide ,copied and pasted all the commands .
but when i had finished and rebooted  beryl would not work

when i typed beryl-manager into terminal it told me xgl was not present
i tried several times to download xgl-xserver but could not get the full packages.

if i got the answer direct rendering :yes it means i had already got 3d acceleration working before i started...so what happend

i deleted it all and tried to install by this how to

               [http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)

but i cant connect to that site ,connection times out.

so i was wondering is beryl down or broken. i would rather do the aiglx than xgl

---

### Post by tomcat1965 on 2007-01-08
Edgy comes with AIGLX,use the Beryl official Instructions here:

 [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

That'll get it working for you.:cool:

---

### Post by STREETURCHINE on 2007-01-08
nope broke my xserver-xorg so that is that,

edgy always refuses to find my back up and i tried to reconfigure it but ,

some gtk warning or something like that refuses to open xserver-xorg so i can reconfigure

well i either reinstall or give up on edgy alltogether,,  :-k

---

### Post by anjoze on 2007-01-08
Try this:
1- Update your Edgy
2- Install the latest Nvidia drivers: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) (this is realy good)
3- fallow the instructions on: [http://wiki.beryl-project.org/wiki/Main_Page](http://wiki.beryl-project.org/wiki/Main_Page)

My beryl is working perfect with these steps.

---

### Post by STREETURCHINE on 2007-01-08
followed these steps but it failed to work.

 rex@rex-desktop:~$ Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap absent, using Copy mode
Xlib:  extension "GLX" missing on display ":0.0".
beryl: Root visual is not a GL visual
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
rex@rex-desktop:~$ 

so what is happening here

---

