---
title: "[Live Usb] gbm is searching for dri drivers on one machine,on the other boots fine?"
date: 2016-11-13
forum: General Help
---

### Post by s-byczkowski on 2016-11-13
I have this live usb with ubuntu 16.04. I have two laptops both with nvidia gtx980m identical graphics and sligtly diffrent intel skylake mobos, well they almost identical except for some two onboard devices. Laptops are Asus G752vy and Asus G751jy.
On G751jy this live usb boots without any problem, on the G752vy I get this error when Xorg starts,Xorg is on autodetect, there is no xorg.conf:
```
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
gbm: failed to open any drivers (search paths /usr/lib/x86_64-linux-gnu/dri:${ORIGIN}/dri/:/usr/lib/dri)
gbm: Last dlopen error: /usr/lib/dri/nouveau_dri.so: cannot open shared object file: No such file or directory
failed to load driver: nouveau
gbm: failed to open any drivers (search paths /usr/lib/x86_64-linux-gnu/dri:${ORIGIN}/dri/:/usr/lib/dri)
gbm: Last dlopen error: /usr/lib/dri/kms_swrast_dri.so: cannot open shared object file: No such file or directory
failed to load driver: kms_swrast
gbm: failed to open any drivers (search paths /usr/lib/x86_64-linux-gnu/dri:${ORIGIN}/dri/:/usr/lib/dri)
gbm: Last dlopen error: /usr/lib/dri/swrast_dri.so: cannot open shared object file: No such file or directory
failed to load swrast driver
failed to load module : /usr/lib/x86_64-linux-gnu/gbm/gbm_gallium_drm.so: cannot open shared object file: No such file or directory
couldn't get display device
(EE) BUG: triggered 'if (axnum >= dev->valuator->numAxes)'
(EE) BUG: ../../Xi/exevents.c:2087 in InitValuatorAxisStruct()
(EE)
```
I have doublechecked and there are no "/usr/lib/x86_64-linux-gnu/dri" or "usr/lib/dri" or "/usr/lib/x86_64-linux-gnu/gbm/" present, nor there are nouveau_dri.so,kms_swrast_dri.so,swrast_dri.so,gbm_gallium_drm.so to be found anywhere in the live usb:confused:
 Why is it searching for those files on G752vy when it does not need them on G751jy and boots on it fine? The two laptops have the same graphic card.](*,)
The drivers are present in "/usr/lib/xorg/modules/drivers". I can see here nouveau_drv.so,fbdev_drv.so,mga_drv.so and others, but there are no dri drivers which seem to be needed, for some reason, for the G752vy. Why?:-k
I just checked and live usb boots fine on my two desktops, why does it fail on G752vy then:confused:

---

