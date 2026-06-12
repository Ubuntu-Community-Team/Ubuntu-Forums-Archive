---
title: "Docky Won't Start"
date: 2017-04-19
forum: General Help
---

### Post by emilward on 2017-04-19
I am using Xubuntu 16.04 so my apologies if this is in the wrong section. But, basically, Docky will not start. I installed it, added my apps, then I went into the settings to add "helpers" and when I tried to add the "Session Manager" helper, it closed. I tried to open it again but it wouldn't. I removed and reinstalled it via terminal but it would not start. I purged and reinstalled it via terminal and it still would not start. So I tried opening it up via terminal and got this output.

```
eric@eric-Satellite-U845:~$ docky
[Info  11:12:46.144] Docky version: 2.2.1.1 Release
[Info  11:12:46.145] Kernel version: 4.8.0.46
[Info  11:12:46.145] CLR version: 4.0.30319.17020
[Error 11:12:46.405] [SystemService] Could not initialize power manager dbus: 'Could not load type 'Docky.Services.SystemService+IUPowerProxy' from assembly 'DBus.Proxies, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null' because it is implements the inaccessible interface 'Docky.Services.SystemService+IUPower'.'
[Info  11:12:46.407] [SystemService]   at System.Reflection.Emit.TypeBuilder.CreateTypeInfo () <0x7f230f19c000 + 0x00884> in <filename unknown>:0 
  at System.Reflection.Emit.TypeBuilder.CreateType () <0x7f230f19bfe0 + 0x0000c> in <filename unknown>:0 
  at DBus.TypeImplementer.GetImplementation (System.Type declType) <0x400936b0 + 0x00283> in <filename unknown>:0 
  at DBus.BusObject.GetObject (DBus.Connection conn, System.String bus_name, DBus.ObjectPath object_path, System.Type declType) <0x40093510 + 0x00037> in <filename unknown>:0 
  at DBus.Connection.GetObject (System.Type type, System.String bus_name, DBus.ObjectPath path) <0x40092040 + 0x0007f> in <filename unknown>:0 
  at DBus.Connection.GetObject[T] (System.String bus_name, DBus.ObjectPath path) <0x40091fd0 + 0x00037> in <filename unknown>:0 
  at Docky.Services.SystemService.InitializeBattery () <0x400d4000 + 0x000b3> in <filename unknown>:0 
[Error 11:12:46.415] [SystemService] Could not initialize Network Manager dbus: 'Could not load type 'Docky.Services.SystemService+INetworkManagerProxy' from assembly 'DBus.Proxies, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null' because it is implements the inaccessible interface 'Docky.Services.SystemService+INetworkManager'.'
[Info  11:12:46.416] [SystemService]   at System.Reflection.Emit.TypeBuilder.CreateTypeInfo () <0x7f230f19c000 + 0x00884> in <filename unknown>:0 
  at System.Reflection.Emit.TypeBuilder.CreateType () <0x7f230f19bfe0 + 0x0000c> in <filename unknown>:0 
  at DBus.TypeImplementer.GetImplementation (System.Type declType) <0x400936b0 + 0x00283> in <filename unknown>:0 
  at DBus.BusObject.GetObject (DBus.Connection conn, System.String bus_name, DBus.ObjectPath object_path, System.Type declType) <0x40093510 + 0x00037> in <filename unknown>:0 
  at DBus.Connection.GetObject (System.Type type, System.String bus_name, DBus.ObjectPath path) <0x40092040 + 0x0007f> in <filename unknown>:0 
  at DBus.Connection.GetObject[T] (System.String bus_name, DBus.ObjectPath path) <0x40091fd0 + 0x00037> in <filename unknown>:0 
  at Docky.Services.SystemService.InitializeNetworkManager () <0x400db4c0 + 0x00117> in <filename unknown>:0 
[Info  11:12:46.445] [ThemeService] Setting theme: Matte
[Warn  11:12:46.480] [DesktopItemService] Could not find remap file '/home/eric/.local/share/docky/remaps.ini'!
[Info  11:12:46.735] [DockServices] Dock services initialized.
[Info  11:12:47.234] [PluginManager] Loaded "Session Manager".
[Error 11:12:47.239] [SystemService] Could not initialize needed dbus service: 'Could not load type 'SessionManager.SystemManager+IUPowerProxy' from assembly 'DBus.Proxies, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null' because it is implements the inaccessible interface 'SessionManager.SystemManager+IUPower'.'
[Info  11:12:47.239] [SystemService]   at System.Reflection.Emit.TypeBuilder.CreateTypeInfo () <0x7f230f19c000 + 0x00884> in <filename unknown>:0 
  at System.Reflection.Emit.TypeBuilder.CreateType () <0x7f230f19bfe0 + 0x0000c> in <filename unknown>:0 
  at DBus.TypeImplementer.GetImplementation (System.Type declType) <0x400936b0 + 0x00283> in <filename unknown>:0 
  at DBus.BusObject.GetObject (DBus.Connection conn, System.String bus_name, DBus.ObjectPath object_path, System.Type declType) <0x40093510 + 0x00037> in <filename unknown>:0 
  at DBus.Connection.GetObject (System.Type type, System.String bus_name, DBus.ObjectPath path) <0x40092040 + 0x0007f> in <filename unknown>:0 
  at DBus.Connection.GetObject[T] (System.String bus_name, DBus.ObjectPath path) <0x40091fd0 + 0x00037> in <filename unknown>:0 
  at SessionManager.SystemManager.Initialize () <0x40179cf0 + 0x000bb> in <filename unknown>:0 
Error while getting object for node in path '/Docky/ItemProvider'.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.IndexOutOfRangeException: Index was outside the bounds of the array.
  at Docky.Items.ProxyDockItem.ItemChanged () <0x4017b6e0 + 0x0027d> in <filename unknown>:0 
  at Docky.Items.ProxyDockItem..ctor (Docky.Items.AbstractDockItemProvider provider, IPreferences prefs) <0x4017b440 + 0x001b3> in <filename unknown>:0 
  at SessionManager.SessionManagerItem..ctor () <0x401796b0 + 0x0008f> in <filename unknown>:0 
  at SessionManager.SessionManagerItemProvider..ctor () <0x40179600 + 0x00033> in <filename unknown>:0 
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (System.Reflection.MonoCMethod,object,object[],System.Exception&)
  at System.Reflection.MonoCMethod.InternalInvoke (System.Object obj, System.Object[] parameters) <0x7f230f1ac8d0 + 0x0003f> in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.InternalInvoke (System.Object obj, System.Object[] parameters) <0x7f230f1ac8d0 + 0x00079> in <filename unknown>:0 
  at System.RuntimeType.CreateInstanceMono (Boolean nonPublic) <0x7f230effa560 + 0x00124> in <filename unknown>:0 
  at System.RuntimeType.CreateInstanceSlow (Boolean publicOnly, Boolean skipCheckThis, Boolean fillCache, System.Threading.StackCrawlMark& stackMark) <0x7f230effa510 + 0x00049> in <filename unknown>:0 
  at System.RuntimeType.CreateInstanceDefaultCtor (Boolean publicOnly, Boolean skipCheckThis, Boolean fillCache, System.Threading.StackCrawlMark& stackMark) <0x7f230effa2b0 + 0x0005c> in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) <0x7f230ef1adb0 + 0x000a1> in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type) <0x7f230ef1ac60 + 0x0000e> in <filename unknown>:0 
  at Mono.Addins.TypeExtensionNode.CreateInstance () <0x40178e40 + 0x0001f> in <filename unknown>:0 
  at Mono.Addins.InstanceExtensionNode.GetInstance () <0x40178dc0 + 0x00023> in <filename unknown>:0 
  at Mono.Addins.InstanceExtensionNode.GetInstance (System.Type expectedType) <0x40178d30 + 0x00017> in <filename unknown>:0 
  at Mono.Addins.ExtensionNode.GetChildObjectsInternal (System.Type arrayElementType, Boolean reuseCachedInstance) <0x40172710 + 0x00193> in <filename unknown>:0 
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.NullReferenceException: Object reference not set to an instance of an object
  at Docky.Items.ProxyDockItem.get_Square () <0x4019b330 + 0x00015> in <filename unknown>:0 
  at Docky.Items.AbstractDockItem.<QueueRedraw>m__0 () <0x4019a810 + 0x00018> in <filename unknown>:0 
  at GLib.Idle+IdleProxy.Handler () <0x4019a750 + 0x0003f> in <filename unknown>:0 
  at GLib.ExceptionManager.RaiseUnhandledException (System.Exception e, Boolean is_terminal) [0x00000] in <filename unknown>:0 
  at GLib.Idle+IdleProxy.Handler () [0x00000] in <filename unknown>:0 
  at Gtk.Application.gtk_main () [0x00000] in <filename unknown>:0 
  at Gtk.Application.Run () [0x00000] in <filename unknown>:0 
  at Docky.Docky.Main (System.String[] args) [0x00000] in <filename unknown>:0 
eric@eric-Satellite-U845:~$
```

