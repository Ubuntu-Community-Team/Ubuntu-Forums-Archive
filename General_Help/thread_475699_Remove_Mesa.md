---
title: "Remove Mesa"
date: 2007-06-16
forum: General Help
---

### Post by ForzaItalia250 on 2007-06-16
Somehow I ended up installing this mesa stuff while trying to solve another problem (see [http://ubuntuforums.org/showthread.php?t=475582](http://ubuntuforums.org/showthread.php?t=475582))

Now while running Beryl, which I had doen previously just fine by inputing

LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/bin/beryl-manager

I get this message

ERROR: ld.so: object '/usr/lib/fglrx/libGL.so.1.2.xlibmesa' from LD_PRELOAD cannot be preloaded: ignored.

(repeated)

I can turn on Beryl manually, but it lags my computer and all the effects are messed up.

Can someone please help me to uninstall this mesa thing that's causing the problem?

---

### Post by ForzaItalia250 on 2007-06-16
This on a different forum helped me turn mesa off as a default driver

"try this 
sudo apt-get remove linux-restricted-modules-$(uname -r)
sudo apt-get remove xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig -initial
sudo aticonfig -overlay-type=XV
ctrl+alt+backspace
if you run fglrxinfo now and get something like
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY FireGL V5000
OpenGL version string: 2.0.6334 (8.34.8)
this is good. now reboot
if you run fglrxinfo and get mesa stuff you may be missing a symbolic link
I had the same problem.

sudo gedit /etc/default/linux-restricted-modules-common
make sure that fglrx is not disabled
sudo apt-get remove linux-restricted-modules-$(uname -r)
sudo apt-get remove xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driver-fglrx
sudo mkdir -p /usr/X11R6/lib/modules/dri 
sudo ln -s /usr/lib/dri/fglrx_dri.so /usr/X11R6/lib/modules/dri
sudo depmod -a
sudo aticonfig -initial
sudo aticonfig -overlay-type=XV

then try the ctr alt backspace check fglrxinfo
if thats good reboot and check it again hopefully i helped"

---

### Post by guixmax on 2008-05-02
Hi Forzaitalia,
I did as you suggest, ant it seem to works.
But when I restart the system, the fglrxinfo return again mesa indirect rendering.

Can you helm me??

Ciao

---

### Post by guixmax on 2008-05-05
I solved by commenting 

DISABLED_MODULES="fglrx"

in the /etc/default/linux-restricted-modules-common file.

---

