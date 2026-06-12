---
title: "kernel blackscreen on login video issues 13.10"
date: 2014-02-16
forum: General Help
---

### Post by faceshed2 on 2014-02-16
Hello. Please excuse my noobyness, but please don't assume I won't learn. I've been trying to solve this problem on my own for a long time and it seams I've just exacerbated it. Currently Ubuntu boots into a black screen unless I log in with the gnome classic flashback. I managed to log out blindly so it's not a freeze and I also cough a glimpse of a error message that said I would have to run in a slow low graphics mode because of video errors, but it only popped up during a shutdown so I couldn't pick any options. I also have or have had trouble with many many programs and in every case googling the errors someone always suggests that or insists that each problem is a incorrect video driver problem.

What I've tried so far:
regular updates (have cause more problems)
reinstalling drivers. (no changes)
messing with xorg. Updating xorg. Uninstalling xorg. Getting confused about what xorg is. (no changes)
Update from 12.04 up to 13.10. (new kernels fail to work)
installing intels own driver fixing program made for 13.10. (no changes)

I'm using a compaq 6510b laptop with a integrated intel video card.
```
lspci -nn | grep VGA
``` will **correctly **(I think) output:
```
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c)
```
and ```
lshw -C Display
``` will **correctly **(I think) output:
```
  *-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (primary)
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:e4600000-e46fffff memory:d0000000-dfffffff ioport:4000(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 0c
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:e4700000-e47fffff

```

I don't know if it will help but minecraft crashes thusly:
```
Time: 2/17/14 3:18 AM
Description: Initializing game

org.lwjgl.LWJGLException: X Error - disp: 0x661aa088 serial: 128 error: GLXBadRenderRequest request_code: 153 minor_code: 1
    at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:321)
    at org.lwjgl.opengl.EXTFramebufferObject.nglCheckFramebufferStatusEXT(Native Method)
    at org.lwjgl.opengl.EXTFramebufferObject.glCheckFramebufferStatusEXT(EXTFramebufferObject.java:254)
    at bwg.i(SourceFile:506)
    at bmz.b(SourceFile:143)
    at bmz.a(SourceFile:61)
    at bmz.<init>(SourceFile:46)
    at azi.ad(SourceFile:338)
    at azi.f(SourceFile:696)
    at net.minecraft.client.main.Main.main(SourceFile:152)


A detailed walkthrough of the error, its code path and all known details is as follows:
---------------------------------------------------------------------------------------

-- Head --
Stacktrace:
    at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:321)
    at org.lwjgl.opengl.EXTFramebufferObject.nglCheckFramebufferStatusEXT(Native Method)
    at org.lwjgl.opengl.EXTFramebufferObject.glCheckFramebufferStatusEXT(EXTFramebufferObject.java:254)
    at bwg.i(SourceFile:506)
    at bmz.b(SourceFile:143)
    at bmz.a(SourceFile:61)
    at bmz.<init>(SourceFile:46)
    at azi.ad(SourceFile:338)

-- Initialization --
Details:
Stacktrace:
    at azi.f(SourceFile:696)
    at net.minecraft.client.main.Main.main(SourceFile:152)

-- System Details --
Details:
    Minecraft Version: 1.7.4
    Operating System: Linux (i386) version 3.11.0-15-generic
    Java Version: 1.7.0_51, Oracle Corporation
    Java VM Version: OpenJDK Server VM (mixed mode), Oracle Corporation
    Memory: 44460536 bytes (42 MB) / 79691776 bytes (76 MB) up to 954466304 bytes (910 MB)
    JVM Flags: 1 total; -Xmx1G
    AABB Pool Size: 0 (0 bytes; 0 MB) allocated, 0 (0 bytes; 0 MB) used
    IntCache: cache: 0, tcache: 0, allocated: 0, tallocated: 0
    Launched Version: 1.7.4
    LWJGL: 2.9.1
    OpenGL: Gallium 0.4 on llvmpipe (LLVM 3.3, 128 bits) GL version 1.4 (2.1 Mesa 9.2.1), VMware, Inc.
    GL Caps: Using GL 1.3 multitexturing.
Using framebuffer objects because EXT_framebuffer_object is supported.
Anisotropic filtering is not supported.
Shaders are not available because OpenGL 2.1 is not supported, ARB_shader_objects is not supported, ARB_vertex_shader is not supported, and ARB_fragment_shader is not supported.

    Is Modded: Probably not. Jar signature remains and client brand is untouched.
    Type: Client (map_client.txt)
    Resource Packs: []
    Current Language: ~~ERROR~~ NullPointerException: null
    Profiler Position: N/A (disabled)
    Vec3 Pool Size: ~~ERROR~~ NullPointerException: null
    Anisotropic Filtering: Off (1)
```

I also have issues loading nearly everything in wine and I had to use some weird workaround for zsnes to work.
Thank you for any help.

---

### Post by faceshed2 on 2014-02-16
Also I'm getting some other errors that I don't think are related, but maybe would be smart to include;
Grub is giving me a "file not found. file not found. file not found.  Press any key to continue..." message and then continuing automatically. After that I get a "kvm: disabled by bios" message. I enabled "virtualization technology" in the bios after getting it, but the error message is still there. Both of these started after going from 12.10 to 13.10. If they are not related, ignore this.

---

### Post by bc.haynes on 2014-02-16
What type of computer is it....desktop, laptop, Acer, Lenovo, etc.?   Was 13.10 a clean install, or did you go from 12.10 to 13.04 to13.10?

---

### Post by faceshed2 on 2014-02-16
I'm using a compaq 6510b laptop with a integrated intel video card.

I was first using 12.04 and updated to 12.10 and that is when the kernel totally messed up. I didn't bother testing much with that and just updated right to 13.10.

---

### Post by bc.haynes on 2014-02-16
It is my understanding that you cannot go from 12.10 to 13.10 without going through 13.04. That may be the cause of "File not found."

Have you tried different boot options like "nomodeset?"

---

### Post by faceshed2 on 2014-02-16
I'm not worried about seeing an error when I boot as long as it boots so I haven't tried anything. Could it really be part of the problem?
I have a live usb I can use to fix grub. I can do that tomorrow.

---

### Post by faceshed2 on 2014-02-17
When my computer refused to boot from my USB drive I used the instructions on the second answer here:
[http://askubuntu.com/questions/202313/error-file-not-found](http://askubuntu.com/questions/202313/error-file-not-found)
```
sudo grub-install /dev/sdX  # replace X with your actual value
sudo update-grub
```
and both startup error messages are now gone. No changes with my main issue.

---

### Post by faceshed2 on 2014-02-17
Ok sort of solved. I found out I had some problems with direct rendering and after a bit of goggling I found a solution:
```
glxinfo | grep '^direct rendering:'
```
answered "no", but after running this:
```
sudo apt-get remove fglrx
sudo apt-get remove mesa-dri
sudo apt-get install mesa-dri
```
direct render gave a "yes". Minecraft now works and I can run the gnome flashback WITH effects. THANKS [**[COLOR=#000000]nick937[/COLOR]**]("http://ubuntuforums.org/member.php?u=490370")!!! ([http://ubuntuforums.org/showthread.php?t=870249](http://ubuntuforums.org/showthread.php?t=870249))

HOWEVER... the 'ubuntu default' (I assume unity) crashes. I got it to send a bug report so that's good enough for me. I'm not marking this as solved because it's not, but I won't be actively looking for a fix anymore. *Post suggestions and help only if you personally want to fix this problem for your own sake and not mine*.

---

