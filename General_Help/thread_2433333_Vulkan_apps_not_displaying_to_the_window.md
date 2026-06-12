---
title: "Vulkan apps not displaying to the window"
date: 2019-12-17
forum: General Help
---

### Post by rendoir on 2019-12-17
[COLOR=#1A1A1B][FONT=&amp]Hi!
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]I don't know if it was an update or a package I installed but all Vulkan applications are no longer working. OpenGL apps are working though.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]I'm using Ubuntu 18.04 with Gnome 3. I have a GTX 950M and I've changed between multiple graphics drivers in 'Sofware & Updates', 'Additional Drivers' tab. I've tried different open source drivers, like nvidia-driver-430 / 440 / 410 and proprietary 435. None worked.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]
In apps that use GLFW 3.3 (an API for the window system) I get this error:
[/FONT][/COLOR]
    X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
    Major opcode of failed request:  149 ()
    Minor opcode of failed request:  4
    Resource id in failed request:  0x220000d
    Serial number of failed request:  179
    Current serial number in output stream:  184
[COLOR=#1A1A1B][FONT=&amp]
Others that natively create and manage the window through XCB simply don't display anything (maybe due to error handling). Offscreen Vulkan rendering is working. I know this because some of the apps use it and display logs.
The windowing system (with GLFW3 at least) is working in OpenGL apps. However, in Vulkan the window opens but it remains black or crashes with the above error.
The crash occurs when I try to poll events for example. If I comment it out, the display remains black but doesn't crash.
[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]I remember that lately I've installed some packages for a program I wanted to run, like sld2, qt5, and maybe others that I don't remember. I've since purged them.[/FONT][/COLOR]
[COLOR=#1A1A1B][FONT=&amp]I honestly have no idea what could be wrong. If you have any ideas please share or if you need more info I can provide, but please keep in mind that I'm a begginer when it comes to messing with Linux.

I've tried these common workarounds but they didn't work:
In /etc/environment add:
QT_X11_NO_MITSHM=1
LIBOVERLAY_SCROLLBAR=0

I've also tried using proprietary driver 435 but it didn't work.

Thank you for reading :)[/FONT][/COLOR]

---

### Post by rendoir on 2019-12-22
I hate bumping but some days have passed and I can't fix it.

---

### Post by rendoir on 2019-12-28
> **rendoir said:**
> I hate bumping but some days have passed and I can't fix it.
^

---

