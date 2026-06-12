---
title: "[SOLVED] ati/xgl+compiz crashes when maximizing windows"
date: 2008-06-08
forum: General Help
---

### Post by gizmo_the_greater on 2008-06-08
the situation

i've got a aticard in my host. lspci shows:

05:00.0 VGA compatible controller: ATI Technologies Inc R520 [Radeon X1800]
05:00.1 Display controller: ATI Technologies Inc R520 [Radeon X1800] (Secondary)

i've installed the prop-drivers fglrx

first i started with a single monitor using compiz, this worked quite well

it what not that easy to find a working way to get a big desktop with compiz to run, the 'bigdesktop'-feature was the answer

now i have a goodlooking desktop with wobbly windows, the nice cube, window-decoration ...

BUT THERE REMAINS TWO BIG PROBLEMS!!!!!!!!!

- EVERYTIME I TRY TO MAXIMIZE A WINDOW THE WINDOWMANAGER CRASHES! 

And there are some other problems to

- When the server crashes because of one of the upper problems and restarts to login the BigDesktop-Extension doesn't work. When i login i see two cloned screens, but on the login-screen i can move the mouse over to the second screen.

While starting normally the login is exactly in the middle of both screen, cutted in two peaces ... not when i restart it.

Here is my xorg.conf

```
Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "screen0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "ServerFlags"
        Option      "Xinerama" "true"
        #Option         "AIGLX"         "off"
EndSection

Section "InputDevice"
        Identifier  "Generic Keyboard"
        Driver      "kbd"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "de"
EndSection

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
EndSection

Section "Monitor"
        Identifier   "monitor0"
EndSection

Section "Monitor"
 #
        Identifier   "monitor1"
        VendorName   "Belinea"
        ModelName    "Belinea"
        HorizSync    30.0 - 81.0
        VertRefresh  50.0 - 160.0
        Gamma        1
EndSection

Section "Device"

#       Busid           "PCI:5:0:0"
        #Option "UseInternalAGPGART" "no"
        #Option "KernelModuleParm" "agplock=0"
        Identifier  "ATI_0"
        Driver      "fglrx"
        BoardName   "ati"
        Option      "DesktopSetup" "horizontal"
EndSection

Section "Device"

        #Option "UseInternalAGPGART" "no"
        #Option "KernelModuleParm" "agplock=0"
        Identifier  "ATI_1"
        Driver      "fglrx"
        BoardName   "ati"
        BusID       "PCI:5:0:1"
        Screen      1
EndSection

Section "Screen"
        Identifier "screen0"
        Device     "ATI_0"
        Monitor    "monitor0"
        DefaultDepth     24
        SubSection "Display"
#               Virtual   1600 1200
                Depth     24
                Modes    "1600x1200@50" "1280x800@75" "1024x768@85"
        EndSubSection
EndSection

Section "Screen"
 #
        Identifier "screen1"
        Device     "ATI_1"
        Monitor    "monitor1"
        DefaultDepth     24
        SubSection "Display"
                Virtual   1600 1200
                Depth     24
                Modes    "1600x1200@50" "1280x800@75" "1024x768@85"
        EndSubSection
EndSection

```

---

### Post by gizmo_the_greater on 2008-06-08
i think i've done it

SHIFT BACKSPACE

The thing with SHIFT+BACKSPACE was fairly easy

just created a .Xmodmap-File in my home with: 
keycode 22 = BackSpace BackSpace

what i'm still wondering is where my AT (for mailaddys) has gone??

ABOUT THE RESIZING

I've changed config in CompizConfig Manager in General Options

Under Display Settings i've disabled 'Detect Outputs' and configured the Outputs to 3200x1200+0+0 ... now i can resize windows, even when there occur some displayerrors, for example in firefox ...

---

### Post by gizmo_the_greater on 2008-06-08
even if i've set up keyboardlayout "de" in xorg it uses english layout within kde ... why ever i had to activate keyboardlayouts ...

---

