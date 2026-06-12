---
title: "Monodevlop on ubuntu 13.10"
date: 2014-03-18
forum: General Help
---

### Post by jozamm on 2014-03-18
[FONT=arial]Hi all,.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I am using monodevelop 3.0.3.2+dfsg-1build1 (the default monodevelop on ubuntu 13.10) together with Mono 3.2.8 compiled from source. When i start monodevelop i get the following error message[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Unhandled Exception:
System.IO.FileNotFoundException: Could not load file or assembly 'Mono.Addins, Version=0.6.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.
File name: 'Mono.Addins, Version=0.6.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756'
  at MonoDevelop.Startup.MonoDevelopMain.Main (System.String[] args) [0x00000] in <filename unknown>:0 
[ERROR] FATAL UNHANDLED EXCEPTION: System.IO.FileNotFoundException: Could not load file or assembly 'Mono.Addins, Version=0.6.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756' or one of its dependencies.
File name: 'Mono.Addins, Version=0.6.0.0, Culture=neutral, PublicKeyToken=0738eb9f132ed756'
  at MonoDevelop.Startup.MonoDevelopMain.Main (System.String[] args) [0x00000] in <filename unknown>:0 
Missing method get_IsInitialized in assembly /usr/lib/monodevelop/bin/MonoDevelop.Ide.dll, type Mono.Addins.AddinManager

uname -a 

Linux 3.14.0-031400rc6-generic #201403100035 SMP Mon Mar 10 04:36:54 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux



[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Am I missing some dependency? or have I messed up my dependencies?[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Any help would be appreciated.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Regards,[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]jozamm[/FONT]

---

