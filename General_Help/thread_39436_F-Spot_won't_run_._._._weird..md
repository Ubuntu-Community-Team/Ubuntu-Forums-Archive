---
title: "F-Spot won't run . . . weird."
date: 2005-06-04
forum: General Help
---

### Post by GTKpower on 2005-06-04
I instralled F-Spot through Synaptic today.  Normal enough.

But it won't run.  I get this in the console:

[B](f-spot:19791): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in <0x00000> <unknown method>
in (wrapper managed-to-native) System.Object:__icall_wrapper_mono_struct_delete_old (intptr,intptr)
in (wrapper managed-to-native) Gtk.StockManager:gtk_stock_lookup (string,Gtk.StockItem&)
in <0x00017> Gtk.StockManager:Lookup (System.String stock_id, Gtk.StockItem item)
in <0x0004b> GtkUtil:MakeToolbarButton (Gtk.Toolbar toolbar, System.String stock_id, System.EventHandler e)
in <0x00177> MainWindow:.ctor (.Db db)
in <0x00134> Driver:Main (System.String[] args)
[/B]

I need a drink.

---

