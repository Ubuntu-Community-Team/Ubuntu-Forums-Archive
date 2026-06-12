---
title: "matplotlib crashes on a remote virtual ubuntu machine"
date: 2024-01-23
forum: General Help
---

### Post by centguy2 on 2024-01-23
My python script runs on a virtual ubuntu OS was OK until yesterday. 
Both the host and the virtual machine are Ubuntu and have been upgraded to the lastest version of 22.04

I believe it started when I did the last apt update; apt upgrade.

It was triggered even by a matplotlib plot on the remote system.
I can only by doing a temporary fix by doing this on the remote system.

export QT_DEBUG_PLUGINS=1

Now the error message:
> 
python 1-plot.py
debug1: client_input_channel_open: ctype x11 rchan 3 win 65536 max 16384
debug1: client_request_x11: request from 127.0.0.1 40052
debug1: channel 1: new [x11]
debug1: confirm x11
debug1: channel 1: FORCE input drain
debug1: channel 1: free: x11, nchannels 2
debug1: client_input_channel_open: ctype x11 rchan 3 win 65536 max 16384
debug1: client_request_x11: request from 127.0.0.1 40068
debug1: channel 1: new [x11]
debug1: confirm x11
debug1: channel 1: FORCE input drain
debug1: channel 1: free: x11, nchannels 2
debug1: client_input_channel_open: ctype x11 rchan 3 win 65536 max 16384
debug1: client_request_x11: request from 127.0.0.1 40078
debug1: channel 1: new [x11]
debug1: confirm x11
debug1: channel 1: FORCE input drain
debug1: channel 1: free: x11, nchannels 2
qt.qpa.plugin: Could not load the Qt platform plugin "xcb" in "" even though it was found.
This application failed to start because no Qt platform plugin could be initialized. Reinstalling the application may fix this problem.
 
Available platform plugins are: eglfs, linuxfb, minimal, minimalegl, offscreen, vnc, wayland-egl, wayland, wayland-xcomposite-egl, wayland-xcomposite-glx, webgl, xcb.




The python run was OK before. Now, the python script crash on the remote system whenever it comes to the first matplotlib command plt.subplots()

---

### Post by centguy2 on 2024-01-23
some digging :

export QT_DEBUG_PLUGINS=1

Got keys from plugin meta data ("xcb")
QFactoryLoader::QFactoryLoader() checking directory path "/usr/bin/platforms" ...
Cannot load library /usr/local/lib/python3.10/dist-packages/PyQt5/Qt5/plugins/platforms/libqxcb.so: (libxcb-icccm.so.4: cannot open shared object file: No such file or directory)
QLibraryPrivate::loadPlugin failed on "/usr/local/lib/python3.10/dist-packages/PyQt5/Qt5/plugins/platforms/libqxcb.so" : "Cannot load library /usr/local/lib/python3.10/dist-packages/PyQt5/Qt5/plugins/platforms/libqxcb.so: (libxcb-icccm.so.4: cannot open shared object file: No such file or directory)"
qt.qpa.plugin: Could not load the Qt platform plugin "xcb" in "" even though it was found.
This application failed to start because no Qt platform plugin could be initialized. Reinstalling the application may fix this problem.

---

