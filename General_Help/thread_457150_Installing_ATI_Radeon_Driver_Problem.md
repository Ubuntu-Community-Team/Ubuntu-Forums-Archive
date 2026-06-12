---
title: "Installing ATI Radeon Driver Problem"
date: 2007-05-28
forum: General Help
---

### Post by kimcheefreak17 on 2007-05-28
Hi, I'm having a problem when I try to install the driver. I'm using an ATI Radeon 9600 and I was advised to install the driver, so I went to do that. I got  ATI Proprietary Linux x86 Display Driver 8.36.5 , from their website, and followed the instructions correctly, but it won't launch the installer. I put in the terminal what they told me to, but that didn't work. Then, i put in * sh ati-driver-installer-8.36.5-x86.x86_64.run*, it looked like it was going to launch the installer, but then this showed up in the terminal: 

Detected configuration:
Architecture: i686 (32-bit)
X Server: X.Org 7.2.x

Detected version of X does not have a matching 'x720' directory
You may override the detected version using the following syntax:
     X_VERSION=<xdir> ./ati-driver-installer-<ver>-<arch>.run [--install]

The following values may be used for <xdir>:
    x430        XFree86 4.3.x
    x430_64a    XFree86 4.3.x 64-bit
    x680        X.Org 6.8.x
    x680_64a    X.Org 6.8.x 64-bit
    x690        X.Org 6.9.x
    x690_64a    X.Org 6.9.x 64-bit
    x700        X.Org 7.0.x
    x700_64a    X.Org 7.0.x 64-bit
    x710        X.Org 7.1.x
    x710_64a    X.Org 7.1.x 64-bit
Removing temporary directory: fglrx-install.Uj6902

Any help would be appreciated. Thanks!

---

### Post by Ek0nomik on 2007-05-28
Well, I know this isn't directly related to your current issue, but have you tried the drivers that Ubuntu will recognize and download for you?  I am quite sure your card is supported by the fglrx drivers.

If you go into System/Administration/Restricted Drivers, you should be able to install there.

---

### Post by kimcheefreak17 on 2007-05-28
Alright, I'll do that right now! Thanks!

---

### Post by strabes on 2007-05-28
Use the link in my signature.

---

