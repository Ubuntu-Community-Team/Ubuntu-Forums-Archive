---
title: "running Alice 2.4"
date: 2015-04-08
forum: General Help
---

### Post by bryan.sailer on 2015-04-08
I has downloaded Alice 2.4 and extracted the files into the /Download file.  In terminal I have used the following command and the program stops running.  What can I do to allow the program to open and function.

bryan@bryan-laptop:~/Downloads/Alice2.4/Required$ ./run-alice
Registered succesfully
*sys-package-mgr*: processing new jar, '/home/bryan/Downloads/Alice2.4/Required/lib/alice.jar'
*sys-package-mgr*: processing new jar, '/home/bryan/Downloads/Alice2.4/Required/externalLib/AppleJavaExtensions.jar'
*sys-package-mgr*: processing new jar, '/home/bryan/Downloads/Alice2.4/Required/externalLib/customizer.jar'
*sys-package-mgr*: processing new jar, '/home/bryan/Downloads/Alice2.4/Required/externalLib/getopt-1.0.7.jar'
*sys-package-mgr*: processing new jar, '/home/bryan/Downloads/Alice2.4/Required/externalLib/gluegen-rt.jar'
*sys-package-mgr*: processing new jar, '/home/bryan/Downloads/Alice2.4/Required/externalLib/j3dcore.jar'
*sys-package-mgr*: processing new jar, '/home/bryan/Downloads/Alice2.4/Required/externalLib/j3dutils.jar'
*sys-package-mgr*: processing new jar, '/home/bryan/Downloads/Alice2.4/Required/externalLib/javazoom.jar'
*sys-package-mgr*: processing new jar, '/home/bryan/Downloads/Alice2.4/Required/externalLib/jl1.0.jar'
*sys-package-mgr*: processing new jar, '/home/bryan/Downloads/Alice2.4/Required/externalLib/jmf.jar'
*sys-package-mgr*: processing new jar, '/home/bryan/Downloads/Alice2.4/Required/externalLib/jogl.jar'
*sys-package-mgr*: processing new jar, '/home/bryan/Downloads/Alice2.4/Required/externalLib/jython.jar'
*sys-package-mgr*: processing new jar, '/home/bryan/Downloads/Alice2.4/Required/externalLib/mediaplayer.jar'
*sys-package-mgr*: processing new jar, '/home/bryan/Downloads/Alice2.4/Required/externalLib/mp3plugin.jar'
*sys-package-mgr*: processing new jar, '/home/bryan/Downloads/Alice2.4/Required/externalLib/multiplayer.jar'
*sys-package-mgr*: processing new jar, '/home/bryan/Downloads/Alice2.4/Required/externalLib/resolver.jar'
*sys-package-mgr*: processing new jar, '/home/bryan/Downloads/Alice2.4/Required/externalLib/sound.jar'
*sys-package-mgr*: processing new jar, '/home/bryan/Downloads/Alice2.4/Required/externalLib/vecmath.jar'
*sys-package-mgr*: processing new jar, '/home/bryan/Downloads/Alice2.4/Required/externalLib/xercesImpl.jar'
*sys-package-mgr*: processing new jar, '/home/bryan/Downloads/Alice2.4/Required/externalLib/xercesSamples.jar'
*sys-package-mgr*: processing new jar, '/home/bryan/Downloads/Alice2.4/Required/externalLib/xml-apis.jar'
*sys-package-mgr*: processing new jar, '/home/bryan/Downloads/Alice2.4/Required/externalLib/xmlParserAPIs.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/resources.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/rt.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/jsse.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/jce.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/charsets.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/rhino.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/ext/dnsns.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/ext/localedata.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/ext/sunjce_provider.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/ext/icedtea-sound.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/ext/zipfs.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/ext/java-atk-wrapper.jar'
*sys-package-mgr*: processing new jar, '/usr/lib/jvm/java-7-openjdk-amd64/jre/lib/ext/sunpkcs11.jar'
OpenJDK 64-Bit Server VM warning: You have loaded library /home/bryan/Downloads/Alice2.4/Required/lib/linux-i586/libgluegen-rt.so which might have disabled stack guard. The VM will try to fix the stack guard now.
It's highly recommended that you fix the library with 'execstack -c <libfile>', or link it with '-z noexecstack'.
java.lang.UnsatisfiedLinkError: /home/bryan/Downloads/Alice2.4/Required/lib/linux-i586/libgluegen-rt.so: /home/bryan/Downloads/Alice2.4/Required/lib/linux-i586/libgluegen-rt.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary1(ClassLoader.java:1965)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1890)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1880)
	at java.lang.Runtime.loadLibrary0(Runtime.java:849)
	at java.lang.System.loadLibrary(System.java:1088)
	at com.sun.gluegen.runtime.NativeLibLoader.loadLibraryInternal(NativeLibLoader.java:102)
	at com.sun.gluegen.runtime.NativeLibLoader.access$000(NativeLibLoader.java:51)
	at com.sun.gluegen.runtime.NativeLibLoader$1.run(NativeLibLoader.java:70)
	at java.security.AccessController.doPrivileged(Native Method)
	at com.sun.gluegen.runtime.NativeLibLoader.loadGlueGenRT(NativeLibLoader.java:68)
	at com.sun.gluegen.runtime.NativeLibrary.ensureNativeLibLoaded(NativeLibrary.java:399)
	at com.sun.gluegen.runtime.NativeLibrary.open(NativeLibrary.java:163)
	at com.sun.gluegen.runtime.NativeLibrary.open(NativeLibrary.java:129)
	at com.sun.opengl.impl.x11.DRIHack.begin(DRIHack.java:109)
	at com.sun.opengl.impl.x11.X11GLDrawableFactory.<clinit>(X11GLDrawableFactory.java:99)
	at java.lang.Class.forName0(Native Method)
	at java.lang.Class.forName(Class.java:191)
	at javax.media.opengl.GLDrawableFactory.getFactory(GLDrawableFactory.java:111)
	at javax.media.opengl.GLCanvas.chooseGraphicsConfiguration(GLCanvas.java:520)
	at javax.media.opengl.GLCanvas.<init>(GLCanvas.java:131)
	at javax.media.opengl.GLCanvas.<init>(GLCanvas.java:90)
	at edu.cmu.cs.stage3.alice.scenegraph.renderer.joglrenderer.OnscreenRenderTarget.getAWTComponent(OnscreenRenderTarget.java:59)
	at edu.cmu.cs.stage3.alice.authoringtool.util.RenderTargetPickManipulator.setRenderTarget(RenderTargetPickManipulator.java:74)
	at edu.cmu.cs.stage3.alice.authoringtool.util.RenderTargetPickManipulator.<init>(RenderTargetPickManipulator.java:45)
	at edu.cmu.cs.stage3.alice.authoringtool.util.RenderTargetMultiManipulator.<init>(RenderTargetMultiManipulator.java:33)
	at edu.cmu.cs.stage3.alice.authoringtool.editors.sceneeditor.CameraViewPanel.renderInit(CameraViewPanel.java:875)
	at edu.cmu.cs.stage3.alice.authoringtool.editors.sceneeditor.SceneEditor.setAuthoringTool(SceneEditor.java:242)
	at edu.cmu.cs.stage3.alice.authoringtool.JAliceFrame.guiInit(JAliceFrame.java:178)
	at edu.cmu.cs.stage3.alice.authoringtool.JAliceFrame.<init>(JAliceFrame.java:89)
	at edu.cmu.cs.stage3.alice.authoringtool.AuthoringTool.mainInit(AuthoringTool.java:466)
	at edu.cmu.cs.stage3.alice.authoringtool.AuthoringTool.<init>(AuthoringTool.java:416)
	at edu.cmu.cs.stage3.alice.authoringtool.JAlice.main(JAlice.java:178)

---

### Post by CantankRus on 2015-04-09
It says @ [http://www.alice.org](http://www.alice.org) ...
> Note to Linux users: Alice is a 32-bit application, and requires the 32-bit Java libraries to run on Linux machines. 
More detailed instructions to follow. In the meantime contact Alice Support with your questions

I installed openjdk 32bit. This pulls in a lot of 32 bit files.
```
sudo apt-get install openjdk-7-jdk:i386
```
Alice would get as far as the loading screen and just stall.
[ATTACH=CONFIG]261189[/ATTACH]

I then set **java-7-openjdk-i386** as the default java...
```
sudo update-alternatives --config java
```

It now loads up fully.
You could probably edit the run-alice file to use **java-7-openjdk-i386** so you don't have to set openjdk-i386 system wide as default.
Beyond my current skills.

---

### Post by bryan.sailer on 2015-04-14
Thank you for the information, I did not read enough on the Alice web site about being 32 bit.  I am still working on getting the 32 bit Java to work on my 64 bit Ubuntu system.  I should be able to have it working shortly.

---

