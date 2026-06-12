---
title: "X resolution from TTY"
date: 2014-04-06
forum: General Help
---

### Post by KubaV on 2014-04-06
Hello,
I am trying to change X resolution from TTY via XRandr, but with no success. Is it possible? From X the same command works.
```
xrandr -d :0 -q
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 16384 x 16384
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1280x960       75.0     60.0  
   1152x864       75.0     60.0  
   1280x768       75.0     60.0  
   1280x720       75.0     60.0  
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     60.3  
   640x480        75.0     72.8     59.9  
CRT1 disconnected (normal left inverted right x axis y axis)
```
XRandr in X returns this:
```
xrandr -d :0 --output DFP2 --mode 1280x1024 -r 60 --verbose
screen 0: 1280x1024 336x269 mm  96.57dpi
crtc 0:    1280x1024   60.0 +0+0 "DFP2"
```
XRandr in TTY returns this:
```
xrandr -d :0 --output DFP2 --mode 1280x1024 -r 60 --verbose
crtc 0: disabled
xrandr: Configure crtc 0 failed
crtc 0: disabled
crtc 1: disabled
crtc 2: disabled
screen 0: revert
crtc 0: revert
crtc 1: revert
crtc 2: revert
```
EDIT: I use AMD Radeon HD 6450 + beta driver 14.3 + Ubuntu 12.04.1 kernel 3.2.0-generic-pae

---

### Post by KubaV on 2014-04-12
Can please somebody help me :(

---

