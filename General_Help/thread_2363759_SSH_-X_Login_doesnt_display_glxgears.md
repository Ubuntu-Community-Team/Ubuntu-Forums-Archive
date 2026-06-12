---
title: "SSH -X Login doesnt display glxgears"
date: 2017-06-14
forum: General Help
---

### Post by ashkanrafiee on 2017-06-14
Hi All,
I have a remote machine running Ubuntu 16.04 on it. The machine has the following graphic card

```
sudo lspci | grep VGA
01:04.0 VGA compatible controller: Matrox Electronics Systems Ltd. MGA G200eW WPCM450 (rev 0a)
```

I have already configured Xorg on t and when I am working directly on the machine everything works just fine and I can run any graphic application (such as glxgears) without any error. 

However, when I "ssh -X " to it from my laptop (again running Ubuntu 16.04 on it as well) the graphic applications do not work. For example when I run "glxgears" I get the following errors:

```
libGL: screen 0 does not appear to be DRI2 capable
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
libGL: Can't open configuration file /home/hpc64/.drirc: No such file or directory.
libGL: Can't open configuration file /home/hpc64/.drirc: No such file or directory.
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Value in failed request:  0x0
  Serial number of failed request:  35
  Current serial number in output stream:  37
```

I have already set "ForwardX11Trusted yes" in /etc/ssh/ssh_config without any success.

Here is also my xorg.conf

```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    #DisplaySize      340   270    # mm
    Identifier   "Monitor0"
    VendorName   "PHL"
    ModelName    "Philips 170S"
    HorizSync    30.0 - 83.0
    VertRefresh  56.0 - 76.0
    Option        "DPMS"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "HWcursor"               # [<bool>]
        #Option     "PciRetry"               # [<bool>]
        #Option     "SyncOnGreen"            # [<bool>]
        #Option     "NoAccel"                # [<bool>]
        #Option     "ShowCache"              # [<bool>]
        #Option     "MGASDRAM"               # [<bool>]
        #Option     "ShadowFB"               # [<bool>]
        #Option     "UseFBDev"               # [<bool>]
        #Option     "ColorKey"               # <i>
        #Option     "SetMclk"                # <freq>
        #Option     "OverclockMem"           # [<bool>]
        #Option     "VideoKey"               # <i>
        #Option     "Rotate"                 # [<str>]
        #Option     "TexturedVideo"          # [<bool>]
        #Option     "Crtc2Half"              # [<bool>]
        #Option     "Crtc2Ram"               # <i>
        #Option     "Int10"                  # [<bool>]
        #Option     "AGPMode"                # <i>
        #Option     "AGPSize"                # <i>
        #Option     "DigitalScreen1"         # [<bool>]
        #Option     "DigitalScreen2"         # [<bool>]
        #Option     "TV"                     # [<bool>]
        #Option     "TVStandard"             # [<str>]
        #Option     "CableType"              # [<str>]
        #Option     "NoHal"                  # [<bool>]
        #Option     "SwappedHead"            # [<bool>]
        #Option     "DRI"                    # [<bool>]
        #Option     "MergedFB"               # [<bool>]
        #Option     "Monitor2HSync"          # [<str>]
        #Option     "Monitor2VRefresh"       # [<str>]
        #Option     "Monitor2Position"       # [<str>]
        #Option     "MetaModes"              # [<str>]
        #Option     "OldDmaInit"             # [<bool>]
        #Option     "ForcePciDma"            # [<bool>]
        #Option     "AccelMethod"            # [<str>]
        #Option     "KVM"                    # [<bool>]
    Identifier  "Card0"
    Driver      "mga"
    BusID       "PCI:1:4:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "ServerFlags"
    Option "IndirectGLX" "on"
EndSection
```

I would highly appreciate any help/comments.

Cheers
Ash

---

### Post by efflandt on 2017-06-14
Just to see if your ForwardX11 is working properly, see if following run from an ssh session shows up in X on your client PC: **xclock**

I believe your problem is that you cannot forward X11 programs over ssh that write directly to graphics hardware. For example for me xclock works, but I get following results:```
~$ glxinfo
Name of display: localhost:10.0
Error: couldn't find RGB GLX visual or fbconfig

~$ glxgears
Error: couldn't get an RGB Double-buffered visual
```So don't expect to be able to run things remotely from an ssh session that write directly to hardware and have them display on your client computer. Although, doing the following in your ssh session may allow you to display glxinfo in your terminal or run glxgears on the server if your user is running X there and report results to your terminal:```
~$ export DISPLAY=:0
```

---

### Post by ashkanrafiee on 2017-06-14
thanks for the comments. here is the out put of "glxinfo"

```
name of display: localhost:10.0
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
X Error of failed request:  GLXBadContext
  Major opcode of failed request:  154 (GLX)
  Minor opcode of failed request:  6 (X_GLXIsDirect)
  Serial number of failed request:  48
  Current serial number in output stream:  47
```

shouldn't setting "ForwardX11Trusted yes" in ssh_config allow X11 forwarding?

---

### Post by efflandt on 2017-06-15
I have not used **ForwardX11Trusted yes**, but **ForwardX11 yes** in my ~/.ssh/config on my client forwards 2D apps, but not 3D apps (as in direct hardware access/acceleration, not necessarily stereo vision). And something I find strange is that when I ssh to a very old Linux PC with netscape, things like xclock work, but if I run netscape in an ssh session, instead of launching netscape on the server and displaying that on my client, it actually triggers firefox to launch on my client (related mozilla browsers).

Similarly you may have trouble playing videos remotely via ssh due to hardware acceleration. For example attempting to run **totem** via ssh results in: **Segmentation fault (core dumped)**. And the apport (crash report) dialog that comes up on the server says: **SegvReason > Reading NULL VMA**. If I run **totum** from terminal window on the server, it works fine.

---

