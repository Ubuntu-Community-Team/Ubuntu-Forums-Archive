---
title: "Monodevelop not starting"
date: 2006-08-18
forum: General Help
---

### Post by kiaton on 2006-08-18
Monodevelop is not starting and returns this:
```

&#65279;While loading layout: don't know how to create a dock object whose nick is ''

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries
used by your application.
=================================================================

Stacktrace:

in (wrapper managed-to-native) Gtk.Notebook:gtk_notebook_insert_page (intptr,intptr,intptr,int) <0x4>
in (wrapper managed-to-native) Gtk.Notebook:gtk_notebook_insert_page (intptr,intptr,intptr,int) <0xffffffdb>
in Gtk.Notebook:InsertPage (Gtk.Widget,Gtk.Widget,int) <0x8b>
in MonoDevelop.Ide.Gui.SdiWorkbenchLayout:ShowView (MonoDevelop.Ide.Gui.IViewContent) <0x26d>
in MonoDevelop.Ide.Gui.DefaultWorkbench:ShowView (MonoDevelop.Ide.Gui.IViewContent,bool) <0x224>
in MonoDevelop.Ide.Gui.Workbench:OpenDocument (MonoDevelop.Ide.Gui.IViewContent,bool) <0x1c>
in MonoDevelop.WelcomePage.ShowWelcomePageOnStartUpHandler:Run () <0x5e>
in (wrapper runtime-invoke) System.Object:runtime_invoke_void (object,intptr,intptr,intptr) <0x2ce241f>
in (wrapper managed-to-native) System.Reflection.MonoMethod:InternalInvoke (object,object[]) <0x4>
in (wrapper managed-to-native) System.Reflection.MonoMethod:InternalInvoke (object,object[]) <0xfffffc75>
in System.Reflection.MonoMethod:Invoke (object,System.Reflection.BindingFlags,System.Reflection.Binder,object[],System.Globalization.CultureInfo) <0x8d>
in System.Reflection.MethodBase:Invoke (object,object[]) <0x1a>
in MonoDevelop.Ide.Gui.IdeApp:Initialize (MonoDevelop.Core.IProgressMonitor) <0x4e8>
in MonoDevelop.Ide.Gui.IdeStartup:Run (string[]) <0x8ad>
in MonoDevelop.Core.AddIns.AddInService:StartApplication (string,string[]) <0x169>
in MonoDevelop.Startup.SharpDevelopMain:Main (string[]) <0x39>
in (wrapper runtime-invoke) System.Object:runtime_invoke_int_string[] (object,intptr,intptr,intptr) <0xac8bef>

Native stacktrace:

        /usr/lib/libmono.so.0(mono_handle_native_sigsegv+0xe3) [0xb7e2543f]
        /usr/lib/libmono.so.0 [0xb7de703e]
        [0xffffe440]
        /usr/lib/firefox/libgtkembedmoz.so [0xb45369e9]
        /usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x43) [0xb616e423]
        /usr/lib/libgobject-2.0.so.0 [0xb616216f]
        /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x11e) [0xb616279f]
        /usr/lib/libgobject-2.0.so.0 [0xb61715cc]
        /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x6b0) [0xb6172b19]
        /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29) [0xb6172e89]
        /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_realize+0xa9) [0xb66e53d1]
        /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_map+0xd1) [0xb66e558f]
        /usr/lib/libgtk-x11-2.0.so.0 [0xb65754a7]
        /usr/lib/libgtk-x11-2.0.so.0 [0xb65befc5]
        /usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0x65) [0xb6573c36]
        /usr/lib/libgtk-x11-2.0.so.0 [0xb65754e0]
        /usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x43) [0xb616e423]
        /usr/lib/libgobject-2.0.so.0 [0xb616216f]
        /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x11e) [0xb616279f]
        /usr/lib/libgobject-2.0.so.0 [0xb61715cc]
        /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x6b0) [0xb6172b19]
        /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29) [0xb6172e89]
        /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_map+0x72) [0xb66e5530]
        /usr/lib/libgtk-x11-2.0.so.0 [0xb65754a7]
        /usr/lib/libgtk-x11-2.0.so.0 [0xb65befc5]
        /usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0x65) [0xb6573c36]
        /usr/lib/libgtk-x11-2.0.so.0 [0xb65754e0]
        /usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x43) [0xb616e423]
        /usr/lib/libgobject-2.0.so.0 [0xb616216f]
        /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x11e) [0xb616279f]
        /usr/lib/libgobject-2.0.so.0 [0xb61715cc]
        /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x6b0) [0xb6172b19]
        /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x29) [0xb6172e89]
        /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_map+0x72) [0xb66e5530]
        /usr/lib/libgtk-x11-2.0.so.0(gtk_widget_set_parent+0x257) [0xb66e5ab0]
        /usr/lib/libgtk-x11-2.0.so.0(gtk_notebook_insert_page_menu+0x20a) [0xb6617a17]
        /usr/lib/libgtk-x11-2.0.so.0(gtk_notebook_insert_page+0xeb) [0xb6617cee]
        [0xb466465e]
        [0xb4664604]
        [0xb4490676]
        [0xb449003d]
        [0xb448fded]
        [0xb465680f]
        [0xb5122041]
        /usr/lib/libmono.so.0 [0xb7e04438]
        /usr/lib/libmono.so.0(mono_runtime_invoke+0x33) [0xb7e66eed]
        /usr/lib/libmono.so.0(mono_runtime_invoke_array+0x161) [0xb7e6ae07]
        /usr/lib/libmono.so.0 [0xb7e71852]
        [0xb6fe10ac]
        [0xb6fe0cf6]
        [0xb6a2ee2b]
        [0xb56484c9]
        [0xb6ebc676]
        [0xb6fec99a]
        [0xb733b932]
        [0xb733b874]
        /usr/lib/libmono.so.0 [0xb7e04438]
        /usr/lib/libmono.so.0(mono_runtime_invoke+0x33) [0xb7e66eed]
        /usr/lib/libmono.so.0(mono_runtime_exec_main+0xa8) [0xb7e69ac9]
        /usr/lib/libmono.so.0(mono_runtime_run_main+0x188) [0xb7e6cbf0]
        /usr/lib/libmono.so.0(mono_jit_exec+0x90) [0xb7e16b5e]
        /usr/lib/libmono.so.0(mono_main+0x962) [0xb7e1754f]
        /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xd2) [0xb7bb3ea2]
        /usr/bin/mono [0x8048459]

```

What's the problem?

Thanks.

---

### Post by helmet on 2006-08-26
i am also experiencing this...unfortunately i have no solution

---

### Post by qodsec on 2006-08-27
same thing here. Bummer:mad:

---

### Post by binks on 2006-08-28
run this cmd 

```
sudo mdtool gsetup
```

and switch off/uninstall the welcome page
binks

---

### Post by ekerazha on 2006-10-20
> **binks said:**
> run this cmd 

```
sudo mdtool gsetup
```

and switch off/uninstall the welcome page
binks

It works!

However... this should be fixed before Ubuntu 6.10 final release.

---

