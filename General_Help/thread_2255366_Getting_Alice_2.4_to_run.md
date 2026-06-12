---
title: "Getting Alice 2.4 to run"
date: 2014-12-04
forum: General Help
---

### Post by cigtoxdoc on 2014-12-04
What does the following mean?  In particular, what is the correct syntak when it is telling me to "fix the library with 'execstack -c <libfile>', or link it with '-z noexecstack'."

```
john@john-MSI-7846:~/Alice 2.4/Required$ ./run-alice
Registered succesfully
Java HotSpot(TM) 64-Bit Server VM warning: You have loaded library /home/john/Alice 2.4/Required/lib/linux-i586/libgluegen-rt.so which might have disabled stack guard. The VM will try to fix the stack guard now.
It's highly recommended that you fix the library with 'execstack -c <libfile>', or link it with '-z noexecstack'.
java.lang.UnsatisfiedLinkError: /home/john/Alice 2.4/Required/lib/linux-i586/libgluegen-rt.so: /home/john/Alice 2.4/Required/lib/linux-i586/libgluegen-rt.so: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1929)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1847)
        at java.lang.Runtime.loadLibrary0(Runtime.java:870)
        at java.lang.System.loadLibrary(System.java:1119)
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
        at java.lang.Class.forName(Class.java:260)
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
^Cjohn@john-MSI-7846:~/Alice 2.4/Required$ execstack -c <libfile>
bash: syntax error near unexpected token `newline'
john@john-MSI-7846:~/Alice 2.4/Required$ -z noexecstack
-z: command not found
john@john-MSI-7846:~/Alice 2.4/Required$
```

---

