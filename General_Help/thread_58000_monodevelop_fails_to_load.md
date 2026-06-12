---
title: "monodevelop fails to load"
date: 2005-08-18
forum: General Help
---

### Post by domstyledesign on 2005-08-18
monodevelop fails to load.  installed from apt.  i get the loading splash, but it disappears while "Initializing Addin Services..."

```
** (MonoDevelop:9503): WARNING **: The following assembly referenced from /usr/lib/monodevelop/bin/MonoDevelop.Base.dll could not be loaded:
     Assembly:   monodoc    (assemblyref_index=8)
     Version:    1.0.0.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/monodevelop/bin).


** (MonoDevelop:9503): WARNING **: The class Monodoc.RootTree could not be loaded, used in /usr/lib/monodevelop/bin/MonoDevelop.Base.dll (token 0x01000063)

** (MonoDevelop:9503): WARNING **: Missing method LoadTree in assembly /usr/lib/monodevelop/bin/MonoDevelop.Base.dll, type Monodoc.RootTree
Loading error, please reinstall :
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
in <0x00000> <unknown method>
in (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
in <0x0006f> System.Reflection.MonoCMethod:Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)--- End of inner exception stack trace ---

in <0x00104> System.Reflection.MonoCMethod:Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
in <0x00019> System.Reflection.MonoCMethod:Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
in <0x00032> System.Reflection.ConstructorInfo:Invoke (System.Object[] parameters)
in <0x000e2> System.Activator:CreateInstance (System.Type type, Boolean nonPublic)
in <0x0000c> System.Activator:CreateInstance (System.Type type)
in <0x0003a> System.Reflection.Assembly:CreateInstance (System.String typeName, Boolean ignoreCase)
in <0x00012> System.Reflection.Assembly:CreateInstance (System.String typeName)
in <0x000af> MonoDevelop.Core.AddIns.AddIn:CreateObject (System.String className)
in <0x00030> MonoDevelop.Core.AddIns.Codons.ClassCodon:BuildItem (System.Object owner, System.Collections.ArrayList subItems, MonoDevelop.Core.AddIns.Conditions.ConditionCollection conditions)
in <0x0014f> MonoDevelop.Core.AddIns.DefaultAddInTreeNode:BuildChildItems (System.Object caller)
in <0x0004c> MonoDevelop.Core.Services.ServiceManager:InitializeServicesSubsystem (System.String servicesPath)
in <0x00640> MonoDevelop.SharpDevelopMain:Main (System.String[] args)
```

i've read that monodevelop isn't very stable yet, but i didn't expect this.  any ideas?

---

### Post by domstyledesign on 2005-08-19
*bump*

anyone?  reinstalling didn't help!

---

### Post by domstyledesign on 2005-08-20
resolved.

dependency issue.


