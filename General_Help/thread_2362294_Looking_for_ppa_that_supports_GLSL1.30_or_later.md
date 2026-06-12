---
title: "Looking for ppa that supports GLSL1.30 or later"
date: 2017-05-26
forum: General Help
---

### Post by desconocido on 2017-05-26
I am trying to run Stellarium on Ubuntu 16.04.

But it says that it needs GLSL (GL Shading Language) 1.30 or later (and OpenGL 2.1 or later).

The standard install is no good.

I looked at the list of ppas (and guessed that I should search for "mesa")
[https://launchpad.net/ubuntu/+ppas?name_filter=mesa]("https://launchpad.net/ubuntu/+ppas?name_filter=mesa")

That gives me 210 possibilities.

I have tried
```
sudo add-apt-repository ppa:oibaf/graphics-drivers

```and
```
sudo add-apt-repository ppa:ubuntu-x-swat/updates

```
but they don't have the version I need of GLSL.

Does anyone know of a ppa that supports GLSL 1.3?

---

### Post by steeldriver on 2017-05-26
Hmm - how did you determine that the standard installation is "no good"? here's what I get on my 16.04 box:

```

$ DISPLAY=:0 glxinfo | grep -i version
server glx version string: 1.4
client glx version string: 1.4
GLX version: 1.4
    Version: 12.0.6
    Max core profile version: 3.3
    Max compat profile version: 3.0
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.0
OpenGL core profile version string: 3.3 (Core Profile) Mesa 12.0.6
OpenGL core profile shading language version string: 3.30
**OpenGL version string: 3.0 Mesa 12.0.6**
OpenGL shading language version string: 1.30
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 12.0.6
**OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00**

```

(you may need to install the mesa-utils package to get glxinfo)

---

### Post by monkeybrain20122 on 2017-05-26
> **desconocido said:**
> I am trying to run Stellarium on Ubuntu 16.04.

But it says that it needs GLSL (GL Shading Language) 1.30 or later (and OpenGL 2.1 or later).

The standard install is no good.

I looked at the list of ppas (and guessed that I should search for "mesa")
[https://launchpad.net/ubuntu/+ppas?name_filter=mesa](https://launchpad.net/ubuntu/+ppas?name_filter=mesa)

That gives me 210 possibilities.

I have tried
```
sudo add-apt-repository ppa:oibaf/graphics-drivers

```and
```
sudo add-apt-repository ppa:ubuntu-x-swat/updates

```
but they don't have the version I need of GLSL.

Does anyone know of a ppa that supports GLSL 1.3?


What is your graphic card? If it is too old the hardware just doesn't support OpenGL 2.1 or later newer drivers won't help

---

### Post by desconocido on 2017-05-27
> **steeldriver said:**
> Hmm - how did you determine that the standard installation is "no good"? here's what I get on my 16.04 box:


And this is mine:


```
$ glxinfo | grep "OpenGL"
OpenGL vendor string: Intel Open Source Technology Center
OpenGL renderer string: Mesa DRI Intel(R) 945GM x86/MMX/SSE2
OpenGL version string: 1.4 Mesa 12.0.6
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 2.0 Mesa 12.0.6
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 1.0.16
OpenGL ES profile extensions:
```

---

### Post by desconocido on 2017-05-27
> **monkeybrain20122 said:**
> What is your graphic card? If it is too old the hardware just doesn't support OpenGL 2.1 or later newer drivers won't help

I am considering installing Ubuntu Mate 16.04 on a variety of machines, so I am trying it out on an old laptop first.

This is a Gateway ML6226b with 1 MB of RAM and
Intel® Graphics Media Accelerator 950
The processor is a Celeron 520 running at 1.60 GHz.

The install went fine and I have brought it up to date with Software Updater.

Running from the terminal as
LIBGL_ALWAYS_SOFTWARE=1 stellarium
works, but slowly, a bit more slowly than I care for.

---

### Post by mc4man on 2017-05-27
> **desconocido said:**
> I am considering installing Ubuntu Mate 16.04 on a variety of machines, so I am trying it out on an old laptop first.

This is a Gateway ML6226b with 1 MB of RAM and
Intel® Graphics Media Accelerator 950
The processor is a Celeron 520 running at 1.60 GHz.

The install went fine and I have brought it up to date with Software Updater.

Running from the terminal as
LIBGL_ALWAYS_SOFTWARE=1 stellarium
works, but slowly, a bit more slowly than I care for.
That hardware only supports OpenGL 1.4, no software is going to change that. So what you see as far as performance now is as good as it'll get

---

### Post by desconocido on 2017-05-27
> **mc4man said:**
> That hardware only supports OpenGL 1.4, no software is going to change that. So what you see as far as performance now is as good as it'll get
OK. My main laptop is a dual core
```
AMD E1-1200 APU with Radeon(tm) HD Graphics × 2
``` 
What's my chances of running it on that?

---

### Post by desconocido on 2017-05-31
> **desconocido said:**
> OK. My main laptop is a dual core
```
AMD E1-1200 APU with Radeon(tm) HD Graphics × 2
``` 
What's my chances of running it on that?

I tried it. It works and is just fast enough.

It's not as fast or smooth as the old version of Stellarium I was running on Ubuntu 12.04 on this machine.

---

