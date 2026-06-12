---
title: "Xwindow connections from terminal?"
date: 2008-05-23
forum: General Help
---

### Post by BananaPeal on 2008-05-23
Hello,

This is my first post, after running Ubuntu 7.10 for about a day now. I was hoping for similar support for x11 windows as one would find in OsX but I think I'm abit disappointed. 

I don't know how to configure the xterminal window. After using the xterm command,  I was hoping to simply connect to my school servers and begin using software on them by using ssh. However, I tried to run something and I got the error that a display isn't specified and got the regular text-only prompt from the software that one would present when using any regular terminal to connect to it.

Any simple ideas on how to get around this? 

Thanks alot! And if there's better places to post my question or threads already answering it, please let me know. 

Thanks again,
Alex

---

### Post by bodhi.zazen on 2008-05-23
You need to start an x session first. 

What window manager do you have installed ? gnome, kde, xfce ???

None ?? If none and you want a minimal install you will need to install X.

---

### Post by unutbu on 2008-05-23
```
ssh -Y username@remote-computer
```

The -Y means "Enable trusted X11 forwarding".
For more info do `man ssh`.

---

### Post by BananaPeal on 2008-05-29
I'm using the regular gnome installed 7.10 version ... fyi. The -Y command worked like a charm. Now, if only comcast was fast enough in my area to allow it to work properly!

Thanks alot for your help. I'm still new to linux and don't quite know what is needed for a xwindow ... for instance it was confusing why the xterm command brought up a new terminal window that wouldn't  have the display set.  I'm not sure if I'll pick up these sorts of things through experience however, any suggestions on becoming more acclamated to the environment? I have all sorts of little quirks (like how do you get it to report the video driver version?!)  that I can't quite find answers to in the documentation... 

Thanks agian, sorry for the basicness of my problem.

---

### Post by unutbu on 2008-05-29
BananaPeal, welcome to Linux. I think you'll enjoy the ride.

> 
any suggestions on becoming more acclamated to the environment?

1) Play. I picked up most of what I know just by playing with Linux. Just try new things every day. Go to the gnome panel menu and try every option. 

2) Read. Read. Read. A long time ago I read Matt Welsh's Running Linux. It is a very nice book, but I must say you can probably find almost all the information in that book for free on the web (albeit scattered about). The best advice I found in that book (which is not repeated often on the web) is to keep a text file of all the commands you type as root, plus any interesting commands you come across -- sort of a diary about your computer. 

There is a wealth of great information at [http://www.tldp.org/](http://www.tldp.org/). There are howto's on ssh, encryption, learning BASH scripting, setting up a network, backing up your computer, etc.

3) Use Google. 

4) Use Ubuntuforums. The help here is fantastic. Ask lots of questions. For better or worse, the squeaky wheel does get the grease. Hanging around ubuntuforums can also help you discover software and resources you might not bump into on your own:

[cool apps you might not know about]("http://ubuntuforums.org/showthread.php?t=382137") 
[for a good laugh]("http://ubuntuforums.org/showthread.php?t=130985") 

Best of luck to you!

PS. For your specific question:

Here are two ways to find out your video driver version. (Substitute the name of your driver for nvidia).

```
08:41:18 atom@rest:~% grep -i nvidia /var/log/Xorg.0.log
<snip>
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
(II) NVIDIA dlloader X Driver  **100.14.19**  Wed Sep 12 14:14:20 PDT 2007
<snip>
08:51:44 atom@rest:~% dmesg | grep -i nvidia
[   27.211775] nvidia: module license 'NVIDIA' taints kernel.
[   27.463804] NVRM: loading NVIDIA UNIX x86 Kernel Module  **100.14.19**  Wed Sep 12 14:12:24 PDT 2007
```

You can also find out about your hardware by typing
```

sudo lshw

``` or clicking on the gnome panel menu: System>Preferences>Hardware Information.

In case you do not have an nvidia card, you can find out the name of your X video driver by looking in /etc/X11/xorg.conf. Try 

```
cat /etc/X11/xorg.conf | less
``` 
look for something like
```
Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

```

---

