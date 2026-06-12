---
title: "Monodevelop problems- won't start"
date: 2008-03-05
forum: General Help
---

### Post by natesully on 2008-03-05
I installed mondevelop on Gutsy, nothing out of the ordinary, and get this wonderful error when trying to start it.

Any Ideas?  Everything is up to date.

```

Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.MethodAccessException: Cannot invoke constructor of an abstract class.
  at <0x00000> <unknown method>
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] --- End of inner exception stack trace ---

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at MonoDevelop.Projects.Serialization.ClassDataType.Deserialize (MonoDevelop.Projects.Serialization.SerializationContext serCtx, System.Object mapData, MonoDevelop.Projects.Serialization.DataNode data) [0x00000] 
  at MonoDevelop.Projects.Serialization.CollectionDataType.Deserialize (MonoDevelop.Projects.Serialization.SerializationContext serCtx, System.Object mdata, MonoDevelop.Projects.Serialization.DataCollection items, System.Object collectionInstance, System.Object position) [0x00000] 
  at MonoDevelop.Projects.Serialization.CollectionDataType.Deserialize (MonoDevelop.Projects.Serialization.SerializationContext serCtx, System.Object mdata, MonoDevelop.Projects.Serialization.DataNode data) [0x00000] 
  at MonoDevelop.Projects.Serialization.DataContext.LoadConfigurationData (MonoDevelop.Projects.Serialization.SerializationContext serCtx, System.Type type, MonoDevelop.Projects.Serialization.DataNode data) [0x00000] 
  at MonoDevelop.Projects.Serialization.DataSerializer.Deserialize (System.Type type, MonoDevelop.Projects.Serialization.DataNode data) [0x00000] 
  at MonoDevelop.Projects.Serialization.XmlDataSerializer.Deserialize (System.Xml.XmlReader reader, System.Type type) [0x00000] 
  at MonoDevelop.Projects.Serialization.XmlDataSerializer.Deserialize (System.IO.TextReader reader, System.Type type) [0x00000] 
  at MonoDevelop.DesignerSupport.Toolbox.ToolboxList.LoadFromFile (System.String fileName) [0x00000] 
  at MonoDevelop.DesignerSupport.ToolboxService.LoadUserToolbox (System.String fileName) [0x00000] 
  at MonoDevelop.DesignerSupport.DesignerSupportService.get_ToolboxService () [0x00000] 
  at MonoDevelop.DesignerSupport.ToolboxPad..ctor () [0x00000] 
  at <0x00000> <unknown method>
  at (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] --- End of inner exception stack trace ---

  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] 
  at Mono.Addins.RuntimeAddin.CreateInstance (System.String typeName, Boolean throwIfNotFound) [0x00000] 
  at MonoDevelop.Ide.Codons.PadCodon.CreatePad () [0x00000] 
  at MonoDevelop.Ide.Codons.PadCodon.get_PadContent () [0x00000] 
  at MonoDevelop.Ide.Gui.SdiWorkbenchLayout.CreatePadContent (Boolean force, MonoDevelop.Ide.Codons.PadCodon padCodon, MonoDevelop.Ide.Gui.PadWindow window, Gdl.DockItem item) [0x00000] 
  at MonoDevelop.Ide.Gui.SdiWorkbenchLayout+<>c__CompilerGenerated44.<>c__AnonymousMethod45 (System.Object +21, System.EventArgs +22) [0x00000] 
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void_object_EventArgs (object,System.EventArgs)
  at GLib.Signal.voidObjectCallback (IntPtr handle, IntPtr gch) [0x00000] 

   at GLib.ExceptionManager.RaiseUnhandledException ()
   at GLib.Signal.voidObjectCallback ()
   at GLib.Signal.voidObjectCallback ()
   at Gtk.Widget.gtk_widget_map ()
   at Gtk.Widget.gtk_widget_map ()
   at Gtk.Widget.Map ()
   at Gdl.DockItem.OnMapped ()
   at Gtk.Widget.mapped_cb ()
   at Gtk.Widget.mapped_cb ()
   at Gtk.Widget.gtk_widget_map ()
   at Gtk.Widget.gtk_widget_map ()
   at Gtk.Widget.Map ()
   at Gdl.DockItem.OnMapped ()
   at Gtk.Widget.mapped_cb ()
   at Gtk.Widget.mapped_cb ()
   at Gtk.Widget.gtk_widget_map ()
   at Gtk.Widget.gtk_widget_map ()
   at Gtk.Widget.Map ()
   at Gdl.DockItem.OnMapped ()
   at Gtk.Widget.mapped_cb ()
   at Gtk.Widget.mapped_cb ()
   at Gtk.Widget.gtk_widget_map ()
   at Gtk.Widget.gtk_widget_map ()
   at Gtk.Widget.Map ()
   at Gdl.DockItem.OnMapped ()
   at Gtk.Widget.mapped_cb ()
   at Gtk.Widget.mapped_cb ()
   at Gtk.Container.gtksharp_container_invoke_gtk_callback ()
   at Gtk.Container.gtksharp_container_invoke_gtk_callback ()
   at Gtk.Container+CallbackInvoker.Invoke ()
   at Gtk.Container+CallbackInvoker.Invoke ()
   at System.MulticastDelegate.invoke_void_Widget ()
   at Gdl.Dock.ForAll ()
   at Gtk.Container.Forall_cb ()
   at Gtk.Container.Forall_cb ()
   at GLib.Object.g_signal_chain_from_overridden ()
   at GLib.Object.g_signal_chain_from_overridden ()
   at Gtk.Widget.OnMapped ()
   at Gdl.Dock.OnMapped ()
   at Gtk.Widget.mapped_cb ()
   at Gtk.Widget.mapped_cb ()
   at GLib.Object.g_object_set_property ()
   at GLib.Object.g_object_set_property ()
   at GLib.Object.SetProperty ()
   at Gtk.Widget.set_Visible ()
   at MonoDevelop.Ide.Gui.Workbench.Show ()
   at MonoDevelop.Ide.Gui.IdeApp.Initialize ()
   at MonoDevelop.Ide.Gui.IdeStartup.Run ()
   at MonoDevelop.Core.ApplicationService.StartApplication ()
   at MonoDevelop.Startup.SharpDevelopMain.Main ()

```

---

### Post by kellemes on 2008-03-05
Can't help you here..

Just suggest installing a more up to date version of Monodevelop, [getdeb]("http://www.getdeb.net/app/MonoDevelop") offers version 0.16 or you can [compile/install the newest]("http://www.monodevelop.com/Download"), which is 0.19

I can't promise this will fix this issue by the way..

---

### Post by natesully on 2008-03-05
Good call, not only is ubuntu's package horribly out of date but that fixed my problems.

---

