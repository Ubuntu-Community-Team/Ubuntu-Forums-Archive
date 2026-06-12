---
title: "Synaptics Touchpad driver not loaded anymore"
date: 2014-07-23
forum: General Help
---

### Post by astronos2007 on 2014-07-23
Hello, guys!

I am having a big problem here with my Xubuntu 14.04 64bit. Recently I noticed that the touchpad acted strange, as the right edge scroll doesn't work anymore, and the cursor moves veeeeery slowly. I did a bit of research and found out that it may be a problem with the Synaptics Touchpad driver. But when I type "synclient" in the terminal, it shows me:

```

"skynet@skynet-Aspire-V3-772G:~$ synclient
Couldn't find synaptics properties. No synaptics driver loaded?"

```

My xorg.conf file is:

```

Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection


Section "Device"
    Identifier "intel"
    Driver "modesetting"
    BusID "PCI:0@0:2:0"
EndSection


Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection


Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:1@0:0:0"
    Option "ConstrainCursor" "off"
EndSection


Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
EndSection

```

"xinput" in terminal shows the following:

```

skynet@skynet-Aspire-V3-772G:~$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Synaptics TouchPad                     id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=10    [slave  keyboard (3)]
    &#8627; HD WebCam                                   id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; Acer WMI hotkeys                            id=14    [slave  keyboard (3)]

```

I have googled a lot trying to figure it out, but none of the solutions I came into helped. Trying to manually edit the xorg.conf file by adding the synaptics input section code (found it on Google) didn't do a thing. Purging and then reinstalling the xorg-xserver-input-synaptics package also did nothing.

Could you please help me bring my touchpad back to its original state? I can't use it anymore, properly. Thank you!

---

