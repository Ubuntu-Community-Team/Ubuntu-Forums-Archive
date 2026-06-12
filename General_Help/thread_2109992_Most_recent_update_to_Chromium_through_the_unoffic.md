---
title: "Most recent update to Chromium through the unofficial PPA is completely unusable"
date: 2013-01-29
forum: General Help
---

### Post by Stonecold1995 on 2013-01-29
The official Chromium PPA is no longer maintained, and the unofficial one (by Alex whatever) seems to also have stalled.  However, a short time ago the first update in a while came out.  However, it won't even start, it just exits with a segmentation fault.

```
alex@kubuntu:~$ chromium-browser
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct null not valid
Aborted (core dumped)
```And in case this helps:
```
alex@kubuntu:~$ ldd /usr/lib/chromium-browser/chromium-browser
        linux-vdso.so.1 =>  (0x00007fff5354a000)
        libX11.so.6 => /usr/lib/x86_64-linux-gnu/libX11.so.6 (0x00007fefa2f32000)
        libXrandr.so.2 => /usr/lib/x86_64-linux-gnu/libXrandr.so.2 (0x00007fefa2d28000)
        libXrender.so.1 => /usr/lib/x86_64-linux-gnu/libXrender.so.1 (0x00007fefa2b1d000)
        libXss.so.1 => /usr/lib/x86_64-linux-gnu/libXss.so.1 (0x00007fefa2919000)
        libXext.so.6 => /usr/lib/x86_64-linux-gnu/libXext.so.6 (0x00007fefa2707000)
        librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007fefa24fe000)
        libdl.so.2 => /lib/x86_64-linux-gnu/libdl.so.2 (0x00007fefa22fa000)
        libgobject-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0 (0x00007fefa20ab000)
        libglib-2.0.so.0 => /lib/x86_64-linux-gnu/libglib-2.0.so.0 (0x00007fefa1db3000)
        libgtk-x11-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgtk-x11-2.0.so.0 (0x00007fefa177a000)
        libgdk-x11-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgdk-x11-2.0.so.0 (0x00007fefa14c8000)
        libatk-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libatk-1.0.so.0 (0x00007fefa12a5000)
        libpangocairo-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libpangocairo-1.0.so.0 (0x00007fefa1099000)
        libgdk_pixbuf-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgdk_pixbuf-2.0.so.0 (0x00007fefa0e7a000)
        libcairo.so.2 => /usr/lib/x86_64-linux-gnu/libcairo.so.2 (0x00007fefa0b81000)
        libpango-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libpango-1.0.so.0 (0x00007fefa0938000)
        libfreetype.so.6 => /usr/lib/x86_64-linux-gnu/libfreetype.so.6 (0x00007fefa069c000)
        libfontconfig.so.1 => /usr/lib/x86_64-linux-gnu/libfontconfig.so.1 (0x00007fefa0461000)
        libnss3.so => /usr/lib/x86_64-linux-gnu/libnss3.so (0x00007fefa015a000)
        libnssutil3.so => /usr/lib/x86_64-linux-gnu/libnssutil3.so (0x00007fef9ff33000)
        libsmime3.so => /usr/lib/x86_64-linux-gnu/libsmime3.so (0x00007fef9fd0b000)
        libplc4.so => /usr/lib/x86_64-linux-gnu/libplc4.so (0x00007fef9fb06000)
        libnspr4.so => /usr/lib/x86_64-linux-gnu/libnspr4.so (0x00007fef9f8c7000)
        libgconf-2.so.4 => /usr/lib/x86_64-linux-gnu/libgconf-2.so.4 (0x00007fef9f698000)
        libdbus-1.so.3 => /lib/x86_64-linux-gnu/libdbus-1.so.3 (0x00007fef9f454000)
        libXcomposite.so.1 => /usr/lib/x86_64-linux-gnu/libXcomposite.so.1 (0x00007fef9f251000)
        libasound.so.2 => /usr/lib/x86_64-linux-gnu/libasound.so.2 (0x00007fef9ef66000)
        libXfixes.so.3 => /usr/lib/x86_64-linux-gnu/libXfixes.so.3 (0x00007fef9ed60000)
        libcups.so.2 => /usr/lib/x86_64-linux-gnu/libcups.so.2 (0x00007fef9eb00000)
        libgcrypt.so.11 => /lib/x86_64-linux-gnu/libgcrypt.so.11 (0x00007fef9e881000)
        libpthread.so.0 => /lib/x86_64-linux-gnu/libpthread.so.0 (0x00007fef9e664000)
        libbz2.so.1.0 => /lib/x86_64-linux-gnu/libbz2.so.1.0 (0x00007fef9e454000)
        libexpat.so.1 => /lib/x86_64-linux-gnu/libexpat.so.1 (0x00007fef9e22a000)
        libudev.so.0 => /lib/x86_64-linux-gnu/libudev.so.0 (0x00007fef9e01d000)
        libstdc++.so.6 => /usr/lib/x86_64-linux-gnu/libstdc++.so.6 (0x00007fef9dd1a000)
        libm.so.6 => /lib/x86_64-linux-gnu/libm.so.6 (0x00007fef9da1d000)
        libgcc_s.so.1 => /lib/x86_64-linux-gnu/libgcc_s.so.1 (0x00007fef9d807000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fef9d448000)
        libxcb.so.1 => /usr/lib/x86_64-linux-gnu/libxcb.so.1 (0x00007fef9d229000)
        /lib64/ld-linux-x86-64.so.2 (0x00007fefa85d7000)
        libffi.so.6 => /usr/lib/x86_64-linux-gnu/libffi.so.6 (0x00007fef9d021000)
        libpcre.so.3 => /lib/x86_64-linux-gnu/libpcre.so.3 (0x00007fef9cde3000)
        libgio-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgio-2.0.so.0 (0x00007fef9ca8e000)
        libpangoft2-1.0.so.0 => /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0 (0x00007fef9c863000)
        libXinerama.so.1 => /usr/lib/x86_64-linux-gnu/libXinerama.so.1 (0x00007fef9c65f000)
        libXi.so.6 => /usr/lib/x86_64-linux-gnu/libXi.so.6 (0x00007fef9c450000)
        libXcursor.so.1 => /usr/lib/x86_64-linux-gnu/libXcursor.so.1 (0x00007fef9c245000)
        libXdamage.so.1 => /usr/lib/x86_64-linux-gnu/libXdamage.so.1 (0x00007fef9c041000)
        libgmodule-2.0.so.0 => /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0 (0x00007fef9be3d000)
        libpixman-1.so.0 => /usr/lib/x86_64-linux-gnu/libpixman-1.so.0 (0x00007fef9bbb6000)
        libpng12.so.0 => /lib/x86_64-linux-gnu/libpng12.so.0 (0x00007fef9b990000)
        libxcb-shm.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-shm.so.0 (0x00007fef9b78d000)
        libxcb-render.so.0 => /usr/lib/x86_64-linux-gnu/libxcb-render.so.0 (0x00007fef9b582000)
        libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007fef9b36b000)
        libplds4.so => /usr/lib/x86_64-linux-gnu/libplds4.so (0x00007fef9b166000)
        libdbus-glib-1.so.2 => /usr/lib/x86_64-linux-gnu/libdbus-glib-1.so.2 (0x00007fef9af3f000)
        libgssapi_krb5.so.2 => /usr/lib/x86_64-linux-gnu/libgssapi_krb5.so.2 (0x00007fef9ad00000)
        libgnutls.so.26 => /usr/lib/x86_64-linux-gnu/libgnutls.so.26 (0x00007fef9aa44000)
        libavahi-common.so.3 => /usr/lib/x86_64-linux-gnu/libavahi-common.so.3 (0x00007fef9a838000)
        libavahi-client.so.3 => /usr/lib/x86_64-linux-gnu/libavahi-client.so.3 (0x00007fef9a626000)
        libgpg-error.so.0 => /lib/x86_64-linux-gnu/libgpg-error.so.0 (0x00007fef9a422000)
        libXau.so.6 => /usr/lib/x86_64-linux-gnu/libXau.so.6 (0x00007fef9a21d000)
        libXdmcp.so.6 => /usr/lib/x86_64-linux-gnu/libXdmcp.so.6 (0x00007fef9a017000)
        libselinux.so.1 => /lib/x86_64-linux-gnu/libselinux.so.1 (0x00007fef99df8000)
        libresolv.so.2 => /lib/x86_64-linux-gnu/libresolv.so.2 (0x00007fef99bdb000)
        libkrb5.so.3 => /usr/lib/x86_64-linux-gnu/libkrb5.so.3 (0x00007fef9990d000)
        libk5crypto.so.3 => /usr/lib/x86_64-linux-gnu/libk5crypto.so.3 (0x00007fef996e3000)
        libcom_err.so.2 => /lib/x86_64-linux-gnu/libcom_err.so.2 (0x00007fef994df000)
        libkrb5support.so.0 => /usr/lib/x86_64-linux-gnu/libkrb5support.so.0 (0x00007fef992d7000)
        libtasn1.so.3 => /usr/lib/x86_64-linux-gnu/libtasn1.so.3 (0x00007fef990c5000)
        libp11-kit.so.0 => /usr/lib/x86_64-linux-gnu/libp11-kit.so.0 (0x00007fef98eb1000)
        libkeyutils.so.1 => /lib/x86_64-linux-gnu/libkeyutils.so.1 (0x00007fef98cac000)
```

