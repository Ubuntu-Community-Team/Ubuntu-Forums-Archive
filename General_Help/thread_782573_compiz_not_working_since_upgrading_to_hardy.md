---
title: "compiz not working since upgrading to hardy?"
date: 2008-05-05
forum: General Help
---

### Post by cutout33 on 2008-05-05
Hello all,

It took much to enable compiz on gutsy with ATI radeon on my Fujitsu Siemens laptop...
and after upgrading to hardy online without problems it just don't work???

ATI is working good
running 

```
glxinfo | grep ATI
```

gives

```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 2400
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, 
    GL_ATI_fragment_shader, GL_ATI_meminfo, GL_ATI_separate_stencil, 
    GL_ATI_texture_compression_3dc, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
```

and running 

```
compiz --replace
```


gives 

```
/home/fadi/.config/compiz/compiz-manager: 1: compiz-manager: not found
/home/fadi/.config/compiz/compiz-manager: 1: compiz-manager: not found

```

please help.

---

### Post by theheadlessrabbit on 2008-05-05
i have the same problem.

here is what i get:
```

Kyle@kyle-laptop:~$ glxinfo | grep ATI

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
    GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, GL_ATI_fragment_shader, 
    GL_ATI_meminfo, GL_ATI_separate_stencil, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 

```

```

kyle@kyle-laptop:~$ compiz --replace


compiz (core) - Fatal: No composite extension

```

---

### Post by vikasvishnu on 2008-05-05
Have you tried re-installing Compiz? Just use Synaptic Manager under System > Administration. There select the Compiz packages and mark them for re-installation. Once done, restart your X (Ctrl + Alt + Backspace). 

-:Vikas:-

> **cutout33 said:**
> Hello all,

It took much to enable compiz on gutsy with ATI radeon on my Fujitsu Siemens laptop...
and after upgrading to hardy online without problems it just don't work???

ATI is working good
running 

```
glxinfo | grep ATI
```

gives

```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 2400
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_envmap_bumpmap, 
    GL_ATI_fragment_shader, GL_ATI_meminfo, GL_ATI_separate_stencil, 
    GL_ATI_texture_compression_3dc, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_float, GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
```

and running 

```
compiz --replace
```


gives 

```
/home/fadi/.config/compiz/compiz-manager: 1: compiz-manager: not found
/home/fadi/.config/compiz/compiz-manager: 1: compiz-manager: not found

```

please help.

---

### Post by cutout33 on 2008-05-05
it didn't work I reinstalled them it gave me the 
same msg

```
/home/fadi/.config/compiz/compiz-manager: 1: compiz-manager: not found
```
:confused:

---

### Post by vikasvishnu on 2008-05-05
> **cutout33 said:**
> it didn't work I reinstalled them it gave me the 
same msg

```
/home/fadi/.config/compiz/compiz-manager: 1: compiz-manager: not found
```
:confused:

Hmm, have you checked if there is any packages called compiz-manager? You can check this under Synaptic. I know about 'compizconfig-settings-manager' (ccsm) but I am not sure if its the one required. Just try installing them and see if that solves your issue.

Vikas

---

### Post by cutout33 on 2008-05-05
nop, there is no package called compiz manager...

---

### Post by peakshysteria on 2008-05-05
I had Compiz working very smooth out of the box on my new 8.0 Hardy Heron (64 bit). But once I tried to enable the ATI driver it all got bad. Lost my resolution and the desktop became slow and sluggish. Then I reverted back to the MESA driver. And got my resolution back. But lost Compiz and Tv out. I would really like to have the fantastic Compiz back again. I'm taking a break from the ATI hell anyway :)

 glxinfo | grep ATI gives me:

    GL_ATI_draw_buffers, GL_ATI_texture_env_combine3, 
    GL_ATI_texture_mirror_once, GL_ATIX_texture_env_combine3,

compiz --replace gives me:

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

If i try to enable Compiz via the appearance and preferences menu I'm promted to enable the restricted driver. Which I know will break my setup. I'm sure the restricted driver wasn't installed as default when I did the install of Hardy.

What am I missing?? :confused:

---

### Post by Zorael on 2008-05-05
I can't help with the ATI bit, but to *ensure* that your compiz installation reflects the packages on the repositories, you need to pop up Software Sources and disable any third-party repos, and then find the compiz packages in Synaptic and tag them for **complete removal**. Merely uninstalling them often does not do the trick.

Terminal command (assumes third-party repos disabled):
```
$ sudo aptitude purge ~ncompiz ~nberyl ~nemerald ~nlibdeco
$ sudo aptitude update
$ sudo aptitude clean
$ sudo aptitude install compiz compizconfig-settings-manager emerald
```