[http://www.ubuntuforums.org/showthread.php?t=50034](http://www.ubuntuforums.org/showthread.php?t=50034)

---

### Post by Raptor Ramjet on 2005-09-14
[QUOTE=domstyledesign]monodevelop fails to load.  installed from apt.  i get the loading splash, but it disappears while "Initializing Addin Services..."

```
** (MonoDevelop:9503): WARNING **: The following assembly referenced from /usr/lib/monodevelop/bin/MonoDevelop.Base.dll could not be loaded:
     Assembly:   monodoc    (assemblyref_index=8)
     Version:    1.0.0.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/monodevelop/bin).


** (MonoDevelop:9503): WARNING **: The class Monodoc.RootTree could not be loaded, used in /usr/lib/monodevelop/bin/MonoDevelop.Base.dll (token 0x01000063)

** (MonoDevelop:9503): WARNING **: Missing method LoadTree in assembly /usr/lib/monodevelop/bin/MonoDevelop.Base.dll, type Monodoc.RootTree
Loading error, please reinstall :
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
in <0x00000> <unknown method>
in (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
in <0x0006f> System.Reflection.MonoCMethod:Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)--- End of inner exception stack trace ---

in <0x00104> System.Reflection.MonoCMethod:Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
in <0x00019> System.Reflection.MonoCMethod:Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
in <0x00032> System.Reflection.ConstructorInfo:Invoke (System.Object[] parameters)
in <0x000e2> System.Activator:CreateInstance (System.Type type, Boolean nonPublic)
in <0x0000c> System.Activator:CreateInstance (System.Type type)
in <0x0003a> System.Reflection.Assembly:CreateInstance (System.String typeName, Boolean ignoreCase)
in <0x00012> System.Reflection.Assembly:CreateInstance (System.String typeName)
in <0x000af> MonoDevelop.Core.AddIns.AddIn:CreateObject (System.String className)
in <0x00030> MonoDevelop.Core.AddIns.Codons.ClassCodon:BuildItem (System.Object owner, System.Collections.ArrayList subItems, MonoDevelop.Core.AddIns.Conditions.ConditionCollection conditions)
in <0x0014f> MonoDevelop.Core.AddIns.DefaultAddInTreeNode:BuildChildItems (System.Object caller)
in <0x0004c> MonoDevelop.Core.Services.ServiceManager:InitializeServicesSubsystem (System.String servicesPath)
in <0x00640> MonoDevelop.SharpDevelopMain:Main (System.String[] args)
```

i've read that monodevelop isn't very stable yet, but i didn't expect this.  any ideas?[/QUOTE]
 Hello,

Well I don't know if this will be of use but I've just upgraded MonoDevelop via synaptic after which it failed to load.  It was getting as far as showing the "Loading MonoDevelop Workbench" message on the splash screen but then it was just dissapearing.  

A small bit of investigation then revealed that attempting to run "monodevelop" from a terminal produced the following:

2005-09-14 20:48:26,111 [-1210246272] INFO  MonoDevelop.Services.ILoggingService [(null)] - Reading /home/ramjet/.config/MonoDevelop/CodeCompletionData/mscorlib_1.0.5000.0_b77a5c561934e089.pidb
2005-09-14 20:48:26,223 [-1210246272] INFO  MonoDevelop.Services.ILoggingService [(null)] - WARNING Could not find stock Icons.16x16.FindPrevIcon
2005-09-14 20:48:26,237 [-1210246272] INFO  MonoDevelop.Services.ILoggingService [(null)] - WARNING Could not find stock gtk-stop
2005-09-14 20:48:26,266 [-1210246272] INFO  MonoDevelop.Services.ILoggingService [(null)] - Creating DefaultWorkbench
Loading error, please reinstall :
System.NullReferenceException: Object reference not set to an instance of an object
in <0x00111> Gdl.DockLayout:SetupObject (System.Xml.XmlNode node)
in <0x00097> Gdl.DockLayout:RecursiveBuild (System.Xml.XmlNode parentNode, Gdl.DockObject parent)
in <0x0015d> Gdl.DockLayout:Load (System.Xml.XmlNode node)
in <0x0006d> Gdl.DockLayout:LoadLayout (System.String name)
in <0x000b0> MonoDevelop.Gui.SdiWorkbenchLayout:set_CurrentLayout (System.String value)
in <0x001ca> MonoDevelop.Gui.SdiWorkbenchLayout:SwitchContext (MonoDevelop.Gui.WorkbenchContext ctxt)
in <0x00296> MonoDevelop.Gui.SdiWorkbenchLayout:CreateDefaultLayout ()
in <0x00640> MonoDevelop.Gui.SdiWorkbenchLayout:Attach (IWorkbench wb)
in <0x00050> MonoDevelop.Gui.DefaultWorkbench:set_WorkbenchLayout (IWorkbenchLayout value)
in <0x00037> MonoDevelop.Gui.WorkbenchSingleton:SetWbLayout ()
in <0x00007> MonoDevelop.Gui.WorkbenchSingleton:CreateWorkspace ()
in <0x00044> MonoDevelop.Commands.InitializeWorkbenchCommand:Run ()
in <0x007ac> MonoDevelop.SharpDevelopMain:Main (System.String[] args)

So after a quick peruse of the errors  I tried deleting my configuration data by calling "rm ~/.config/MonoDevelop", tried MonoDevelop again and it now loads again.

However this doesn't really look related to your error but maybe you could try doing the same thing ?  And if that fails I'd go for removing then reinstalling MonoDevelop (I know this is a bit of a "Microsoft" approach to the problem but it may work ;)

Additionally when upgrading SharpDevelop on Windows (on which monodevelop is based) the usual advice is to remove the program and perform a clean install.

Just my tuppence worth.

P.S.  Apologies too for having edited your original post as I actually tried to reply but made a speeling mistak (or ten) and when I went to edit my post it put me into edit mode on the whole thing ?

---

