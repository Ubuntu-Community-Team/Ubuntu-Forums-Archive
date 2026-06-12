---
title: "Trying to install Trusty HWE - impossible without losing Wine, nvidia-331, zsnes"
date: 2014-07-16
forum: General Help
---

### Post by james_mcl on 2014-07-16
After looking at a lot of threads, I try using this command line to circumvent the dependency issues that a lot of people have recently encountered when trying to upgrade to the Trusty HWE in Precise:

```

sudo apt-get install --install-recommends linux-generic-lts-trusty libgl1-mesa-glx-lts-trusty linux-image-generic-lts-trusty xserver-xorg-lts-trusty libglapi-mesa-lts-trusty xserver-xorg-video-glamoregl-lts-trusty xserver-xorg-video-ati-lts-trusty xserver-xorg-input-all-lts-trusty xserver-xorg-video-all-lts-trusty libglapi-mesa-lts-trusty libgl1-mesa-dri-lts-trusty x11-xserver-utils-lts-trusty

```

Among the packages this will apparently remove are:

ia32-libs
ia32-libs-multiarch:i386
nvidia-331
wine
wine1.4
wine1.4-amd64
wine1.4-common
wine1.4-i386:i386
zsnes:i386

There are no replacement packages offered for these.

Does anyone know of a way to use the Trusty HWE X stack, kernel, etc. in Precide without losing these?

---

