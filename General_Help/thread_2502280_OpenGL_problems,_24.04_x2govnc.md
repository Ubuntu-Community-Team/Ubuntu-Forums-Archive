---
title: "OpenGL problems, 24.04 x2go/vnc"
date: 2024-11-08
forum: General Help
---

### Post by jeffberrymrc on 2024-11-08
Good morning,

We're building a compute cluster using Dell rackmounts and ubuntu 24.04.  Generally, the install is going well, but OpenGL is not.

The machines are multi-user, and users can connect using x2go (preferred) or vnc in order to get graphical logins.  Our previous cluster was running CentOS and the OpenGL worked a treat, however on these new machines I get the dreaded 'Error: couldn't get an RGB,, Double-buffered visual' from glxgears, and glxinfo spits out:
[FONT=courier new]   name of display: :50
   Error: couldn't find RGB GLX visual or fbconfig[/FONT]

From an x2go session:

inxi -F shows this:
[FONT=courier new]Graphics:
  Device-1: Matrox Systems G200eR2 driver: mgag200 v: kernel
  Display: server: X.Org v: 0.0 driver: X: loaded: modesetting gpu: mgag200
    resolution: 1456x902~60Hz
  API: EGL v: 1.5 drivers: swrast platforms: x11,surfaceless,device
  API: OpenGL v: 4.5 vendor: mesa v: 24.0.9-0ubuntu0.2 note: incomplete
    (EGL sourced) renderer: llvmpipe (LLVM 17.0.6 256 bits)


[FONT=arial]Which suggests that the mesa drivers might be at fault, and the X.org v: of 0.0 looks suspicious.[/FONT][/FONT]

A vnc session to same machine gives different data (although still fails to work)
[FONT=courier new]Graphics:
  Device-1: Matrox Systems G200eR2 driver: mgag200 v: kernel
  Display: server: X.Org v: 1.21.1.11 driver: X: loaded: modesetting gpu: mgag200
    s-res: 1024x768
  API: EGL v: 1.5 drivers: swrast platforms: x11,surfaceless,device
  API: OpenGL v: 4.5 vendor: mesa v: 24.0.9-0ubuntu0.2 note: incomplete
    (EGL sourced) renderer: llvmpipe (LLVM 17.0.6 256 bits)

[FONT=arial]The difference is in the Display line as one would expect.  I've had a look at the mesa drivers and the dependencies look alright (from 'apt depends mesa-common-dev')  It feels like I might be missing something obvious, but ...
in any case, just for completeness:
6.8.0-48-generic #48-Ubuntu SMP PREEMPT_DYNAMIC
PRETTY_NAME="Ubuntu 24.04.1 LTS"
NAME="Ubuntu"
VERSION_ID="24.04"
VERSION="24.04.1 LTS (Noble Numbat)"
VERSION_CODENAME=noble
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=noble
LOGO=ubuntu-logo

Any pointers will be gratefully accepted.

Jeff, MRC-CBSU


 [/FONT]
[/FONT]

---

### Post by Yellow Pasque on 2024-11-08
Matrox doesn't have a 3D driver for Linux nowadays. Mesa removed it a long time ago ( [https://www.phoronix.com/news/OTg0Mg](https://www.phoronix.com/news/OTg0Mg) ). Even if it did have a driver, I'm not sure the hardware even supported OpenGL 2.x, so that would be almost useless nowadays.

---

### Post by jeffberrymrc on 2024-11-11
Thanks for that!   Very useful.   We've got OpenGL running on Matrox hardware on our existing (CentOS 7) cluster but only with OpenGL 2, so are we going to have to backlevel our OpenGL or is there a workaround that you know of?  (eg third party drivers we could use instead of the Matrox)

---

### Post by Yellow Pasque on 2024-11-11
I'm not aware of any special drivers for Matrox. If it was me, I'd get something old/cheap like a RadeonHD 6450. Chips like the G200eR2 are just there for troubleshooting headless systems; not for 3D.

---

### Post by jeffberrymrc on 2024-11-12
These are headless systems, but we do have people  doing some visualisation on them - I'll have to have a think.   And  you've given me much to think about, thanks again.

---

### Post by jeffberrymrc on 2024-11-15
Following up - we don't need a lot of heavy graphics, and in the past we've run using software rendering - eg swrast.  That should work for us again, but it's proving trickier to implement than I had hoped.

In any case, that's probably a new topic.  I just wanted to provide a bit of a summary in case someone else wanders into this thread.

---

