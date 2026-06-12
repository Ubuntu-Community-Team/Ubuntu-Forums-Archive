---
title: "Running Eclipse"
date: 2008-06-17
forum: General Help
---

### Post by jtreg on 2008-06-17
I recently installed Eclipse,eclipse-java-europa-winter-linux-gtk.tar.gz

 extracting it to /opt/eclipse

I have $JAVA_HOME as java-1.5.0-sun-1.5.0.15

I get this console output 

Can ayone help?

james@ubik:/opt/eclipse$ eclipse
!SESSION 2008-06-17 12:27:49.362 -----------------------------------------------
eclipse.buildId=M20080221-1800
java.version=1.5.0_15
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_GB
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 4 0 2008-06-17 12:27:50.897
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: no swt-gtk-3349 or swt-gtk in swt.library.path, java.library.path or the jar file
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:219)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:151)
        at org.eclipse.swt.internal.C.<clinit>(C.java:21)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:128)
        at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:482)
        at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
        at org.eclipse.ui.internal.ide.application.IDEApplication.createDisplay(IDEApplication.java:133)
        at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:86)
        at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:169)
        at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:106)
        at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:76)
        at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:363)
        at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:176)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:585)
        at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:508)
        at org.eclipse.equinox.launcher.Main.basicRun(Main.java:447)
        at org.eclipse.equinox.launcher.Main.run(Main.java:1173)
        at org.eclipse.equinox.launcher.Main.main(Main.java:1148)

!ENTRY org.eclipse.osgi 2 0 2008-06-17 12:27:51.153
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-06-17 12:27:51.154
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.compiler.apt_1.0.1.R33x_v20071002-2100.jar[/email] [69] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.compiler.apt 2 0 2008-06-17 12:27:51.154
!MESSAGE Missing imported package org.eclipse.jdt.internal.compiler.tool_0.0.0.
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-06-17 12:27:51.154
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.apt.pluggable.core_1.0.1.R33x_v20071002-2100.jar[/email] [71] was not resolved.
!SUBENTRY 2 org.eclipse.jdt.apt.pluggable.core 2 0 2008-06-17 12:27:51.154
!MESSAGE Missing imported package org.eclipse.jdt.internal.compiler.tool_0.0.0.
!SUBENTRY 2 org.eclipse.jdt.apt.pluggable.core 2 0 2008-06-17 12:27:51.154
!MESSAGE Missing imported package org.eclipse.jdt.internal.compiler.apt.dispatch_0.0.0.
!SUBENTRY 2 org.eclipse.jdt.apt.pluggable.core 2 0 2008-06-17 12:27:51.154
!MESSAGE Missing imported package org.eclipse.jdt.internal.compiler.apt.model_0.0.0.
!SUBENTRY 2 org.eclipse.jdt.apt.pluggable.core 2 0 2008-06-17 12:27:51.154
!MESSAGE Missing imported package org.eclipse.jdt.internal.compiler.apt.util_0.0.0.
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-06-17 12:27:51.154
!MESSAGE Bundle [email]update@plugins/org.eclipse.jdt.compiler.tool_1.0.1.v_793_R33x.jar[/email] [93] was not resolved.

(eclipse:3414): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(eclipse:3414): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(eclipse:3414): Gtk-CRITICAL **: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(eclipse:3414): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

(eclipse:3414): GLib-GObject-WARNING **: value "TRUE" of type `gboolean' is invalid or out of range for property `visible' of type `gboolean'

(eclipse:3414): Gtk-CRITICAL **: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(eclipse:3414): GLib-GObject-CRITICAL **: g_object_get: assertion `G_IS_OBJECT (object)' failed

(eclipse:3414): Gtk-WARNING **: Screen for GtkWindow not set; you must always set
a screen for a GtkWindow before using the window

(eclipse:3414): Gdk-CRITICAL **: gdk_pango_context_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(eclipse:3414): Pango-CRITICAL **: pango_context_set_font_description: assertion `context != NULL' failed

(eclipse:3414): Pango-CRITICAL **: pango_context_set_base_dir: assertion `context != NULL' failed

(eclipse:3414): Pango-CRITICAL **: pango_context_set_language: assertion `context != NULL' failed

(eclipse:3414): Pango-CRITICAL **: pango_layout_new: assertion `context != NULL' failed

(eclipse:3414): Pango-CRITICAL **: pango_layout_set_text: assertion `layout != NULL' failed

(eclipse:3414): Pango-CRITICAL **: pango_layout_set_attributes: assertion `layout != NULL' failed

(eclipse:3414): Pango-CRITICAL **: pango_layout_set_alignment: assertion `layout != NULL' failed

(eclipse:3414): Pango-CRITICAL **: pango_layout_set_ellipsize: assertion `PANGO_IS_LAYOUT (layout)' failed

(eclipse:3414): Pango-CRITICAL **: pango_layout_set_single_paragraph_mode: assertion `PANGO_IS_LAYOUT (layout)' failed

(eclipse:3414): Pango-CRITICAL **: pango_layout_set_width: assertion `layout != NULL' failed

(eclipse:3414): Pango-CRITICAL **: pango_layout_get_extents: assertion `layout != NULL' failed

(eclipse:3414): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(eclipse:3414): Gtk-CRITICAL **: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed

(eclipse:3414): Gtk-CRITICAL **: gtk_icon_size_lookup_for_settings: assertion `GTK_IS_SETTINGS (settings)' failed

(eclipse:3414): Gtk-WARNING **: Invalid icon size 6


(eclipse:3414): Gtk-CRITICAL **: gtk_icon_theme_load_icon: assertion `GTK_IS_ICON_THEME (icon_theme)' failed
Segmentation fault

---

### Post by jtreg on 2008-06-17
please help

---

### Post by tim_wright on 2008-06-17
You aren't going to get help any faster by pleading. Instead, the chances of people ignoring your thread is greatly increased.

---

### Post by jespdj on 2008-06-17
It sounds like Eclipse can't find a native library that it needs. Maybe this is because of a permissions problem. I've installed Eclipse by downloading it from the Eclipse website myself, and I noticed that the ownerships of the files were wrong after unpacking the .tar.gz. Do this:
```
sudo chown -R root:root /opt/eclipse
```
to make root the owner of /opt/eclipse and everything under it, and try running it again.

---

### Post by kpkeerthi on 2008-06-17
Install it from the repository.. So the dependencies are property take care of.

```
sudo aptitude install eclipse-platform eclipse-jdt
```

---

### Post by jtreg on 2008-06-17
Thanks guys ... I will try, tim_wright, you are a bit of a plonker.

---

### Post by tim_wright on 2008-06-17
/rant 

Dude, I'm giving you advice. Wether you regard that as offensive is up to you but the fact of the matter is that posting comments to bump your thread are immature and don't contribute to or speed up the resolution of your problem. Furthermore bothering me with private messages containing "If you cant be nice, keep your stupid comments to yourself." just reinforce my belief that you are an idiot. 

/end rant

---

