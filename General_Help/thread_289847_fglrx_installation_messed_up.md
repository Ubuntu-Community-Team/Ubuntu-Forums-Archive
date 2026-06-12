---
title: "fglrx installation messed up"
date: 2006-10-31
forum: General Help
---

### Post by meimato on 2006-10-31
I installed Edgy and tried several video card configurations (I've got a Mobility RADEON 9600).
I installed th fglrx driver in edgy repositories and acceleration worked fine; then I tried installing XGL following the Unofficial Ubuntu Guide (with no luck).
Then I removed all the packages for XGL, and from that moment 3D acceleration stopped working; I even tried to install the new ATI drivers (8.29.06), but here's my present situation:
- glxinfo show direct rendering: No
- fglrxinfo shows OpenGL vendor: Brian Paul
                  OpenGL renderer string: Mesa X11
                  OpenGL version string: 1.5 Mesa 6.5.1
Is there a way to reset my 3D acceleration? Thanks.

---

### Post by John.Michael.Kane on 2006-10-31
Have you tried ```
sudo dpkg-reconfigure xserver-xorg
```


Theres also this thread [http://ubuntuforums.org/showthread.php?t=235145&highlight=ati](http://ubuntuforums.org/showthread.php?t=235145&highlight=ati) which has info on script install of ati drivers

---

### Post by meimato on 2006-10-31
Yes, several ways.
As I said, after having tried XGL (and then removed it), I saw 3D acceleration was not working.
I made dpkg-reconfigure to go back to ati drivers, and then to go again to fglrx; then, I decided to install manually the newest ATI drivers, and again they install regularly but I have no accelerations...
Who the hell is this Brian Paul? :)

---

### Post by araz on 2007-01-04
I had the same problem witch solved by:
removing beryl repos
> sudo gedit /etc/apt/sources.list
sudo aptitude update

removed previously  downloaded .deb from cache
> sudo aptitude clean

and reinstalling the drivers from Ubuntu repos
> sudo aptitude reinstall xorg-driver-fglrx

---

### Post by jaimz on 2007-01-04
use the steps from here to get fglrx working properly
it's what I used to get mine running with the latest ATI drivers

[http://ubuntuforums.org/showthread.php?t=321766&highlight=fglrx+beryl+xgl]("http://ubuntuforums.org/showthread.php?t=321766&highlight=fglrx+beryl+xgl")

as for xgl use this, with beryl

[http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/XGL]("http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/XGL")

those are the ways I got my fglrx working with 3d acceleration on xgl with beryl

enjoy!

---

