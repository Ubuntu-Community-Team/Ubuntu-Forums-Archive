---
title: "Nvidia Xorg.conf"
date: 2008-05-05
forum: General Help
---

### Post by Robbyx on 2008-05-05
Does this look right to you for a dual monitor setup? I can not get the nvidia-config program to set the monitor on the right to be relative to the one on the left.

I have also lost the ability to close or drag windows with the mouse. The buttons have gone.

> # Removed Option "metamodes" "CRT: 1280x1024 +0+0, DFP: nvidia-auto-select +1280+0; CRT: 1024x768 +0+0, DFP: nvidia-auto-select +1024+0; CRT: 832x624 +0+0, DFP: nvidia-auto-select +832+0; CRT: 800x600 +0+0, DFP: nvidia-auto-select +800+0; CRT: 640x480 +0+0, DFP: nvidia-auto-select +640+0"
# Removed Option "metamodes" "CRT: 1280x1024 +1280+0, DFP: nvidia-auto-select +0+0; CRT: 1024x768 +1280+0, DFP: nvidia-auto-select +0+0; CRT: 832x624 +1280+0, DFP: nvidia-auto-select +0+0; CRT: 800x600 +1280+0, DFP: nvidia-auto-select +0+0; CRT: 640x480 +1280+0, DFP: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: nvidia-auto-select +1280+0, DFP: nvidia-auto-select +0+0; CRT: 1024x768 +1280+0, DFP: nvidia-auto-select +0+0; CRT: 832x624 +1280+0, DFP: nvidia-auto-select +0+0; CRT: 800x600 +1280+0, DFP: nvidia-auto-select +0+0; CRT: 640x480 +1280+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Robin

---