---

### Post by peakshysteria on 2008-05-05
> **Zorael said:**
> I can't help with the ATI bit, but to *ensure* that your compiz installation reflects the packages on the repositories, you need to pop up Software Sources and disable any third-party repos, and then find the compiz packages in Synaptic and tag them for **complete removal**. Merely uninstalling them often does not do the trick.

Terminal command (assumes third-party repos disabled):
```
$ sudo aptitude purge ~ncompiz ~nberyl ~nemerald ~nlibdeco
$ sudo aptitude update
$ sudo aptitude clean
$ sudo aptitude install compiz compizconfig-settings-manager emerald
```


Okey. Will this remove and reinstall Compiz configuration settings manager as well? Or do i need to make additional steps to remove it? Or can I leave it alone?

---

### Post by cutout33 on 2008-05-05
> **Zorael said:**
> I can't help with the ATI bit, but to *ensure* that your compiz installation reflects the packages on the repositories, you need to pop up Software Sources and disable any third-party repos, and then find the compiz packages in Synaptic and tag them for **complete removal**. Merely uninstalling them often does not do the trick.

Terminal command (assumes third-party repos disabled):
```
$ sudo aptitude purge ~ncompiz ~nberyl ~nemerald ~nlibdeco
$ sudo aptitude update
$ sudo aptitude clean
$ sudo aptitude install compiz compizconfig-settings-manager emerald
```

it didn't work for me :confused:

---

### Post by cutout33 on 2008-05-05
I found a post in launchpad says to run the following command
```
 echo SKIP_CHECKS="yes" >> ~/.config/compiz/compiz-manager
```

now running 
```

compiz --replace
 
```

gives 

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:94c9 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 406: /usr/local/bin/compiz: not found
```

what can i do now??

---

### Post by Perpetual on 2008-05-05
It is mostly likely [this]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/201330").    Which I see is marked as "Will Not Fix".

There are work arounds as noted in the bug report.  I found this one to be the easiset..

[i]Chad Bernier wrote on 2008-04-11: (permalink)

i guess this isn't ready quite yet. I updated my compiz again and it stopped working. It took me a few minutes to figure it out. I first though it had to do with my new version of awn. this time i took an even easier fix. i went into /usr/bin/compiz, went to the laptop detect portion, and changed return 1 to return 0. hahaha, it can still check but ignore the result. Open source and scripts rule.[/i]

---

### Post by cutout33 on 2008-05-05
now running 
```

compiz --replace
 
```

gives 

```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:94c9 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (8192): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz: 406: /usr/local/bin/compiz: not found
```

the same even I changed return to 0????

---

### Post by vicky1984 on 2008-05-05
try editing /usr/bin/compiz and changing the path for compiz to /usr/local/bin/compiz.real instead of /usr/local/bin/compiz

---

### Post by cutout33 on 2008-05-05
if anyone reached the same place I was in just try editing /usr/bin/compiz by putting
this block insted the one you got

```
COMPIZ_BIN_PATH="/usr/bin/" # For window decorators and compiz
PLUGIN_PATH="/usr/lib/compiz/"
GLXINFO="/usr/bin/glxinfo"
KWIN="/usr/bin/kwin"
METACITY="/usr/bin/metacity"
COMPIZ_NAME="compiz.real" # Final name for compiz (compiz.real)

# For Xgl LD_PRELOAD
LIBGL_NVIDIA="/usr/lib/nvidia/libGL.so.1.2.xlibmesa"
LIBGL_FGLRX="/usr/lib/fglrx/libGL.so.1.2.xlibmesa"

# Minimum amount of memory (in kilo bytes) that nVidia cards need
# to be allowed to start
# Set to 262144 to require 256MB
NVIDIA_MEMORY="65536" # 64MB
NVIDIA_SETTINGS="nvidia-settings" # Assume it's in the path by default

# For detecting what driver is in use, the + is for one or more /'s
XORG_DRIVER_PATH="/usr/lib/xorg/modules/drivers/+"

FALLBACKWM="${METACITY}"
FALLBACKWM_OPTIONS="--replace $@"

# Driver whitelist
WHITELIST="fglrx nvidia intel ati radeon i810"

# blacklist based on the pci ids
# See http://wiki.compiz-fusion.org/Hardware/Blacklist for details
#T=" 1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12" # intel 965
T="$T 8086:2972" # i965 (x3000)
#T="$T 1002:3152 1002:3150 1002:5462 1002:5653 " # ati X300 X600,X600 X700
BLACKLIST_PCIIDS="$T"
unset T
```

it worked for me :guitar:

---

