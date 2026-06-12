---
title: "Help with VMWare Direct3D support under Workstation 6.0.1 amd64"
date: 2007-10-02
forum: General Help
---

### Post by besson3c on 2007-10-02
Hello,

I've added the following to my VMWare .vmx file:

> mks.enable3d = "TRUE"
svga.vramSize = "67108864"
vmmouse.present = "FALSE"

I've also made the following changes to my /usr/lib32 directory in adding some additional symlinks:

> 
# ls -l /usr/lib32/*nvidia*
lrwxrwxrwx 1 root root     26 2007-10-01 21:54 /usr/lib32/libnvidia-cfg.so.1 -> libnvidia-cfg.so.100.14.19
-rwxr-xr-x 1 root root 110656 2007-10-01 21:51 /usr/lib32/libnvidia-cfg.so.100.14.19
-rw-r--r-- 1 root root 107136 2007-06-25 17:31 /usr/lib32/libnvidia-cfg.so.1.0.9631
lrwxrwxrwx 1 root root     26 2007-10-01 21:54 /usr/lib32/libnvidia-tls.so -> libnvidia-tls.so.100.14.19
lrwxrwxrwx 1 root root     26 2007-10-01 21:54 /usr/lib32/libnvidia-tls.so.1 -> libnvidia-tls.so.100.14.19
-rwxr-xr-x 1 root root   2324 2007-10-01 21:51 /usr/lib32/libnvidia-tls.so.100.14.19
-rw-r--r-- 1 root root   2440 2007-06-25 17:31 /usr/lib32/libnvidia-tls.so.1.0.9631


> # ls -l /usr/lib32/tls/*
lrwxrwxrwx 1 root root   26 2007-10-01 21:54 /usr/lib32/tls/libnvidia-tls.so.1 -> libnvidia-tls.so.100.14.19
-rwxr-xr-x 1 root root 2324 2007-10-01 21:51 /usr/lib32/tls/libnvidia-tls.so.100.14.19
-rw-r--r-- 1 root root 2440 2007-10-02 00:25 /usr/lib32/tls/libnvidia-tls.so.1.0.9631
-rw-r--r-- 1 root root 2412 2007-06-25 17:31 /usr/lib32/tls/libnvidia-tls.so.1.0.9631.backup


I'm getting the "failed to render" error message upon startup of my virtual machine. Have I missed anything here? I'd love to get Direct3D working on my setup here!

---

### Post by besson3c on 2007-10-02
Perhaps there ought to be an nvidia 32 package for those of us on 64 bit machines that need the 32 bit driver installed this way?

---

### Post by besson3c on 2007-10-03
Just giving this thread a bump. I found this information from April 2006:

> Well ... here's a possible showstopper on AMD64 systems with NVIDIA graphic cards (I'm running VMware Wks 5.5.1 build 19175 on Breezy AMD64).

You added the following lines to your <virtualmachine>.vmx file:

mks.enable3d = "TRUE"
svga.vramSize = "67108864" (or "134217728")

As soon as you start the VM you get an error saying the 3d acceleration cannot be used because of a problem with libnvidia-tls.so.1

Reason: unknown (only Nvidia may know the answer)
Source: VMware opens the 32-Bit TLS library (instead of the 64-Bit one) ... and here seems to be a catch.

Open a terminal and type ...

# sudo mv /usr/lib32/tls/libnvidia-tls.so.1.0.<version> /usr/lib32/tls/libnvidia-tls.so.1.0.<version>.backup
# sudo cp /usr/lib32/libnvidia-tls.so.1.0.<version> /usr/lib32/tls

Replace <version> with the version number of the Nvidia driver that's installed on your box ... here's an example for v87.56 ...

# sudo mv /usr/lib32/tls/libnvidia-tls.so.1.0.8756 /usr/lib32/tls/libnvidia-tls.so.1.0.8756.backup
# sudo cp /usr/lib32/libnvidia-tls.so.1.0.8756 /usr/lib32/tls

That's it ... exit the terminal, fire up VMware, start the VM ... the error should be gone and 3d acceleration should be available.

Hope this information is useful ...

Storm.


[http://ubuntuforums.org/archive/index.php/t-84344.html](http://ubuntuforums.org/archive/index.php/t-84344.html)

Unfortunately, these instructions don't seem to work for me, and I've seen other instructions floating around that involve creating symlinks to get around the fact that the 32 bit drivers are being used. I haven't found a solution that works for me yet. Any update on this? Anybody?

I'd *love* to get this working!

---

