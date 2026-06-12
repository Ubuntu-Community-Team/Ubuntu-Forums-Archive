---
title: "How can I resolve this error code message?"
date: 2020-09-28
forum: General Help
---

### Post by suomalainen on 2020-09-28
I received this error message and would like to learn what it means and how I may possibly resolve it.

Thank you!

Suomalainen


```
Sep 28, 2020 8:17:33 PM javafx.scene.control.Control loadSkinClass
SEVERE: Failed to load skin 'com.sun.javafx.scene.control.skin.ProgressBarSkin' for control ProgressBar[id=splashProgressBar, styleClass=progress-bar progress-bar]
java.lang.ClassNotFoundException: com.sun.javafx.scene.control.skin.ProgressBarSkin
	at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(BuiltinClassLoader.java:581)
	at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(ClassLoaders.java:178)
	at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:522)
	at java.base/java.lang.Class.forName0(Native Method)
	at java.base/java.lang.Class.forName(Class.java:398)
	at javafx.controls/javafx.scene.control.Control.loadClass(Control.java:124)
	at javafx.controls/javafx.scene.control.Control.loadSkinClass(Control.java:720)
	at javafx.controls/javafx.scene.control.Control$5.invalidated(Control.java:680)
	at javafx.base/javafx.beans.property.StringPropertyBase.markInvalid(StringPropertyBase.java:110)
	at javafx.base/javafx.beans.property.StringPropertyBase.set(StringPropertyBase.java:145)
	at javafx.graphics/javafx.css.StyleableStringProperty.set(StyleableStringProperty.java:83)
	at javafx.controls/javafx.scene.control.Control$5.set(Control.java:672)
	at javafx.graphics/javafx.css.StyleableStringProperty.applyStyle(StyleableStringProperty.java:69)
	at javafx.graphics/javafx.css.StyleableStringProperty.applyStyle(StyleableStringProperty.java:45)
	at javafx.graphics/javafx.scene.CssStyleHelper.transitionToState(CssStyleHelper.java:787)
	at javafx.graphics/javafx.scene.Node.doProcessCSS(Node.java:9647)
	at javafx.graphics/javafx.scene.Node.access$900(Node.java:398)
	at javafx.graphics/javafx.scene.Node$1.doProcessCSS(Node.java:471)
	at javafx.graphics/com.sun.javafx.scene.NodeHelper.processCSSImpl(NodeHelper.java:192)
	at javafx.graphics/com.sun.javafx.scene.ParentHelper.superProcessCSSImpl(ParentHelper.java:93)
	at javafx.graphics/com.sun.javafx.scene.ParentHelper.superProcessCSS(ParentHelper.java:63)
	at javafx.graphics/javafx.scene.Parent.doProcessCSS(Parent.java:1366)
	at javafx.graphics/javafx.scene.Parent.access$400(Parent.java:79)
	at javafx.graphics/javafx.scene.Parent$1.doProcessCSS(Parent.java:125)
	at javafx.graphics/com.sun.javafx.scene.ParentHelper.processCSSImpl(ParentHelper.java:98)
	at javafx.controls/com.sun.javafx.scene.control.ControlHelper.superProcessCSSImpl(ControlHelper.java:63)
	at javafx.controls/com.sun.javafx.scene.control.ControlHelper.superProcessCSS(ControlHelper.java:55)
	at javafx.controls/javafx.scene.control.Control.doProcessCSS(Control.java:886)
	at javafx.controls/javafx.scene.control.Control.access$000(Control.java:83)
	at javafx.controls/javafx.scene.control.Control$1.doProcessCSS(Control.java:89)
	at javafx.controls/com.sun.javafx.scene.control.ControlHelper.processCSSImpl(ControlHelper.java:67)
	at javafx.graphics/com.sun.javafx.scene.NodeHelper.processCSS(NodeHelper.java:145)
	at javafx.graphics/javafx.scene.Parent.doProcessCSS(Parent.java:1397)
	at javafx.graphics/javafx.scene.Parent.access$400(Parent.java:79)
	at javafx.graphics/javafx.scene.Parent$1.doProcessCSS(Parent.java:125)
	at javafx.graphics/com.sun.javafx.scene.ParentHelper.processCSSImpl(ParentHelper.java:98)
	at javafx.graphics/com.sun.javafx.scene.NodeHelper.processCSS(NodeHelper.java:145)
	at javafx.graphics/javafx.scene.Node.processCSS(Node.java:9529)
	at javafx.graphics/javafx.scene.Scene.doCSSPass(Scene.java:569)
	at javafx.graphics/javafx.scene.Scene.preferredSize(Scene.java:1745)
	at javafx.graphics/javafx.scene.Scene$2.preferredSize(Scene.java:393)
	at javafx.graphics/com.sun.javafx.scene.SceneHelper.preferredSize(SceneHelper.java:66)
	at javafx.graphics/javafx.stage.Window$12.invalidated(Window.java:1086)
	at javafx.base/javafx.beans.property.BooleanPropertyBase.markInvalid(BooleanPropertyBase.java:110)
	at javafx.base/javafx.beans.property.BooleanPropertyBase.set(BooleanPropertyBase.java:145)
	at javafx.graphics/javafx.stage.Window.setShowing(Window.java:1174)
	at javafx.graphics/javafx.stage.Window.show(Window.java:1189)
	at javafx.graphics/javafx.stage.Stage.show(Stage.java:273)
	at com.nxp.tagxplorer.Main.start(Main.java:66)
	at javafx.graphics/com.sun.javafx.application.LauncherImpl.lambda$launchApplication1$9(LauncherImpl.java:846)
	at javafx.graphics/com.sun.javafx.application.PlatformImpl.lambda$runAndWait$12(PlatformImpl.java:455)
	at javafx.graphics/com.sun.javafx.application.PlatformImpl.lambda$runLater$10(PlatformImpl.java:428)
	at java.base/java.security.AccessController.doPrivileged(Native Method)
	at javafx.graphics/com.sun.javafx.application.PlatformImpl.lambda$runLater$11(PlatformImpl.java:427)
	at javafx.graphics/com.sun.glass.ui.InvokeLaterDispatcher$Future.run(InvokeLaterDispatcher.java:96)
	at javafx.graphics/com.sun.glass.ui.gtk.GtkApplication._runLoop(Native Method)
	at javafx.graphics/com.sun.glass.ui.gtk.GtkApplication.lambda$runLoop$11(GtkApplication.java:277)
	at java.base/java.lang.Thread.run(Thread.java:834)

Sep 28, 2020 8:17:33 PM javafx.scene.control.Control loadSkinClass
SEVERE: Failed to load skin 'com.sun.javafx.scene.control.skin.ProgressBarSkin' for control ProgressBar[id=splashProgressBar, styleClass=progress-bar progress-bar]
java.lang.ClassNotFoundException: com.sun.javafx.scene.control.skin.ProgressBarSkin
	at java.base/jdk.internal.loader.BuiltinClassLoader.loadClass(BuiltinClassLoader.java:581)
	at java.base/jdk.internal.loader.ClassLoaders$AppClassLoader.loadClass(ClassLoaders.java:178)
	at java.base/java.lang.ClassLoader.loadClass(ClassLoader.java:522)
	at java.base/java.lang.Class.forName0(Native Method)
	at java.base/java.lang.Class.forName(Class.java:398)
	at javafx.controls/javafx.scene.control.Control.loadClass(Control.java:124)
	at javafx.controls/javafx.scene.control.Control.loadSkinClass(Control.java:720)
	at javafx.controls/javafx.scene.control.Control$5.invalidated(Control.java:680)
	at javafx.base/javafx.beans.property.StringPropertyBase.markInvalid(StringPropertyBase.java:110)
	at javafx.base/javafx.beans.property.StringPropertyBase.set(StringPropertyBase.java:145)
	at javafx.graphics/javafx.css.StyleableStringProperty.set(StyleableStringProperty.java:83)
	at javafx.controls/javafx.scene.control.Control$5.set(Control.java:672)
	at javafx.graphics/javafx.css.StyleableStringProperty.applyStyle(StyleableStringProperty.java:69)
	at javafx.graphics/javafx.css.StyleableStringProperty.applyStyle(StyleableStringProperty.java:45)
	at javafx.graphics/javafx.scene.CssStyleHelper.transitionToState(CssStyleHelper.java:787)
	at javafx.graphics/javafx.scene.Node.doProcessCSS(Node.java:9647)
	at javafx.graphics/javafx.scene.Node.access$900(Node.java:398)
	at javafx.graphics/javafx.scene.Node$1.doProcessCSS(Node.java:471)
	at javafx.graphics/com.sun.javafx.scene.NodeHelper.processCSSImpl(NodeHelper.java:192)
	at javafx.graphics/com.sun.javafx.scene.ParentHelper.superProcessCSSImpl(ParentHelper.java:93)
	at javafx.graphics/com.sun.javafx.scene.ParentHelper.superProcessCSS(ParentHelper.java:63)
	at javafx.graphics/javafx.scene.Parent.doProcessCSS(Parent.java:1366)
	at javafx.graphics/javafx.scene.Parent.access$400(Parent.java:79)
	at javafx.graphics/javafx.scene.Parent$1.doProcessCSS(Parent.java:125)
	at javafx.graphics/com.sun.javafx.scene.ParentHelper.processCSSImpl(ParentHelper.java:98)
	at javafx.controls/com.sun.javafx.scene.control.ControlHelper.superProcessCSSImpl(ControlHelper.java:63)
	at javafx.controls/com.sun.javafx.scene.control.ControlHelper.superProcessCSS(ControlHelper.java:55)
	at javafx.controls/javafx.scene.control.Control.doProcessCSS(Control.java:900)
	at javafx.controls/javafx.scene.control.Control.access$000(Control.java:83)
	at javafx.controls/javafx.scene.control.Control$1.doProcessCSS(Control.java:89)
	at javafx.controls/com.sun.javafx.scene.control.ControlHelper.processCSSImpl(ControlHelper.java:67)
	at javafx.graphics/com.sun.javafx.scene.NodeHelper.processCSS(NodeHelper.java:145)
	at javafx.graphics/javafx.scene.Parent.doProcessCSS(Parent.java:1397)
	at javafx.graphics/javafx.scene.Parent.access$400(Parent.java:79)
	at javafx.graphics/javafx.scene.Parent$1.doProcessCSS(Parent.java:125)
	at javafx.graphics/com.sun.javafx.scene.ParentHelper.processCSSImpl(ParentHelper.java:98)
	at javafx.graphics/com.sun.javafx.scene.NodeHelper.processCSS(NodeHelper.java:145)
	at javafx.graphics/javafx.scene.Node.processCSS(Node.java:9529)
	at javafx.graphics/javafx.scene.Scene.doCSSPass(Scene.java:569)
	at javafx.graphics/javafx.scene.Scene.preferredSize(Scene.java:1745)
	at javafx.graphics/javafx.scene.Scene$2.preferredSize(Scene.java:393)
	at javafx.graphics/com.sun.javafx.scene.SceneHelper.preferredSize(SceneHelper.java:66)
	at javafx.graphics/javafx.stage.Window$12.invalidated(Window.java:1086)
	at javafx.base/javafx.beans.property.BooleanPropertyBase.markInvalid(BooleanPropertyBase.java:110)
	at javafx.base/javafx.beans.property.BooleanPropertyBase.set(BooleanPropertyBase.java:145)
	at javafx.graphics/javafx.stage.Window.setShowing(Window.java:1174)
	at javafx.graphics/javafx.stage.Window.show(Window.java:1189)
	at javafx.graphics/javafx.stage.Stage.show(Stage.java:273)
	at com.nxp.tagxplorer.Main.start(Main.java:66)
	at javafx.graphics/com.sun.javafx.application.LauncherImpl.lambda$launchApplication1$9(LauncherImpl.java:846)
	at javafx.graphics/com.sun.javafx.application.PlatformImpl.lambda$runAndWait$12(PlatformImpl.java:455)
	at javafx.graphics/com.sun.javafx.application.PlatformImpl.lambda$runLater$10(PlatformImpl.java:428)
	at java.base/java.security.AccessController.doPrivileged(Native Method)
	at javafx.graphics/com.sun.javafx.application.PlatformImpl.lambda$runLater$11(PlatformImpl.java:427)
	at javafx.graphics/com.sun.glass.ui.InvokeLaterDispatcher$Future.run(InvokeLaterDispatcher.java:96)
	at javafx.graphics/com.sun.glass.ui.gtk.GtkApplication._runLoop(Native Method)
	at javafx.graphics/com.sun.glass.ui.gtk.GtkApplication.lambda$runLoop$11(GtkApplication.java:277)
	at java.base/java.lang.Thread.run(Thread.java:834)

Sep 28, 2020 8:17:37 PM javafx.css.CssParser declaration
WARNING: CSS Error parsing jar:file:/home/paavo/NFC/NXP/TagXplorer-v1.2.jar!/css/Launch_Screen_Style.css: expected series of <size> while parsing 'box-shadow' at [28,13]
Sep 28, 2020 8:17:37 PM javafx.css.CssParser declaration
WARNING: CSS Error parsing jar:file:/home/paavo/NFC/NXP/TagXplorer-v1.2.jar!/css/Launch_Screen_Style.css: expected series of <size> while parsing 'box-shadow' at [33,13]
Sep 28, 2020 8:17:37 PM javafx.css.CssParser declaration
WARNING: CSS Error parsing jar:file:/home/paavo/NFC/NXP/TagXplorer-v1.2.jar!/css/Launch_Screen_Style.css: Expected '<font-weight>' while parsing '-fx-font-weight' at [42,18]
Sep 28, 2020 8:17:37 PM javafx.css.CssParser declaration
WARNING: CSS Error parsing jar:file:/home/paavo/NFC/NXP/TagXplorer-v1.2.jar!/css/Launch_Screen_Style.css: expected series of <size> while parsing 'box-shadow' at [64,13]
Sep 28, 2020 8:17:37 PM javafx.css.CssParser declaration
WARNING: CSS Error parsing jar:file:/home/paavo/NFC/NXP/TagXplorer-v1.2.jar!/css/Launch_Screen_Style.css: expected series of <size> while parsing 'box-shadow' at [189,13]
Sep 28, 2020 8:17:37 PM javafx.css.CssParser declaration
WARNING: CSS Error parsing jar:file:/home/paavo/NFC/NXP/TagXplorer-v1.2.jar!/css/Launch_Screen_Style_1600x900.css: expected series of <size> while parsing 'box-shadow' at [39,13]
Sep 28, 2020 8:17:37 PM javafx.css.CssParser declaration
WARNING: CSS Error parsing jar:file:/home/paavo/NFC/NXP/TagXplorer-v1.2.jar!/css/Launch_Screen_Style_1600x900.css: expected series of <size> while parsing 'box-shadow' at [45,13]
Sep 28, 2020 8:17:37 PM javafx.css.CssParser declaration
WARNING: CSS Error parsing jar:file:/home/paavo/NFC/NXP/TagXplorer-v1.2.jar!/css/Launch_Screen_Style_1600x900.css: Expected '<font-weight>' while parsing '-fx-font-weight' at [54,18]
Sep 28, 2020 8:17:37 PM javafx.css.CssParser declaration
WARNING: CSS Error parsing jar:file:/home/paavo/NFC/NXP/TagXplorer-v1.2.jar!/css/Launch_Screen_Style_1600x900.css: expected series of <size> while parsing 'box-shadow' at [76,13]
```

