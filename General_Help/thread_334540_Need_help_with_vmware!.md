---
title: "Need help with vmware!"
date: 2007-01-09
forum: General Help
---

### Post by 0xDEFACE on 2007-01-09
Hello, mates!

Need help with VMWARE!

I installed vmware-server, corrected symbolic links and etc...
but when i try start it:
$ sudo vmware
i have read next notifications:

VMWARE_LD_LIBRARY_PATH is already set, but it will be overriden.
VMWARE_LD_PRELOAD is already set, but it will be overriden.
VMWARE_PANGO_RC_FILE is already set, but it will be overriden.
VMWARE_GDK_PIXBUF_MODULE_FILE is already set, but it will be overriden.
VMWARE_GTK_IM_MODULE_FILE is already set, but it will be overriden.
VMWARE_FONTCONFIG_PATH is already set, but it will be overriden.
VMWARE_GTK2_RC_FILES is already set, but it will be overriden.
VMWARE_GTK_PATH is already set, but it will be overriden.
VMWARE_LD_LIBRARY_PATH is already set, but it will be overriden.
VMWARE_LD_PRELOAD is already set, but it will be overriden.
VMWARE_PANGO_RC_FILE is already set, but it will be overriden.
VMWARE_GDK_PIXBUF_MODULE_FILE is already set, but it will be overriden.
VMWARE_GTK_IM_MODULE_FILE is already set, but it will be overriden.
VMWARE_FONTCONFIG_PATH is already set, but it will be overriden.
VMWARE_GTK2_RC_FILES is already set, but it will be overriden.
VMWARE_GTK_PATH is already set, but it will be overriden.

the notifications are always repeated and me system works very slow... and nothing occurs :-k

---

### Post by maniacmusician on 2007-01-09
...why are you running vmware with sudo? I've never tried it, but that could be the source of the problem? it may be trying to reconfigure the settings for root instead of for normal users and that could be screwing it up *just a theory*

---

### Post by 0xDEFACE on 2007-01-09
It doesn't influence in any way...
When i try start vmware under usual user (without sudo), i get the same errors (notifications)...

---

### Post by 0xDEFACE on 2007-01-10
hehe i found alternate a decision of the problem ^)

i downloaded another version of vmware-server (already .deb and not .rpm :))
i got it here:
[http://download3.vmware.com/software/vmserver/VMware-server-1.0.1-29996.tar.gz](http://download3.vmware.com/software/vmserver/VMware-server-1.0.1-29996.tar.gz)
And i installed linux headers files though:

$ sudo apt-get install linux-headers-`uname -r`

After installing, next folder has been created:
/usr/src/linux-headers-2.6.17-10/

When i started vmware-config.pl and when there were questions are sort of GCC and vmmon kernel module (don't know exactly ^^), i selected path like above, after that configure script started compiling of a this modul :) Thus, my vmware has been installed successfully!

However the story has not ended...
Further i try to run vmware i have read next text:

/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)

But nothing occurs... just only my system very brakes and i yet don't know what problem is... ](*,)

---

### Post by murlock on 2007-01-14
You can check in  /tmp/vmware-{username]/ the log...

With ubuntu 6.6 all was ok on my computer and after upgraded to 6.10, vmware doesn't start... because there was two libdbus libraries :

```

apt-get remove libdbus.1.2

```

---

