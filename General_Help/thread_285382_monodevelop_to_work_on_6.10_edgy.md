---
title: "monodevelop to work on 6.10 edgy"
date: 2006-10-26
forum: General Help
---

### Post by rammy22 on 2006-10-26
HI I haven't gotten any replies in programming forum. I was hoping someone here might be able to help.

 uograded to 6.10 edgy and monodevelop doesn't seem to work. WHen I click on Applications->Programming->Mnoodevelop from previous 6.60 installation nothing happens. I ran the command to upgrade all the mono files
sudo apt-get install mono mono-gmcs mono-gac mono-utils monodevelop
but that doesn't seem to work.
Running from terminal (bash shell) I type "monodevelop" and get output

** (./MonoDevelop.exe:6036): WARNING **: The following assembly referenced from /usr/lib/monodevelop/bin/MonoDevelop.Core.dll could not be loaded:
Assembly: log4net (assemblyref_index=5)
Version: 1.2.9.0
Public Key: a5715cc6d5c3540b
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/monodevelop/bin).


** (./MonoDevelop.exe:6036): WARNING **: Could not load file or assembly 'log4net, Version=1.2.9.0, Culture=neutral, PublicKeyToken=a5715cc6d5c3540b' or one of its dependencies.

** (./MonoDevelop.exe:6036): WARNING **: Missing method Configure in assembly /usr/lib/monodevelop/bin/MonoDevelop.Core.dll, type log4net.Config.XmlConfigurator

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'log4net, Version=1.2.9.0, Culture=neutral, PublicKeyToken=a5715cc6d5c3540b' or one of its dependencies.
at <0x00000> <unknown method>
at MonoDevelop.Core.Runtime.get_LoggingService () [0x00000]
at MonoDevelop.Core.ServiceManager.FetchService (System.Type serviceType) [0x00000]
at MonoDevelop.Core.ServiceManager.GetService (System.Type serviceType) [0x00000]
at MonoDevelop.Core.AddIns.Setup.SetupService..ctor () [0x00000]
at MonoDevelop.Core.Runtime.get_SetupService () [0x00000]
at MonoDevelop.Core.AddIns.AddInService.Initialize () [0x00000]
Does anyone understand the error, and how to get monodevelop to run on 6.10 Edgy
Thanks for help

---

### Post by rjseagraves on 2006-11-01
I had the same problem (I'm guessing something in the upgrade from 6.06 to 6.10 screwed up how log4net was installed).  The problem is that MonoDevelop code makes calls into log4net, so the MonoDevelop application assembly (MonoDevelop.Core.dll) needs to load the log4net assembly when starting.  From the messages, log4net isn't in one of the mono assembly load locations, so monodevelop can't load it.  First, make sure you have the right version of log4net installed.  Use Synaptic or apt-get to make sure you have the Ubuntu package liblog4net1.2-cil installed.  If you don't, install it and see if that fixes your problem.  If it is installed, you need to either put the log4net dll in you GAC (Global Assembly Cache) or on your MONO_PATH.  Putting it on your GAC is easier, but the MONO_PATH is safer.

To put log4net in your GAC, type
"sudo gacutil -i /usr/lib/cli/log4net-1.2/log4net.dll" from the command line.  After this, you should be able to run monodevelop fine.

To put log4net on your MONO_PATH, add
"/usr/lib/cli/log4net-1.2/log4net.dll" to your MONO_PATH environment variable in your shell config file ("~/.bashrc" in bash) and source your shell config file (type "source ~/.bashrc").  After this, you should be able to run monodevelop from the command line, but you will probably need to log out and then back in to Gnome to run monodevelop from the menu.

Hope this helps.

---

### Post by Marller on 2006-11-04
A "Mark for Reinstallation" on log4net in Synaptic did the trick for me.

---

