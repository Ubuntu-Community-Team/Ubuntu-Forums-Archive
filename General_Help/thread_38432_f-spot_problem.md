---
title: "f-spot problem"
date: 2005-05-31
forum: General Help
---

### Post by burlap on 2005-05-31
I can run f-spot only under English (POSIX, en_US) locale, with other (pl_PL, es_ES) I get the following error:```
Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in <0x00000> <unknown method>
in (wrapper managed-to-native) System.Object:__icall_wrapper_mono_struct_delete_old (intptr,intptr)
in (wrapper managed-to-native) Gtk.StockManager:gtk_stock_lookup (string,Gtk.StockItem&)
in <0x00017> Gtk.StockManager:Lookup (System.String stock_id, Gtk.StockItem item)
in <0x0004b> GtkUtil:MakeToolbarButton (Gtk.Toolbar toolbar, System.String stock_id, System.EventHandler e)
in <0x00131> MainWindow:.ctor (.Db db)
in <0x00134> Driver:Main (System.String[] args)
```
All mono-related packages come from backports. 

Is there any way to run f-spot under non-English locale without setting variables each time or editing scripts? (I can do it, but I would like to avoid it)

---

### Post by infinito on 2005-05-31
[QUOTE=burlap]I can run f-spot only under English (POSIX, en_US) locale, with other (pl_PL, es_ES) I get the following error:```
Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in <0x00000> <unknown method>
in (wrapper managed-to-native) System.Object:__icall_wrapper_mono_struct_delete_old (intptr,intptr)
in (wrapper managed-to-native) Gtk.StockManager:gtk_stock_lookup (string,Gtk.StockItem&)
in <0x00017> Gtk.StockManager:Lookup (System.String stock_id, Gtk.StockItem item)
in <0x0004b> GtkUtil:MakeToolbarButton (Gtk.Toolbar toolbar, System.String stock_id, System.EventHandler e)
in <0x00131> MainWindow:.ctor (.Db db)
in <0x00134> Driver:Main (System.String[] args)
```
All mono-related packages come from backports. 

Is there any way to run f-spot under non-English locale without setting variables each time or editing scripts? (I can do it, but I would like to avoid it)[/QUOTE]
 This problem is being followed here: [http://ubuntuforums.org/forumdisplay.php?f=47](http://ubuntuforums.org/forumdisplay.php?f=47)
It seems there's something worng with mono backports...

---

### Post by burlap on 2005-05-31
Thanks, I have seen you have also reported that to the mono-testing thread. These are my first experiences with mono, I kept myself far away not without a reason...

---

