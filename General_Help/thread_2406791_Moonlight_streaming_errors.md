---
title: "Moonlight streaming errors"
date: 2018-11-25
forum: General Help
---

### Post by milesnorth on 2018-11-25
Attempted to install Moonlight streaming from flatpak.  Steam streaming works, but was hoping moonlight would be more efficient.

Moonlight run errors:
```
flatpak run com.moonlight_stream.Moonlight
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
00:00:00 - Qt Fatal: Could not initialize GLX
```

Setup:
```
Operating System: KDE neon 5.14
KDE Plasma Version: 5.14.3
Qt Version: 5.11.2
KDE Frameworks Version: 5.52.0
Kernel Version: 4.15.0-39-generic
OS Type: 64-bit
Processors: 4 × Intel® Core™2 Quad CPU Q6600 @ 2.40GHz
Memory: 3.9 GiB of RAM
NVidia drivers: 396.54.09 on NVidia 670
```

Cacophony of bash commands from second install attempt (multiple forums):
```
sudo add-apt-repository --remove ppa:alexlarsson/flatpak
sudo apt remove flatpak
sudo apt autoremove
sudo apt-get remove gnome-software-plugin-flatpak
sudo apt remove plasma-discover-flatpak-backend
sudo apt-get purge flatpak*
sudo apt install plasma-discover-flatpak-backend
sudo apt-get update
sudo apt-get upgrade
flatpak install flathub com.moonlight_stream.Moonlight
flatpak run com.moonlight_stream.Moonlight
flatpak --version
flatpak run --command=sh com.moonlight_stream.Moonlight -c export
flatpak update
sudo add-apt-repository ppa:jonathonf/ffmpeg-4
sudo apt-get update
sudo apt-get install libavcodec-dev libavutil-dev
flatpak run com.moonlight_stream.Moonlight
nvidia-smi
flatpak remote-ls flathub | grep nvidia
flatpak install flathub org.freedesktop.Platform.GL.nvidia-396-54
flatpak install flathub org.freedesktop.Platform.GL32.nvidia-396-54
flatpak run com.moonlight_stream.Moonlight
```

Reached or passed a point of diminished returns, advice is appreciated.

Kurt

---

### Post by T.J. on 2018-11-28
Assuming you mean Moonlight the game streaming solution, and not the replacement for Sliverlight - it appears that you do not have either the proper GLX library installed, or your Nvidia driver is using a different one.  Unfortunately, the Nvidia Linux driver does not use the standard Mesa GL library, so you will have to go over the dependencies carefully.

---

### Post by milesnorth on 2018-12-01
> **T.J. said:**
> Assuming you mean Moonlight the game streaming solution, and not the replacement for Sliverlight - it appears that you do not have either the proper GLX library installed, or your Nvidia driver is using a different one.  Unfortunately, the Nvidia Linux driver does not use the standard Mesa GL library, so you will have to go over the dependencies carefully.
Had a 7.0 shaker yesterday.  That'll wake you up.

Not much of a debugger but if I purge the NVidia driver and reboot, then the Moonlight game streaming program starts (albeit with a GUI you can see at a 100 ft).  Reinstalling NVidia drivers leads to a nicer GUI but the same Moonlight error as listed above.

I'm not sure how to tell if libGL.so.1 is pointing correctly??

```
$ sudo ldconfig -p | grep -i gl.so

        libwayland-egl.so.1 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libwayland-egl.so.1
        libftgl.so.2 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libftgl.so.2
        libQt5OpenGL.so.5 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libQt5OpenGL.so.5
        libQtOpenGL.so.4 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libQtOpenGL.so.4
        libQtOpenGL.so (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libQtOpenGL.so
        libOpenGL.so.0 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libOpenGL.so.0
        libOpenGL.so (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libOpenGL.so
        libGL.so.1 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libGL.so.1
        libGL.so.1 (libc6) => /usr/lib/i386-linux-gnu/libGL.so.1
        libGL.so (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libGL.so
        libEGL.so.1 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libEGL.so.1
        libEGL.so (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libEGL.so

```

---

### Post by milesnorth on 2018-12-01
> **milesnorth said:**
> Had a 7.0 shaker yesterday.  That'll wake you up.

Not much of a debugger but if I purge the NVidia driver and reboot, then the Moonlight game streaming program starts (albeit with a GUI you can see at a 100 ft).  Reinstalling NVidia drivers leads to a nicer GUI but the same Moonlight error as listed above.

I'm not sure how to tell if libGL.so.1 is pointing correctly??

```
$ sudo ldconfig -p | grep -i gl.so

        libwayland-egl.so.1 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libwayland-egl.so.1
        libftgl.so.2 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libftgl.so.2
        libQt5OpenGL.so.5 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libQt5OpenGL.so.5
        libQtOpenGL.so.4 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libQtOpenGL.so.4
        libQtOpenGL.so (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libQtOpenGL.so
        libOpenGL.so.0 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libOpenGL.so.0
        libOpenGL.so (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libOpenGL.so
        libGL.so.1 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libGL.so.1
        libGL.so.1 (libc6) => /usr/lib/i386-linux-gnu/libGL.so.1
        libGL.so (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libGL.so
        libEGL.so.1 (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libEGL.so.1
        libEGL.so (libc6,x86-64) => /usr/lib/x86_64-linux-gnu/libEGL.so

```$ LIBGL_DEBUG=verbose flatpak run com.moonlight_stream.Moonlight
libGL: screen 0 does not appear to be DRI2 capable
libGL: OpenDriver: trying /lib/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /lib/dri/swrast_dri.so
libGL: Can't open configuration file /home/theatre/.drirc: No such file or directory.
libGL: Can't open configuration file /home/theatre/.drirc: No such file or directory.
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
00:00:00 - Qt Fatal: Could not initialize GLX

edit:
Just found a debug command using glxgears.  Does this output help?

```
$ LIBGL_DEBUG=verbose flatpak run com.moonlight_stream.Moonlight
libGL: screen 0 does not appear to be DRI2 capable
libGL: OpenDriver: trying /lib/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /lib/dri/swrast_dri.so
libGL: Can't open configuration file /home/theatre/.drirc: No such file or directory.
libGL: Can't open configuration file /home/theatre/.drirc: No such file or directory.
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
00:00:00 - Qt Fatal: Could not initialize GLX
```

---

