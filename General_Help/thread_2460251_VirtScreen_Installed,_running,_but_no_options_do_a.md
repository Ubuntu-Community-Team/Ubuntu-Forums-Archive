---
title: "VirtScreen: Installed, running, but no options do anything"
date: 2021-04-05
forum: General Help
---

### Post by makem2 on 2021-04-05
I am attempting to use VirtScreen to connect to Samsung Tab A which is running a vnc client. I have installed x11vnc and configured as required.

When I select the VirtServe icon I have menu with 4 options:

1. Enable VirtScreen First

2. Enable Virtual Screen

3. Start VNC Server

4. Open VirtScreen

Start VNC Server (3) is greyed out. According to the x11vnc icon, it is running.

When I select (4) in the drop down menu VirScreen appears to crash. When I start it again and select entry (1) I get: 'No virtual screen name found' appearing in the icon drop down menu below (1)

The tablet vnc client bVNC Pro fails to connect with VirtScreen, attempting to get a handshake with a long error message.

I am unable to get the gui for VirtScreen to set anything up.

Has anyone got this working with Ubuntu 20.04?

---

### Post by TheFu on 2021-04-05
To connect from Linux to Android, I just use scrcpy.  There's a snap package to make it easy.
[https://snapcraft.io/scrcpy](https://snapcraft.io/scrcpy)
Much easier than all the VNC junk.  Are you trying to run an Ubuntu on Android inside a chroot?

---

### Post by makem2 on 2021-04-06
Thank you for that suggestion which I will investigate.

My reason for using the tablet is as follows:

I currently have to use Alt+ Tab to access two web pages I am referring to on a laptop. One, the one I propose to have on the tablet, will show the method of 'making' a project. The other, on my laptop, will show the 'manufacturing' of the 'project', avoiding the need for web page swapping on the laptop and easy ability to check the paused page on the tablet.

I can do this currently if I use two mice but would prefer to be able to slide from one view to another. What I require is the same ability I used to have in Windows where I could swap between my two monitors, effectively extending my desktop.

I do not want to mirror the tablet screen on the laptop which I can and have done using a USBC to USBC cable.

---

### Post by TheFu on 2021-04-06
I think I understand the purpose now.  You want to control 2 computers, each with a different "monitor", but connected to a single mouse and keyboard.  I have dual monitors on 1 of my Linux systems, and use a tool called Xinerama. I understand there's a new way, but guess my OS is too old.

Does **synergy** work on Android?  I think that's a tool that lets two computers, with 2 monitors be controlled by 1 mouse and 1 keyboard virtually.  Just tell synergy the tablet "monitor" is on the left or right of the computer monitor, then when you slide the mouse to the right ... it shows up on the tablet.  I think it is called synergy. [https://symless.com/synergy](https://symless.com/synergy)
Looks like there is an Android version [https://forums.symless.com/topic/5577-synergy-for-android-l-m-n-o/](https://forums.symless.com/topic/5577-synergy-for-android-l-m-n-o/)

Of course, program windows can't be dragged between the screens.

---

### Post by makem2 on 2021-04-06
Yes, I looked into Synergy and it does work on Android but it is not open source which was my goal.

VirtScreen is and I see it has worked on previous Linux versions apparently with little if any problem. It seems to be a change in 20.04 which cause it not to work and I am rather like a dog with a rag, so will continue to research why.

I have not yet tried running VirtScreen from the Terminal and I also need to look into whether it is a gfx problem with this machine, an XPS13-9300.

Thank you for taking the time to answer my post.

EDIT: Running VirtScreen from the terminal produces the below result which offers a possible solution route which is hopefully not beyond my abilities.

```

makem@XPS-13-9300:~$ virtscreen
libGL error: MESA-LOADER: failed to open iris (search paths /usr/lib/x86_64-linux-gnu/dri:\$${ORIGIN}/dri:/usr/lib/dri)
libGL error: failed to load driver: iris
libGL error: MESA-LOADER: failed to open iris (search paths /usr/lib/x86_64-linux-gnu/dri:\$${ORIGIN}/dri:/usr/lib/dri)
libGL error: failed to load driver: iris
libGL error: MESA-LOADER: failed to open swrast (search paths /usr/lib/x86_64-linux-gnu/dri:\$${ORIGIN}/dri:/usr/lib/dri)
libGL error: failed to load driver: swrast
QGLXContext: Failed to create dummy context
qml: Loader Status Changed. 1
Failed to create OpenGL context for format QSurfaceFormat(version 2.0, options QFlags<QSurfaceFormat::FormatOption>(), depthBufferSize 24, redBufferSize -1, greenBufferSize -1, blueBufferSize -1, alphaBufferSize -1, stencilBufferSize 8, samples -1, swapBehavior QSurfaceFormat::SwapBehavior(DoubleBuffer), swapInterval 1, colorSpace QSurfaceFormat::ColorSpace(DefaultColorSpace), profile  QSurfaceFormat::OpenGLContextProfile(NoProfile)) 
Aborted (core dumped)
makem@XPS-13-9300:~$

```

---

### Post by makem2 on 2021-04-06
Dell tell me that VirtScreen requires a Nvidea or AMD gfx card and the card I have is a Intel Corporation Iris Plus Graphics G7 (rev 07)

The error message says it cannot find the Iris driver which seems strange when it is running an Iris gfx card.

I'm afraid its looking like it will be beyond me.

Unless there is a Ubuntu Iris driver?

Ah! I may need Mesa.

[https://itsfoss.com/install-mesa-ubuntu/](https://itsfoss.com/install-mesa-ubuntu/)

EDIT: I have decided to post in Upgrades as it looks like it involves an upgrade to drivers and may involve a different kernel too.

---

