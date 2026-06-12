---
title: "VNC desktop sharing not working on ubuntu 15.04"
date: 2015-05-30
forum: General Help
---

### Post by dieter-erich on 2015-05-30
Hi,

   I just installed ubuntu 15.04 and am desperately trying to get desktop sharing (VNC) to work. I tried turbovnc (server/client) and tightvnc (server/client). In both cases, on connection, I get either a gray or a white screen but nothing else. I even tried vino. In this latter case I just get a security mismatch warning but no connection. I shoud mention that I successfully installed turbovnc/virtualgl (using the pre-release version 1.2.90 as this is the only one that should work with ubuntu) on a laptop running ubuntu 14.04 and a number of other PCs. I also did not see any problems with tightvnc on a Raspberry Pi. It seems to me that ubuntu 15.04 is the reason. I should mention that I have also installed gnome-flashback.

Thanks for help, D-E

---

### Post by steeldriver on 2015-05-30
If you use Vino, you will probably need to modify the default security settings - see this previous question (for 14.04, but I believe the situation is the same for 15.04)

[http://ubuntuforums.org/showthread.php?t=2233675](http://ubuntuforums.org/showthread.php?t=2233675)

Alternatively, you could use x11vnc (which is more commonly used on non-gnome systems).

In contrast, tightvnc/turbovnc are standalone VNC servers not 'desktop sharing' servers: by default they start a minimal X session and if you want a 'desktop' you will need to configure one via the ~/.vnc/xstartup file

---

### Post by dieter-erich on 2015-05-31
Hi Steeldriver, thanks for the hint. Unfortunately, I was not correct in calling it 'desktop sharing'. I rather want to have a new desktop on connecting to a remote and headless machine. So, vino will, in any case, not be useful. The only option seems to be tight- or turbo-vnc, and these give me the trouble with ubuntu 15.04!

---

### Post by QIII on 2015-05-31
Hello!

Is this remote, headless machine also "X-less", or does it have a DE or WM?  Were the other machines you mentioned connecting to the same remote machine?

---

### Post by dieter-erich on 2015-06-01
Hi,
   the 'headless' machine runs 'normal' Ubuntu 15.04 with everything including gnome-flashback. So, when I start it with screen, keyboard, and mouse physically attached it shows the usual gnome2 desktop. 

I want to connect to it from other linux machines to a desktop of my own. In fact, I usually connect via turbovncclient to display #1 or #2 or whatever parameter I have started turbovncserver with (i.e. 'turbovncserver :1' or :2). As I said, this works well when I connect to my laptops running ubuntu 14.04 but it does not on my PC running ubuntu 15.04. Since I know that turbovnc is somewhat problematic with ubuntu (e.g. only the pre-release version works) I also tried with tightvnc from the repository. However, I get essentially the same uniformly unresponsive coloured window without any panel! So, I strongly believe that it is due to ubuntu 15.04. But if so, what would be the solution?
Thanks, D-E

---

### Post by steeldriver on 2015-06-01
I'm confused about what remote session you are trying to run - you tagged the thread 'lubuntu' but in your post you mention Ubuntu and gnome-flashback

In my experience, VNC works best with lightweight desktops / plain window managers - I used to run XFCE4, then switched to LXDE in 14.04 because of apparent problems with xfsettingsd, then recently back to XFCE4.  In fact, the server that I use at work was upgraded a couple of weeks ago to 15.04 with tightvncserver version 1.3.10-0ubuntu1, and I didn't notice anything different (I am using the same ~/.vnc/xstartup since the server was originally build with 12.04). It is happily running an XFCE4 session right now. So I don't think there's an intrinsic problem with VNC on 15.04.

Perhaps if you could describe your setup / configuration in more detail?

---

### Post by dieter-erich on 2015-06-01
Hi steeldriver, thanks for your willingness to help! I am sorry for the confusion:

the machine I want to access via vnc is running ubuntu 15.04 with gnome-flashback installed (because I do not want all these desktop effects of Unity and also because TurboVNC is said to not run under Unity). I have installed TurboVNC and TightVNC on this machine. I am trying to access this machine from other PCs running Ubuntu or Lubuntu or Windows by using the respective viewers (i.e. either Turbovncviewer when I run TurboVNCserver or Thightvncviewer when I run Tightvncserver). The problem is that regardless from where I try to access I only get a black screen (Turbovnc) or a grey screen (Tightvnc) and no 'real' gnome desktop. As you state that TightVNC runs fine in your hands (on 15.04) my problems might be due to a faulty gnome-flashback installation (something missing???) on my 15.04 machine and not to the OS itself. Is there a way of finding out? At least when I have a screen physically connected to the machine the appearance of the desktop is completely normal.

---

### Post by dieter-erich on 2015-06-02
ONE MORE THING: I also copied xstartup.turbovnc from my laptop running Ubuntu 14.04 (where turbovnc is working) to my 15.04 PC (where it is not working) with the same negative result. So, I believe that it has something to do with my setup of gnome-flashback. But how to find out?

---

### Post by dieter-erich on 2015-06-05
The developer of turbovnc has posted a solution: do not use gnome-fallback but rather put :

1) install mate
2) put:

exec /usr/bin/mate-session
exit

on top of the xstartup.turbovnc file

mate is the continuation of gnome2

---

### Post by wizrddreams on 2015-06-28
Hey dieter-erich -- do you know if tightvnc works for running an Ubuntu 14.04 computer remotely via another Linux box (Mint 17.1)? Or is tightvnc really only meant for running a light desktop environment? (Like a Raspbian)

Do you have a xstartup file for tightvnc that might work for my situation? (Or maybe suggestions)

---