---

### Post by scorp123 on 2020-09-28
That's a Java crash message. What app were you running at the time?

---

### Post by suomalainen on 2020-09-29
I'm running TagExlorer and explained here:

[https://ubuntuforums.org/showthread.php?t=2450568](https://ubuntuforums.org/showthread.php?t=2450568)

How I installed it and the files I'm suppose to use to even get it to open.

MY only challenge now is that connected NFC readers/writes don't seem to be recognized.

---

### Post by scorp123 on 2020-09-29
> **suomalainen said:**
> I'm running TagExlorer 

... but the application continues to work? Then ignore those messages. Java applications always print tons and tons of diagnostic messages that most of the time sound a lot more dramatic than they are. For as long as your application keeps running and remains functional I'd bet that whatever the error message says was non-fatal and the application will continue to function as is.

---

### Post by suomalainen on 2020-09-29
The only problem with the application is that it does not recognize the NFC reader/writer connected to it when it should. So without having a NFC reader/writer that the application sees I'm still dead in the water :(

---

### Post by scorp123 on 2020-09-30
> **suomalainen said:**
> The only problem with the application is that it does not recognize the NFC reader/writer connected to it 

How is it connected? USB? PCI card? ...?

---

### Post by suomalainen on 2020-09-30
USB
paavo@Paavo:~$ lsusb
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
paavo@Paavo:~$

---

### Post by scorp123 on 2020-09-30
> **suomalainen said:**
> USB
paavo@Paavo:~$ lsusb
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
paavo@Paavo:~$

And which of these is the NFC device?

---

### Post by suomalainen on 2020-10-01
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer

---

### Post by suomalainen on 2020-10-01
paavo@Paavo:~$ lsusb
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Flash Card Reader/Writer
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 002: ID 04e6:5790 SCM Microsystems, Inc. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c52f Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Above I made a mistake. Actually it is this one SCM Microsystems, Inc.

---

### Post by scorp123 on 2020-10-02
> **suomalainen said:**
> paavo@Paavo:~$ lsusb
...
Bus 007 Device 002: ID 04e6:5790 SCM Microsystems, Inc. 
...

Above I made a mistake. Actually it is this one SCM Microsystems, Inc.

And that device gets recognised and is supported by the kernel? What do you get e.g. from:
```
sudo lsdev
sudo lsmod
```

Could be that you need to install a package for "lsdev" first, it's not there by default.

The point is this: Even if the device can be seen on the USB port (that's a standard USB thing), unless it can also be used by the kernel and a kernel module there's no way you will be able to talk to it.

---

