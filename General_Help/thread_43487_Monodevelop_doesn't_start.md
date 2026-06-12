---
title: "Monodevelop doesn't start"
date: 2005-06-22
forum: General Help
---

### Post by mgoellner on 2005-06-22
Hi,

I have my first Ubuntu running now and one of the first apps I wanted to try was Monodevelop. I added the extra apt repositories according to Ubuntuguide.org ([http://www.ubuntuguide.org/#extrarepositories)](http://www.ubuntuguide.org/#extrarepositories)), did an apt-get update, apt-get upgrade. From within Synaptic I then chose Monodevelop and some other stuff. The install seemed to go well. However, when I start Monodevelop I get the following:



```
mgoellner@kanrei:~$ monodevelop

** (MonoDevelop:10917): WARNING **: The following assembly referenced from /usr/lib/monodevelop/bin/MonoDevelop.Base.dll could not be loaded:
     Assembly:   monodoc    (assemblyref_index=8)
     Version:    1.0.0.0
     Public Key: 0738eb9f132ed756
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/monodevelop/bin).


** (MonoDevelop:10917): WARNING **: The class Monodoc.RootTree could not be loaded, used in /usr/lib/monodevelop/bin/MonoDevelop.Base.dll (token 0x01000063)

** (MonoDevelop:10917): WARNING **: Missing method LoadTree in assembly /usr/lib/monodevelop/bin/MonoDevelop.Base.dll, type Monodoc.RootTree
Loading error, please reinstall :
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> System.NullReferenceException: Object reference not set to an instance of an object
in <0x00000> <unknown method>
in (wrapper managed-to-native) System.Reflection.MonoCMethod:InternalInvoke (object,object[])
in <0x0006f> System.Reflection.MonoCMethod:Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)--- End of inner exception stack trace ---

in <0x00104> System.Reflection.MonoCMethod:Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)in <0x00019> System.Reflection.MonoCMethod:Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture)
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
mgoellner@kanrei:~$

```

I then marked Monodevelop for a fresh installation in Synaptic but nothing has changed. Could someone please point me in the correct direction on how to solve this? Preferably in a way which would enable me to solve issues like this myself in the future :)

---

### Post by jmeadows111 on 2005-06-22
I have had issues in the past with mono and monodevelop on Ubuntu, so when 1.1.8.1 came out recently, I tried a different approach; using Synaptic I uninstalled the current version of mono on my PC, then I tried using the [mono installer from the download page](http://www.mono-project.com/Downloads) , and except for the fact that it didn't create menu items for me (I am running XFCE) it seems to be working so far.

Of course with this approach you don't get the nice updating from Synaptic, but I am OK with that. You will have to make your own call here.

---

### Post by mgoellner on 2005-06-22
Well, it's not working with Synaptic or via apt from the command line so I'll have to try that, thank you

---

### Post by mgoellner on 2005-06-22
The Installer didn't do the trick either, I reinstaleld just about everything out of Synaptic and added some devel packages as well, now Monodevelop launches just fine, I think there are some dependency issues with this packages somewhere

---