---

### Post by RobGoss on 2017-04-19
You should use the code tags when posting results for any issues you're having it saves everyone from having to scrolling the post

---

### Post by emilward on 2017-04-19
Sorry. Not sure how to do that. Is there a button somewhere?

---

### Post by ajgreeny on 2017-04-19
To use **Code-Tags** for terminal output see my signature below for a **How-to**

Regarding your Docky problem, is there a configuration folder or file for Docky in your home somewhere?  I've never used it so I do not know but have a look in the hidden .config folder first to see if anything is there.

If you find something looking as if it is for docky just rename it as docky-backup by right clicking on it, choosing Rename.

You might find some files or folders in your home that look hopeful with command ```
locate -i docky | grep $USER
```

---

### Post by emilward on 2017-04-20
Okay, I got it. I purged docky again and then used catfish to search for any files & directories still lingering. I found some directories and config files. So I deleted them, logged out/in, then reinstalled docky. It's working like normal again. Thanks

---

### Post by mörgæs on 2017-04-20
Thanks for an attempt at marking the thread solved but better to use Thread Tools. This gives other people the option to see only solved threads when using the search page.

---

### Post by emilward on 2017-04-21
Yeah I clicked in Thread Tools but didn't see the option to mark it as solved there. I'll try again, thanks

---

### Post by mörgæs on 2017-04-21
Were you logged in when you opened the menu?

---

