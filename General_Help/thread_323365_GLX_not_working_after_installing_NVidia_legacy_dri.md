---
title: "GLX not working after installing NVidia legacy driver"
date: 2006-12-22
forum: General Help
---

### Post by Antarctica on 2006-12-22
When I had Ubuntu Dapper, I used Automatix2 to install my graphics driver.  My card is quite old.  It's the nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15).  It uses the nvidia legacy drivers.  Automatix2 would install the correct drivers and GLX would work perfectly.

Now, on Ubuntu Edgy, GLX works right out of the box with the nv driver, but when I use Automatix2 to install the nvidia legacy driver, I cannot seem to get GLX to work.  I've tried glxinfo and glxgears.  Does anybody have a solution to my problem?

---

### Post by hashimoto on 2006-12-22
Same here. GL screen savers don't work and glxgears gives:

```
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't get an RGB, Double-buffered visual
```
Also, the .xsession-errors says:
```
(gnome-panel:5016): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -3 and height 24
Xlib:  extension "GLX" missing on display ":0.0".

(/usr/lib/gnome-screensaver/gnome-screensaver-gl-helper:5108): Gdk-CRITICAL **: gdk_x11_visual_get_xvisual: assertion `visual != NULL' failed
```

I had GL working OK earlier, but after a reinstall and Automatix2 this does not work anymore. Does it now install a new (and defunc?) version of nvidia driver? It's now 1.0-7184.

---

### Post by hashimoto on 2006-12-22
> **hashimoto said:**
> Same here. GL screen savers don't work 

OK got mine solved. I installed nvidia-glx  instead of the nvidia-glx-legacy and seems to run.

---

### Post by userek on 2006-12-22
> **hashimoto said:**
> OK got mine solved. I installed nvidia-glx  instead of the nvidia-glx-legacy and seems to run.

I don't know how in the world this works for you but it shouldn't since you are using diferent kernel module version and diverent glx, it just cannot work :). I had the similar problem getting glx to work on ubuntu 6.10. After tracking the problem i found out that 
there is complan in Xorg logfile that icannot load glx while the comosite is enabled(well i didn't enable it it seems its enable dby default). Anyway adding this line:
```

Option "AllowGLXWithComposite" "1"

```
in device section solved the problem for me.

---

### Post by Antarctica on 2006-12-22
> **userek said:**
> I don't know how in the world this works for you but it shouldn't since you are using diferent kernel module version and diverent glx, it just cannot work :). I had the similar problem getting glx to work on ubuntu 6.10. After tracking the problem i found out that 
there is complan in Xorg logfile that icannot load glx while the comosite is enabled(well i didn't enable it it seems its enable dby default). Anyway adding this line:
```

Option "AllowGLXWithComposite" "1"

```in device section solved the problem for me.
Okay, where do I add "AllowGLXWithComposite" "1" in xorg.conf?  Thanks btw.  Never mind.  I didn't read your post correctly.  Haha, device section.

---

### Post by userek on 2006-12-22
> **Antarctica said:**
> Okay, where do I add "AllowGLXWithComposite" "1" in xorg.conf?  Thanks btw.

Bellow the Driver "nvidia" line, but i don't know if you have the same problem i had.

btw. i also commented Load dri line in modules section and the last last 3 lines of the file that contained dri section, i don't know if that was nessesery but i remember that nvidia howto says tu comment load dri line.

---

### Post by Antarctica on 2006-12-22
Well, my problem's solved.  I wonder if my graphics card can support XGL and AIGLX now.

---

### Post by hashimoto on 2006-12-23
> **userek said:**
> I don't know how in the world this works for you but it shouldn't since you are using diferent kernel module version and diverent glx, it just cannot work :). 

Hey, don't ask me! I'm just a stupid user. I didn't know it was impossible so I just did it ;).

---

### Post by moopere on 2007-01-09
> **userek said:**
> I don't know how in the world this works for you but it shouldn't since you are using diferent kernel module version and diverent glx, it just cannot work :). I had the similar problem getting glx to work on ubuntu 6.10. After tracking the problem i found out that 
there is complan in Xorg logfile that icannot load glx while the comosite is enabled(well i didn't enable it it seems its enable dby default). Anyway adding this line:
```

