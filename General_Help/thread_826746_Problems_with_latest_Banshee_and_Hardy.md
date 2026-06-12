---
title: "Problems with latest Banshee and Hardy"
date: 2008-06-12
forum: General Help
---

### Post by _sAm_ on 2008-06-12
Hi , I want to try the latest version of Banshee but get an error.

This is what I have done;
I followed this site; [https://edge.launchpad.net/~banshee-team/+archive](https://edge.launchpad.net/~banshee-team/+archive) and add the two lines for apt sources.list for Hardy, and did the update. Then I run sudo apt-get install banshee-1 

When I try to start Banshee this error appear:

> An unhandled exception was thrown: duplicate column name: ExternalID
  at Mono.Data.SqliteClient.SqliteCommand.GetNextStatement (IntPtr pzStart, System.IntPtr& pzTail, System.IntPtr& pStmt) [0x00000] 

  at Mono.Data.SqliteClient.SqliteCommand.ExecuteReader (CommandBehavior behavior, Boolean want_results, System.Int32& rows_affected) [0x00000] 

  at Mono.Data.SqliteClient.SqliteCommand.ExecuteNonQuery () [0x00000] 

  at Hyena.Data.Sqlite.HyenaSqliteCommand.Execute (Hyena.Data.Sqlite.HyenaSqliteConnection hconnection, Mono.Data.SqliteClient.SqliteConnection connection) [0x00093] in /build/buildd/banshee-1-1.0.0/src/Libraries/Hyena/Hyena.Data.Sqlite/HyenaSqliteCommand.cs:116 

Exception has been thrown by the target of an invocation.



  at System.Reflection.MonoMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 

  at System.Reflection.MethodBase.Invoke (System.Object obj, System.Object[] parameters) [0x00000] 

  at Banshee.Database.BansheeDbFormatMigrator.InnerMigrate () [0x000ae] in /build/buildd/banshee-1-1.0.0/src/Core/Banshee.Services/Banshee.Database/BansheeDbFormatMigrator.cs:176 

  at Banshee.Database.BansheeDbFormatMigrator.Migrate () [0x00018] in /build/buildd/banshee-1-1.0.0/src/Core/Banshee.Services/Banshee.Database/BansheeDbFormatMigrator.cs:136 

Exception has been thrown by the target of an invocation.



  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 

  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 

  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 

  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 

  at System.Activator.CreateInstance (System.Type type) [0x00000] 

  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in /build/buildd/banshee-1-1.0.0/src/Core/Banshee.ThickClient/Banshee.Gui/GtkBaseClient.cs:55 

  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00048] in /build/buildd/banshee-1-1.0.0/src/Libraries/Hyena.Gui/Hyena.Gui/CleanRoomStartup.cs:54 



.NET Version: 2.0.50727.42
OS Version: Unix 2.6.24.18
Assembly Version Information:
System.Transactions (2.0.0.0)
System.Xml (2.0.0.0)
System.Data (2.0.0.0)
Mono.Data.SqliteClient (2.0.0.0)
Mono.Addins (0.3.0.0)
atk-sharp (2.12.0.0)
Hyena.Gui (1.0.0.12614)
NDesk.DBus.Proxies (0.0.0.0)
Mono.Posix (2.0.0.0)
NDesk.DBus.GLib (1.0.0.0)
NDesk.DBus (1.0.0.0)
gtk-sharp (2.12.0.0)
Hyena (1.0.0.12613)
System (2.0.0.0)
gdk-sharp (2.12.0.0)
glib-sharp (2.12.0.0)
Banshee.Core (1.0.0.12618)
Banshee.Services (1.0.0.12619)
Banshee.ThickClient (1.0.0.12622)
Nereid (1.0.0.12623)
mscorlib (2.0.0.0)

Platform Information: Linux 2.6.24-18-server i686 unknown GNU/Linux

Disribution Information:
[/etc/lsb-release]
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04"
[/etc/debian_version]
lenny/sid


I am using Ubuntu 8.04(32 bits).

---

