---
title: "MonoDevelop 1.2.5 does not start!"
date: 2007-09-13
forum: General Help
---

### Post by lordfkiller on 2007-09-13
I just installed Mono 1.2.5 using compiled binary package. When I click MonoDevelop icon, nothing happens. And the same problem exists for MonoDoc.
I tried running it from terminal. This is the result:
[INDENT]######################################################################
MonoDevelop failed to start.
If you installed MonoDevelop using a binary installer, take a look at 
[http://www.mono-project.com/InstallerInstructions](http://www.mono-project.com/InstallerInstructions) for more info about possible
causes of this error.
######################################################################
System.TypeInitializationException: An exception was thrown by the type initializer for Gnome.ModuleInfo ---> System.DllNotFoundException: gnomesharpglue-2
  at (wrapper managed-to-native) Gnome.ModuleInfo:gnomesharp_gnome_moduleinfo_get_name_offset ()
  at Gnome.ModuleInfo..cctor () [0x00000] --- End of inner exception stack trace ---

  at <0x00000> <unknown method>
  at Gnome.Modules.get_UI () [0x00000] 
  at MonoDevelop.Ide.Gui.IdeStartup.Run (System.String[] args) [0x00000] 
[/INDENT] 

Maybe this helps:

Mono Project website FAQ:
[INDENT]Why don't the MonoDoc and MonoDevelop Nautilus icons work?

As long as you have the necessary libraries installed, this is no longer a problem in version 1.2.3.1. If you're using an older version, you need to restart your desktop for the .bashrc/.profile settings to take effect. See below about running Monodevelop if you're still having problems.

Why doesn't MonoDevelop run on NLD9?

You probably have Firefox installed, but not Mozilla. Install the Mozilla package and this should fix the problem. This requirement will not be necessary with future versions of MonoDevelop.

[/INDENT]

Thanks for any help.

---

