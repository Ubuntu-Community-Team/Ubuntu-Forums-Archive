---
title: "Problems with visual effects in Hardy"
date: 2008-05-06
forum: General Help
---

### Post by zieglerj on 2008-05-06
I upgraded to hardy when it was still beta and haven't been able to use any visual effects since. It's getting kind of worry some since hardy has been released now. Am I ever going to get my visual effects back? Every time I try to enable them my window boarders disappear. 
Is there a way to fix this? Would a clean install do anything?

---

### Post by macaholic on 2008-05-06
My guess is it is a driver issue, do you have your latest graphics driver installed and configured correctly?
Also, what is the output of compiz --replace in terminal?

---

### Post by ubuntwinkel on 2008-05-06
Installing package 'xserver-xgl' corrected this for me.

See my [[COLOR="Blue"]original post[/COLOR]]("http://ubuntuforums.org/showpost.php?p=4898803&postcount=3").

---

### Post by macaholic on 2008-05-06
> **ubuntwinkel said:**
> Installing package 'xserver-xgl' corrected this for me.

See my [[COLOR="Blue"]original post[/COLOR]]("http://ubuntuforums.org/showpost.php?p=4898803&postcount=3").
That won't necessarily fix it, and it would be quite unnecessary if he is using Nvidia, or a current ATI driver.

---

### Post by ubuntwinkel on 2008-05-06
> **macaholic said:**
> That won't necessarily fix it, and it would be quite unnecessary if he is using Nvidia, or a current ATI driver.

But I tried to fix this myself in a multitude of ways, and installing xserver-xgl did work for me, and I am using nVidia.

---

### Post by macaholic on 2008-05-06
My guess is that installing XGL reconfigured your Xorg.conf file in such a way that allowed it to work, I'm not saying that XGL is a bad thing, but in many cases it is unnecessary with nvidia.

---

### Post by Winsbreaker on 2008-05-06
I don't know if I'm in the right place, but I have Hardy installed on a T42 IBM laptop, and it is up and running, I have the propitiatory ATI driver for  my ATI Radeon 9600. The effects appear to be running, yet every 5-ish seconds when rendering a 3D environment, the screen flashes black and continues rendering. It doesn't stop playing for instance the 3D screen saver, it just blacks out for a second. Is there anyway to fix this?

Also, if this helps

> paul@paul-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON 9600/9700 Series
OpenGL version string: 2.1.7412 Release

paul@paul-laptop:~$ glxgears
9404 frames in 5.0 seconds = 1880.742 FPS
9457 frames in 5.0 seconds = 1891.357 FPS
9438 frames in 5.0 seconds = 1887.445 FPS
9409 frames in 5.0 seconds = 1880.400 FPS
9431 frames in 5.0 seconds = 1886.046 FPS
9418 frames in 5.0 seconds = 1883.428 FPS
9400 frames in 5.0 seconds = 1879.847 FPS
9443 frames in 5.0 seconds = 1888.430 FPS
9389 frames in 5.0 seconds = 1877.779 FPS
9356 frames in 5.0 seconds = 1871.140 FPS

paul@paul-laptop:~$ 


Please help, I'm fairly new to Ubuntu and would like to stay here. Thanks.

---

### Post by zieglerj on 2008-05-07
Thanks guys. I am running a nvida. I'm working on trying XGL because unnecessary or not right now I've tried about everything else. 

I'll let you know how it goes in a sec.

---

### Post by zieglerj on 2008-05-07
Hey, on another topic, is there a reason why my synapic package manager would quit connecting to the internet. I'm connected through a crossover cable network using a wireless connection from my laptop which runs XP. Everything else is running fine as far as connection speed but all of my synaptic programs slowed down so far that they usually time out.

---

### Post by zieglerj on 2008-05-07
OK, I've run into a little trouble here. xserver-xgl wont install. Here's what I get:

