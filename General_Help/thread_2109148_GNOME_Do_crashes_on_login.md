---
title: "GNOME Do crashes on login"
date: 2013-01-26
forum: General Help
---

### Post by Zvlwab on 2013-01-26
On my laptop, the option "Start GNOME Do at login." is enabled in the preferences, but the program doesn't start. However, if I start the program manually, it runs fine.
The following appears in my ~/.xsession-errors
```
System.NullReferenceException: Object reference not set to an instance of an object
  at Do.Interface.PositionWindow.GetMonitor () [0x00000] in <filename unknown>:0
  at Do.Interface.PositionWindow+<UpdatePosition>c__AnonStorey3.<>m__8 (System.Object , System.EventArgs ) [0x00000] in <filename unknown>:0
  at Gtk.Application+InvokeCB.Invoke () [0x00000] in <filename unknown>:0
  at GLib.Timeout+TimeoutProxy.Handler () [0x00000] in <filename unknown>:0
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at GLib.Timeout+TimeoutProxy.Handler()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Do.Do.Main(System.String[] args)
```
On my pc with the same setup it just starts like it should though.

---