---

### Post by dino99 on 2013-01-29
that might be time to use ppa-purge, then reinstall chromium (or use something else :) )

---

### Post by Stonecold1995 on 2013-01-29
> **dino99 said:**
> that might be time to use ppa-purge, then reinstall chromium (or use something else :) )

Re-installing would give me a very, very out of date version and I don't want the security risks (the official PPA is never updated anymore).  And I've tried compiling Chromium from source, but it seems like a really round-about way of doing it (I have no idea why they make it so confusing...).

If an update came out and that's what broke this, wouldn't that be a sign that Alex whatever is maintaining the PPA again, and that an update may come out to fix it?

---

### Post by mparillo on 2013-01-29
Is the PPA version different from the 'regular' version I can install directly from Muon Software Center? There it looks to be version 22.

---

### Post by dino99 on 2013-01-29
why not using these recent ones ?

[https://launchpad.net/ubuntu/+source/chromium-browser](https://launchpad.net/ubuntu/+source/chromium-browser)

or change the ppa used:

[https://launchpad.net/~a-v-shkop/+archive/chromium-dev](https://launchpad.net/~a-v-shkop/+archive/chromium-dev)

---

### Post by NadirPoint on 2013-01-29
The Chromium update I installed last week from the normal Ubuntu repositories is  v23.0.1271.97.

Seems pretty stable, so I'm a Chromium user again.  I had switched to Firefox sometime last fall due to issues with the earlier version.  Those problems (slowness, hangs) seem to be resolved.

---

### Post by Stonecold1995 on 2013-01-30
Well, I found out what it is.  The update made a bunch of changes to the permissions Chromium requires, and my AppArmor profile was preventing it from starting.

---