fenguin@fenguin:~$ sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsdl-ttf2.0-0 fb-music-high libgettext-ruby1.8 libsdl-console
  libsdl-gfx1.2-4 libsdl-net1.2 libsdl-perl amaya-data libsmpeg0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libglitz-glx1 libglitz1
The following NEW packages will be installed:
  libglitz-glx1 libglitz1 xserver-xgl
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 2142kB of archives.
After this operation, 5595kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libglitz1 0.5.6-1
  504 Gateway Time-out [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe libglitz-glx1 0.5.6-1
  504 Gateway Time-out [IP: 91.189.88.46 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy/universe xserver-xgl 1:1.1.99.1~git20080115-0ubuntu1
  504 Gateway Time-out [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/g/glitz/libglitz1_0.5.6-1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/glitz/libglitz1_0.5.6-1_amd64.deb)  504 Gateway Time-out [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/g/glitz/libglitz-glx1_0.5.6-1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/g/glitz/libglitz-glx1_0.5.6-1_amd64.deb)  504 Gateway Time-out [IP: 91.189.88.46 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/x/xserver-xgl/xserver-xgl_1.1.99.1~git20080115-0ubuntu1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/universe/x/xserver-xgl/xserver-xgl_1.1.99.1~git20080115-0ubuntu1_amd64.deb)  504 Gateway Time-out [IP: 91.189.88.46 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by zieglerj on 2008-05-07
O.k. I got xserver-xgl installed and it didn't work. I still have no boarders on my windows when visual effects are turned on.

---

### Post by zieglerj on 2008-05-07
In answer to your original question Macaholic, I'm pretty sure I have my latest driver installed. I'm using a restricted driver that ubuntu recommended. I'm not quite sure how to configure it so I can't say if it's configured correctly.

---

### Post by zieglerj on 2008-05-07
I've got it. I installed xserver-xgl. Then re-installed compiz. Then installed emerald and selected a theme for it. Then I had to double click window decorations in compiz and select it that way. Then my visual effects started working again.

---

### Post by ubuntwinkel on 2008-05-08
@zieglerj: Glad it works now.  I didn't need emerald for mine.  I even thought I didn't really need xgl; I was tending to agree with macaddict, that xgl *appeared* to fix my problem, by reconfiguring my xserver, and that reconfiguring was all I really needed, not xgl.  

So, I decided to remove xgl and see if all is well.  Nope.  I uninstalled xgl and window decorations disappeared.  I don't know why it is necessary for compiz to work--it is not a prerequisite for anything on my system.  And having xgl installed seems to make my screensaver lock-up after a while.  But it is definitely necessary for window decorations to work in compiz on my system.

---

### Post by JonathanSchroeder on 2008-05-08
Ok, I also recently upgraded to Hardy, and my problem is similar but still different.  While upgrading to hardy, i noticed that one of the things it did after the restart failed.  I have no idea which that one was, but now, I can only run my computer in low graphics mode, which means no visual effects whatsoever, and a small screen.  I havea Nvidia GeForce 7600GT graphics card, with the latest restricted driver in use.  However, if i try and access nvidia-settings, it tells me to run nvidia-xconfig as root.  This leaves me with this message: 
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

which doesn't help me at all.  Any ideas?

---

### Post by ubuntwinkel on 2008-05-08
> **JonathanSchroeder said:**
> Ok, I also recently upgraded to Hardy, and my problem is similar but still different.  While upgrading to hardy, i noticed that one of the things it did after the restart failed.  I have no idea which that one was, but now, I can only run my computer in low graphics mode, which means no visual effects whatsoever, and a small screen.  I havea Nvidia GeForce 7600GT graphics card, with the latest restricted driver in use.  However, if i try and access nvidia-settings, it tells me to run nvidia-xconfig as root.  This leaves me with this message: 
Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

which doesn't help me at all.  Any ideas?

Jonathan, did you restart X (Control-Alt-Backspace) after running nvidia-xconfig?

---

### Post by JonathanSchroeder on 2008-05-08
Yeah, I did, just like it said to.  No change.

---

