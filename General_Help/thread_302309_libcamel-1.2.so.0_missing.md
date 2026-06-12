---
title: "libcamel-1.2.so.0 missing"
date: 2006-11-18
forum: General Help
---

### Post by niels on 2006-11-18
I'm trying to run SyncEvolution to sync with ScheduleWorld, but I get the following errormessage:
```
niels@niels-laptop:~$ syncevolution 
syncevolution: error while loading shared libraries: libcamel-1.2.so.0: cannot open shared object file: No such file or directory
niels@niels-laptop:~$ 
```

I have libcamel-1.2-8 and libcamel-1.2-dev installed.

What's the problem and how do I solw it?

---

### Post by aerials on 2006-11-28
I just had the same problem. I guess the problem is, that edgy ships with libcamel-1.2.so.8, so my blind try was just creating a symlink in /usr/lib named libcamel-1.2.so.0 that points to the .8 library.

But after taking that step, syncevolution wants libssl.so.0.9.7 and libcrypto .so.0.9.7 while edgy has the 0.9.8 versions for both. Luckily I have vmware-server installed, which comes with these two libraries in the 0.9.7 version. So I just made symlinks for libssl.so.0.9.7 and libcrypto.so.0.9.7 in /usr/lib pointing to /usr/lib/vmware/lib/libssl.so.0.9.7/libssl.so.0.9.7 and /usr/lib/vmware/lib/libcrypto.so.0.9.7/libcrypto.so.0.9.7

I hope it works, my setup doesn't yet, but it seems to be a problem with the horde server I'm trying to sync with.

---

### Post by niels on 2006-11-29
> **aerials said:**
> I just had the same problem. I guess the problem is, that edgy ships with libcamel-1.2.so.8, so my blind try was just creating a symlink in /usr/lib named libcamel-1.2.so.0 that points to the .8 library.

But after taking that step, syncevolution wants libssl.so.0.9.7 and libcrypto .so.0.9.7 while edgy has the 0.9.8 versions for both. Luckily I have vmware-server installed, which comes with these two libraries in the 0.9.7 version. So I just made symlinks for libssl.so.0.9.7 and libcrypto.so.0.9.7 in /usr/lib pointing to /usr/lib/vmware/lib/libssl.so.0.9.7/libssl.so.0.9.7 and /usr/lib/vmware/lib/libcrypto.so.0.9.7/libcrypto.so.0.9.7

I hope it works, my setup doesn't yet, but it seems to be a problem with the horde server I'm trying to sync with.

I got EvolutionSync working perfectly using harty83's howto in [this thread]("http://ubuntuforums.org/showthread.php?t=282408").

The deal is to compile EvolutionSync and not using the precompiled binaries. Download the newest [source here]("http://sourceforge.net/projects/sync4jevolution/").

Then I unpacked the files and from the new evolutionsync directory I ran:
```
./configure --prefix=/usr
```
```
./make
```
```
sudo ./checkinstall
```

I had to install the following packages to make it work (I actually don't think I have all of these installed, but it cant harm):
```
build-essential, evolution-data-dev, libcurl-dev, checkinstall, evolution-data-server-dev
```
Mabye I also intalled ```
libcamel, libcamel-dev
``` but I don't know if this is necessary

---