Option "AllowGLXWithComposite" "1"

```
in device section solved the problem for me.

Thanks for the pointer.  Your suggestion has fixed up my problem.  For those wondering where it goes and how it should all look, see a section from my xorg.conf

```

Section "Device"
        Identifier      "nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        Option          "AllowGLXWithComposite" "On"

EndSection

```

Now, off to launchpad to report the bug - its present on both edgy & feisty so I'm guessing its not been reported.

Cheers, Craig

---

### Post by voided3 on 2007-01-17
Hello. I also have a Riva TNT2 64 in my computer and I added the Option "AllowGLXWithComposite" "1" line in xorg and now glxgears opens, but immediately freezes the computer, as does opening web pages with animation. I installed the nvidia-legacy driver with Automatix2 and I do get the nvidia splash screen. Any thoughts?

---

### Post by matrix on 2007-01-21
Hello,
It seems I have the same problem. I have the nvidia-legacy driver installed from repositories:
sudo apt-get install nvidia-glx-legacy 
Then
sudo nvidia-glx-config enable

Sudo modinfo nvidia gives:
filename:       /lib/modules/2.6.17-10-generic/volatile/nvidia.ko
license:        NVIDIA
alias:          char-major-195-*
vermagic:       2.6.17-10-generic SMP mod_unload 586 REGPARM gcc-4.1
depends:        agpgart,i2c-core
alias:          pci:v000010DEd*sv*sd*bc03sc00i00*
alias:          pci:v000010DEd*sv*sd*bc03sc02i00*
parm:           NVreg_PanelBrightnessLimits:int
parm:           NVreg_PanelPWMFrequency:int
parm:           NVreg_EnableBrightnessControl:int
parm:           NVreg_SaveVBios:int
parm:           NVreg_VbiosFromROM:int
parm:           NVreg_DetectPrimaryVga:int
parm:           NVreg_UseCPA:int
parm:           NVreg_RemapLimit:int
parm:           NVreg_RmLogonRC:int
parm:           NVreg_VideoEnhancement:int
parm:           NVreg_DevicesConnected:int
parm:           NVreg_FlatPanelMode:int
parm:           NVreg_ResmanDebugLevel:int
parm:           NVreg_DeviceFileMode:int
parm:           NVreg_DeviceFileGID:int
parm:           NVreg_DeviceFileUID:int
parm:           NVreg_ModifyDeviceFiles:int
parm:           NVreg_Mobile:int
parm:           NVreg_SoftEDIDs:int
parm:           NVreg_EnableAGPFW:int
parm:           NVreg_EnableAGPSBA:int
parm:           NVreg_NvAGP:int
parm:           NVreg_ReqAGPRate:int
parm:           NVreg_EnableALiAGP:int
parm:           NVreg_EnableVia4x:int
parm:           NVreg_VideoMemoryTypeOverride:int
parm:           nv_disable_pat:int


glxinfo | grep direct  command gives:
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
In DEVICE section (in xorg.conf) I have:
Option "RenderAccel" "true"
Option "AllowGLXWithComposite" "true"
and the new section at the bottom of the xorg,conf file:
Section "Extensions"
        Option "Composite" "Enable"
EndSection
Of course I changed the nv to nvidia ...
Xorg freezes after reboot.:(

---

### Post by alexfittyfives on 2007-02-01
matrix -

> Option "AllowGLXWithComposite" "true"

it might not help but I used

```
Option          "AllowGLXWithComposite" "1"
```

and it worked.

---

### Post by matrix on 2007-02-04
alexfittyfives -

Thanks for reply. 

I've changed this option. The same result,.. Xorg freezes after reboot.  The end of Xorg.O.log shows:
 
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "RenderAccel" "true"
(**) NVIDIA(0): Option "AllowGLXWithComposite" "1"
(**) NVIDIA(0): Enabling experimental RENDER acceleration
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.
Fatal server error:
no screens found

---

