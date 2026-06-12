---
title: "Unity dead. Can't revive."
date: 2013-04-11
forum: General Help
---

### Post by captainwithershins on 2013-04-11
I rebooted my Ubuntu and unity was gone as were the desktop icons. Reinstalled compiz icons came back, but still no unity. When I try to start it I get::~$ unity
compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
unity-panel-service: no process found
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
libGL error: failed to load driver: swrast
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
compiz (core) - Info: Starting plugin: opengl
libGL error: failed to load driver: swrast
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Info: Starting plugin: compiztoolbox
compiz (core) - Info: Loading plugin: decor
compiz (core) - Info: Starting plugin: decor
compiz (core) - Info: Loading plugin: resize
compiz (core) - Info: Starting plugin: resize
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: grid
compiz (core) - Info: Starting plugin: grid
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: widget
compiz (core) - Info: Starting plugin: widget
compiz (core) - Info: Loading plugin: move
compiz (core) - Info: Starting plugin: move
compiz (core) - Info: Loading plugin: wall
compiz (core) - Info: Starting plugin: wall
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Info: Starting plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: animation
compiz (core) - Info: Starting plugin: animation
compiz (core) - Info: Loading plugin: wobbly
compiz (core) - Info: Starting plugin: wobbly
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Info: Starting plugin: workarounds
compiz (core) - Info: Loading plugin: fade
compiz (core) - Info: Starting plugin: fade
compiz (core) - Info: Loading plugin: scale
compiz (core) - Info: Starting plugin: scale
compiz (core) - Info: Loading plugin: expo
compiz (core) - Info: Starting plugin: expo
compiz (expo) - Warn: failed to bind image to texture
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Info: Starting plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
compiz (core) - Info: Starting plugin: unityshell
compiz (unityshell) - Error: GL_ARB_vertex_buffer_object not supported

compiz (core) - Error: Plugin initScreen failed: unityshell
compiz (core) - Error: Failed to start plugin: unityshell
compiz (core) - Info: Unloading plugin: unityshell
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  3 (X_GetWindowAttributes)
  Resource id in failed request:  0x300016e
  Serial number of failed request:  9225
  Current serial number in output stream:  9226

Solutions?

---

### Post by blackbird34 on 2013-04-11
Have you used Unity before? part of that wall of text says "compiz (core) - Info: **Unity is not supported by your hardware**. Enabling software rendering instead (slow)."

What about installing an alternative desktop environment while you are doing day-to-day stuff, while you sort this out? (e.g. ```
 sudo apt-get install xfce4 
``` )

Secondly, did you enable a lot of plugins in the CompizConfig Settings Manager? Some are incompatible with each other, it occasionally causes problems, which is why the settings manager is not installed by default. 
You can probably restore unity to default settings by opening a command prompt with ALT+F2 and typing: ```
unity --reset
```.
If you want to have a go refreshing unity to see if you can get it started again before giving up, you can also try refreshing it with ALT+F2 and ```
unity --replace
```

---

### Post by sideburns on 2013-04-11
I use Compiz with Xfce, although on Fedora.  When you try to enable a plugin that conflicts with another one, the settings manager will warn you that there's a conflict, and that enabling this one will disable the other.  (It also lets you know when one plugin requires a second one to be enabled, and lets you decide if you want that.)

I'm not sure how the OP managed to get conflicting plugins enabled, but I agree with you that it might be what's causing the problem.  You may want to nuke ~/.compiz, which will remove all of your settings, then log out and back in.  This will set you up with the default configuration, which should work.  Once you're sure it's working, you can start to customize it again.

---

### Post by captainwithershins on 2013-04-11
I have a fairly new ATI video card and have always used unity with Ubuntu. I haven't enabled any plugins for months. I just rebooted. How exactly do I nuke ~/.compiz?

---

### Post by deadflowr on 2013-04-11
Try running
```
/usr/lib/nux/unity_support_test -p
```

Did you install the closed-source drivers by chance?
And if so, from where.

---

### Post by sideburns on 2013-04-11
If you can log in at a CLI, you can nuke all of your compiz settings one of two ways:

rm -rf ~/.compiz

will completely delete them.  However, you must be very careful to get that command exactly right because it's possible to delete your entire home directory if there's a space in the wrong place.  Or, much safer would be this:

mv ~/.compiz ~/.compiz.bad

This will simply rename the directory, and unless you're very comfortable with a CLI, it's the one I'd recommend.

---

### Post by captainwithershins on 2013-04-11
> **deadflowr said:**
> Try running
```
/usr/lib/nux/unity_support_test -p
```

Did you install the closed-source drivers by chance?
And if so, from where.

The original ATI drivers some weeks ago.

:~$ /usr/lib/nux/unity_support_test -p
libGL error: failed to load driver: swrast
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
OpenGL vendor string:   ATI Technologies Inc.
OpenGL renderer string: AMD Radeon HD 6700 Series 
OpenGL version string:  1.4 (2.1 (4.2.12002 Compatibility Profile Context 9.012))

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  no
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

Tried installing gnome shell and the same. It does not start and I'm left with a nice wallpaper and keyboard commands.

---

### Post by deadflowr on 2013-04-11
What do you mean by the original ATI drivers?

And also, what version of Ubuntu are you currently running?
This might help to resolve/understand the issue clearer.

---

### Post by captainwithershins on 2013-04-12
The ATI drivers from their website. Newest version.

EDIT: Fixed it! Downloaded the latest beta driver. and installed it.

---

