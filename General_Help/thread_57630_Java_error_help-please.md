---
title: "Java error help-please"
date: 2005-08-17
forum: General Help
---

### Post by rjwood on 2005-08-17
Can anyone help with this?
Exception in thread "main" java.lang.ClassFormatError: erroneous class name
   at java.lang.VMClassLoader.defineClass(java.lang.ClassLoader, java.lang.String, byte[], int, int, java.security.ProtectionDomain) (/usr/lib/libgcj.so.5.0.0)
   at java.lang.ClassLoader.defineClass(java.lang.String, byte[], int, int, java.security.ProtectionDomain) (/usr/lib/libgcj.so.5.0.0)
   at java.security.SecureClassLoader.defineClass(java.lang.String, byte[], int, int, java.security.CodeSource) (/usr/lib/libgcj.so.5.0.0)
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.5.0.0)
   at gnu.gcjwebplugin.AppletClassLoader.findClass(java.lang.String) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.5.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.5.0.0)
   at gnu.gcjwebplugin.AppletViewer.createApplet(gnu.gcjwebplugin.AppletTag) (Unknown Source)
   at gnu.gcjwebplugin.PluginAppletWindow.setHandle(long) (Unknown Source)
   at gnu.gcjwebplugin.PluginAppletViewer.start(java.io.InputStream, java.io.OutputStream) (Unknown Source)
   at gnu.gcjwebplugin.AppletViewer.main(java.lang.String[]) (Unknown Source)
thanks in advance

---

