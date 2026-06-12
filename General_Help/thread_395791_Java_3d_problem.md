---
title: "Java 3d problem"
date: 2007-03-28
forum: General Help
---

### Post by zpon on 2007-03-28
Hello
I have a problem with my java installation, I have had it working, but I managed to **** it up, now when I compile and run a app i get

```
 java HelloJava3Da 
Java 3D WARNING : reported GLX version = 1.2
    GLX version 1.3 or higher is required
    The reported version number may be incorrect.  There is a known
    ATI driver bug in glXQueryVersion that incorrectly reports the GLX
    version as 1.2 when it really is 1.3, so Java 3D will attempt to
    run anyway.
Exception in thread "main" java.lang.NullPointerException: Canvas3D: null GraphicsConfiguration
        at javax.media.j3d.Canvas3D.checkForValidGraphicsConfig(Canvas3D.java:954)
        at javax.media.j3d.Canvas3D.<init>(Canvas3D.java:997)
        at HelloJava3Da.<init>(HelloJava3Da.java:50)
        at HelloJava3Da.main(HelloJava3Da.java:78)

```

Does anyone know anything that can help me?

---

### Post by zpon on 2007-03-29
After reinstalling the kernel and several other things I get this error in stead of the other
```
$ java HelloJava3Da
Exception in thread "main" java.lang.UnsatisfiedLinkError: /usr/lib/jvm/java-6-sun-1.6.0.00/jre/lib/i386/libj3dcore-ogl.so: libGL.so.1: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1668)
        at java.lang.Runtime.loadLibrary0(Runtime.java:823)
        at java.lang.System.loadLibrary(System.java:1030)
        at javax.media.j3d.NativePipeline$1.run(NativePipeline.java:138)
        at java.security.AccessController.doPrivileged(Native Method)
        at javax.media.j3d.NativePipeline.loadLibrary(NativePipeline.java:135)
        at javax.media.j3d.NativePipeline.loadLibraries(NativePipeline.java:95)
        at javax.media.j3d.MasterControl.loadLibraries(MasterControl.java:785)
        at javax.media.j3d.VirtualUniverse.<clinit>(VirtualUniverse.java:259)
        at HelloJava3Da.<init>(HelloJava3Da.java:47)
        at HelloJava3Da.main(HelloJava3Da.java:78)

```

---

### Post by zpon on 2007-04-07
Fixed by reinstalling libgl1-mesa-glx (did rm /usr/lib/libGL*) and libglu1-mesa (to reinstall libGLU)

---

