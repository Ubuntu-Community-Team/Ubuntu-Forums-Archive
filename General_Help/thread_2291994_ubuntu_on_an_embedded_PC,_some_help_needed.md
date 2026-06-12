---
title: "ubuntu on an embedded PC, some help needed"
date: 2015-08-24
forum: General Help
---

### Post by wonxega on 2015-08-24
Hello everyone.
I've installed Ubuntu 15.04 on a single board PC (Gizmo 2) which is meant to sit inside a custom device case, run an OpenGL program.

For this I'll need to do few things:

1) Not start the desktop, but run the OpenGL program on startup which is the only program which should ever be running. How can I set up this?

2) Would be nice to disable the Ubuntu boot logo, or even better, control when the projector starts receiving HDMI signal. I'm sure the first thing is possible. But is the second possible to do? I'd like the projector to start displaying something after the OpenGL program has started. Otherwise I would probably need to add a mechanical shutter to block the projection for some time which isn't ideal...

3) Disable any kind of OS or included program notifications. The device needs Ubuntu just to start running the Panda3D library program, any interference might result in not working properly. This includes any "OS has restarted after some unexpected crash" or similar messages. How can all this be disabled?

One more thing, I'll need an Arduino Nano for controlling a hacked pico projector from my program via Serial. For that I need to specify the baud rate and PORT the Arduino i connected to. I hope Ubuntu works the same way as Windows and as long as the Arduino is connected to the same port, the PORT index won't change.

---

