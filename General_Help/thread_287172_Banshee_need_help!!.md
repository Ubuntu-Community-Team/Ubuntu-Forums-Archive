---
title: "Banshee need help!!"
date: 2006-10-28
forum: General Help
---

### Post by gorded on 2006-10-28
OK, this problem is really starting to piss me off, I used the following command to install banshee and its plugins.

```
sudo aptitude install banshee banshee-official-plugins
```

i asked to dowload these other packages

```
banshee banshee-official-plugins binfmt-support cli-common 
  gnome-volume-manager gstreamer0.10-gnomevfs gstreamer0.10-plugins-ugly 
  gthumb liba52-0.7.4 libdvdread3 libgconf2.0-cil libglade2.0-cil 
  libglib2.0-cil libgnome2.0-cil libgphoto2-2 libgphoto2-port0 
  libgtk2.0-cil libgtkhtml3.8-15 libid3tag0 libipoddevice0 libmad0 
  libmono-cairo1.0-cil libmono-cairo2.0-cil libmono-corlib1.0-cil 
  libmono-corlib2.0-cil libmono-data-tds1.0-cil libmono-data-tds2.0-cil 
  libmono-security1.0-cil libmono-security2.0-cil libmono-sharpzip0.84-cil 
  libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data1.0-cil 
  libmono-system-data2.0-cil libmono-system-web1.0-cil 
  libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil 
  libmono0 libmono1.0-cil libmono2.0-cil libmpeg2-4 libmusicbrainz4c2a 
  libnjb5 libsgutils1 libsidplay1 libsqlite3-0 mono-common mono-gac 
  mono-jit mono-runtime sg3-utils totem totem-gstreamer totem-mozilla 
```

I said yes, and it went about and did its thing, then i come back and run

```
banshee
```

and the splash screen starts up all nice and the half way through at initializing audio it stops, the massage i got in the terminal is as follows

```
Warning: [28/10/2006 2:28:12 PM] (Cannot connect to NetworkManager) - An available working network connection will be assumed
Creating track table
Creating playlists table
Creating playlistentries table

```

Has any one had this problem and know howto fix it, i am open to almost any solution.

Thanks

---

### Post by beerfan on 2006-10-28
What release? Xubuntu 6.06?

---

### Post by gorded on 2006-10-28
6.10

---

### Post by gorded on 2006-10-28
I went to the banshee hompage and found this to get further imformation 

```
mono --debug /usr/lib/banshee/banshee.exe
```

and it produced

```
libbanshee
System.DllNotFoundException: libbanshee
  at (wrapper managed-to-native) Banshee.BansheeEntry:banshee_dbus_compat_thread_init ()
  at Banshee.BansheeEntry.Startup (System.String[] args) [0x00000] in /build/buildd/banshee-0.11.1/src/Main.cs:51 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_string[] (string[])
  at Banshee.Gui.CleanRoomStartup.Startup (Banshee.Gui.StartupInvocationHandler startup, System.String[] args) [0x00045] in /build/buildd/banshee-0.11.1/src/Banshee.Base/Gui/CleanRoomStartup.cs:54 

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
  at Banshee.Base.Branding.get_ApplicationIconName () [0x00000] in /build/buildd/banshee-0.11.1/src/Banshee.Base/Branding.cs:104 
  at Banshee.Base.IconThemeUtils.SetWindowIcon (Gtk.Window window) [0x00000] in /build/buildd/banshee-0.11.1/src/Banshee.Base/IconThemeUtils.cs:105 
  at Banshee.Gui.Dialogs.ExceptionDialog..ctor (System.Exception e) [0x001f0] in /build/buildd/banshee-0.11.1/src/Banshee.Base/Gui/ExceptionDialog.cs:110 
  at Banshee.Gui.CleanRoomStartup.Startup (Banshee.Gui.StartupInvocationHandler startup, System.String[] args) [0x0006b] in /build/buildd/banshee-0.11.1/src/Banshee.Base/Gui/CleanRoomStartup.cs:60 
  at Banshee.BansheeEntry.Main (System.String[] args) [0x00000] in /build/buildd/banshee-0.11.1/src/Main.cs:43 

```

Maybe that can help

---

### Post by gorded on 2006-10-28
Ok yeah, i got this to work, I had to go to download the newest version of banshee 0.11.2 and compile , ipod-sharp , liipoddevice banshee and the official plugins from source.

Calling all MOTU can the newest release be made into .debs for the universe.

Thanks

---

### Post by beerfan on 2006-10-28
> **gorded said:**
> Calling all MOTU can the newest release be made into .debs for the universe.

Good luck with that. They'll probably have you file a bug to have it backported and then refuse to do it anyway. Canonical doesn't upgrade app versions once they've been released :-(

[Edit: I just noticed you said for Universe. Just ignore my ranting.]

---

