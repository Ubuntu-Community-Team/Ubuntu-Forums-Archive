---
title: "libGL segfaults, I have no OpenGL!!"
date: 2007-03-07
forum: General Help
---

### Post by freerick on 2007-03-07
I have an NVIDIA 6200, and I'm installing the nvidia drivers from the binary on their web site. The native Ubuntu driver can't handle 1600x1200 resolution, much less 3d acceleration, so I need nvidia's.

The driver installer that nvidia provides compiles a kernel module; this works fine except for libGL. libGL segfaults at compile-time and at runtime, leaving me with no 3D support. :( 

At the end of nvidia's driver installation, I get the following warning dialog:

```

WARNING: Unable to perform the runtime configuration check for library
         'libGL.so.1' ('/usr/lib32/libGL.so.1.0.9746'); assuming successful
         installation.

```


nvidia-installer.log shows the following:


```

-> Kernel module compilation complete.
-> Kernel messages:
**   [   68.141464] glxinfo[7969]: segfault at 00002aaaaab2b014 rip**
   00002b731a0b8c4b rsp 00007fff919a1bd0 error 4
   [   72.465762] eth0: no IPv6 routers present
 [B]  [   92.101494] nvidia-settings[8148]: segfault at 00002aaaaf118014 rip
   00002aaaab298c4b rsp 00007ffffa7db080 error 4[/B]
   [   92.717873] ISO 9660 Extensions: Microsoft Joliet Level 3
   [   92.818788] ISO 9660 Extensions: RRIP_1991A
   [  333.877705] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
   [  333.877731] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
   [  333.877843] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
   [  381.997325] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) ->
   IRQ 225
   [  381.997453] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 24 (level, low) ->
   IRQ 233
   [  381.997461] PCI: Setting latency timer of device 0000:02:00.0 to 64
   [  381.997597] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  1.0-9746  Fri
   Dec 15 10:19:35 PST 2006
   [  431.666035] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) ->
   IRQ 225
   [  431.666533] PCI: Enabling device 0000:02:00.0 (0004 -> 0006)
   [  431.666539] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 24 (level, low) ->
   IRQ 233
   [  431.666614] PCI: Setting latency timer of device 0000:02:00.0 to 64
   [  431.666974] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  1.0-9746  Fri
   Dec 15 10:19:35 PST 2006
   [  432.002601] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
   [  432.002632] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
   [  432.002746] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
   [  442.490245] glxinfo[9627]: segfault at 00002aaaaab2b014 rip
   00002b6259333c4b rsp 00007fff52724950 error 4
   [ 9316.005212] ACPI: PCI Interrupt 0000:01:00.0[A] -> GSI 16 (level, low) ->
   IRQ 225
   [ 9316.005574] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 24 (level, low) ->
   IRQ 233
   [ 9316.005757] PCI: Setting latency timer of device 0000:02:00.0 to 64
   [ 9316.006022] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  1.0-9746  Fri
   Dec 15 10:19:35 PST 2006
-> Installing both new and classic TLS OpenGL libraries.
-> Installing classic TLS 32bit OpenGL libraries.
-> Install NVIDIA's 32-bit compatibility OpenGL libraries? (Answer: Yes)
-> Parsing log file:
-> done.
-> Validating previous installation:
-> done.
-> Uninstalling NVIDIA Accelerated Graphics Driver for Linux-x86_64
   (1.0-9746):
-> done.
-> Uninstallation of existing driver: NVIDIA Accelerated Graphics Driver for
   Linux-x86_64 (1.0-9746) is complete.
-> Searching for conflicting X files:
-> done.
-> Searching for conflicting OpenGL files:
-> done.
-> Installing 'NVIDIA Accelerated Graphics Driver for Linux-x86_64'
   (1.0-9746):
   executing: '/sbin/ldconfig'...
   executing: '/sbin/depmod -aq'...
-> done.
-> Driver file installation is complete.
-> Running post-install sanity check:
-> done.
-> Post-install sanity check passed.
-> Shared memory test passed.
[B]-> Running runtime sanity check:
WARNING: Unable to perform the runtime configuration check for library
         'libGL.so.1' ('/usr/lib32/libGL.so.1.0.9746'); assuming successful
         installation.
-> done.[/B]
-> Runtime sanity check passed.
-> Would you like to run the nvidia-xconfig utility to automatically update you
   r X configuration file so that the NVIDIA X driver will be used when you res
   tart X?  Any pre-existing X configuration file will be backed up. (Answer: N
   o)
-> Installation of the NVIDIA Accelerated Graphics Driver for Linux-x86_64
   (version: 1.0-9746) is now complete.  Please update your XF86Config or
   xorg.conf file as appropriate; see the file
   /usr/share/doc/NVIDIA_GLX-1.0/README.txt for details.

```


I'm guessing that there is some version mismatch among the header files and modules, but I can't figure out how to fix it. 

If anyone has any info regarding this problem, please let me know, your help will be much appreciated.

---

### Post by rurinix on 2007-03-24
I'm a n00b to Ubuntu, but I did notice that the /usr/lib directory contains the content which the NVidia drivers where looking for.  Thus, I would suggest you make a symbolic link (here is a refresher line for you)

```
sudo ln --symbolic /usr/lib /usr/lib32
```

see if that helps you.  I haven't yet to gotten it to work myself either.

I tried downloading the driver from NVidia's website, but now they only have a *.run file which requires X-server to not be running.  If you can tell me how to do that in Ubuntu I will be very happy.  The only way I know is to remove gdm from the /etc/rc2.0/ directory,  which still doesn't allow me to log in as root.  I'm a bit baffled because I have never seen a linux flavor which effectively disables linux (though gentoo suggested to do basically that).

---

### Post by darthrevan13 on 2007-04-10
I had that error too, but i got rid of it. I realized that after installing some 32 bit libraries the message disappears. Just type: 

sudo apt-get install ia32-libs linux32 lib32asound2

in a terminal and after it's done, download the ia32-libs-gtk from here:

[http://ubuntu-hr.org/ubuntu/pool/main/i/ia32-libs-gtk/ia32-libs-gtk_7_amd64.deb](http://ubuntu-hr.org/ubuntu/pool/main/i/ia32-libs-gtk/ia32-libs-gtk_7_amd64.deb)

If the site does not work get another one from here:

[http://packages.ubuntu.com/breezy/libs/ia32-libs-gtk](http://packages.ubuntu.com/breezy/libs/ia32-libs-gtk)

It should work after that

Cheers

---

### Post by KushMaster on 2007-09-11
Darthrevan13 both your links are broken and your code

Code:sudo apt-get install ia32-libs linux32 lib32asound2

does not work either.

---

