---
title: "Banshee 0.12.1 make error on DAAP plugin"
date: 2007-04-16
forum: General Help
---

### Post by jfinkels on 2007-04-16
I posted this to the Banshee mailing list but no response (they're no ubuntuforums.org). Downloaded svn version of Banshee (same error happens on stable release version), when make gets to the DAAP plugin, I get this error:
```

Making all in Banshee.Plugins.Daap
make[4]: Entering directory `/home/jeff/src/banshee/src/Plugins/Banshee.Plugins.Daap'
MONO_PATH=../../../ext/dbus-sharp /usr/bin/gmcs -debug -nowarn:0278 -r:../../../src/Core/Banshee.Base/Banshee.Base.dll -r:../../../src/Core/Banshee.Widgets/Banshee.Widgets.dll -target:library -out:Banshee.Plugins.Daap.dll  -r:/usr/local/lib/mono/avahi-sharp/avahi-sharp.dll   -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/pango-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/atk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gdk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gtk-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glib-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gnome-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/art-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gnome-vfs-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/glade-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.0/gconf-sharp.dll -r:/usr/lib/pkgconfig/../../lib/mono/gtk-sharp-2.
 0/gconf-sharp-peditors.dll   -r:Mono.Posix -r:ICSharpCode.SharpZipLib -r:System.Web -resource:./daap-sharp/content-codes,content-codes ../../../src/AssemblyInfo.cs ./DaapPlugin.cs ./DaapCore.cs ./DaapContainerSource.cs ./DaapSource.cs ./DaapTrackInfo.cs ./DaapLoginDialog.cs ./DatabaseProxy.cs ./DaapPlaylistSource.cs ./DaapProxyWebServer.cs ./DaapConfigPage.cs ./DaapErrorView.cs ./daap-sharp/*.cs ./daap-sharp/Mono.Zeroconf/*.cs
error CS0006: Cannot find assembly `/usr/local/lib/mono/avahi-sharp/avahi-sharp.dll'
Log: 

Compilation failed: 1 error(s), 0 warnings
make[4]: *** [Banshee.Plugins.Daap.dll] Error 1
make[4]: Leaving directory `/home/jeff/src/banshee/src/Plugins/Banshee.Plugins.Daap'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/jeff/src/banshee/src/Plugins'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jeff/src/banshee/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jeff/src/banshee'
make: *** [all] Error 2

```
I have avahi-sharp installed, and although there is a directory at /usr/local/lib/mono/ , there is no directory at /usr/local/lib/mono/avahi-sharp. Has anyone experienced a similar problem?

Ubuntu 6.10, x86.

---

### Post by thephotoman on 2007-04-18
Run this and try the build:

apt-get build-dep banshee-daap

---

### Post by jfinkels on 2007-04-18
> **thephotoman said:**
> Run this and try the build:

apt-get build-dep banshee-daap

Tried it that way, still no go. Thanks though.

---

