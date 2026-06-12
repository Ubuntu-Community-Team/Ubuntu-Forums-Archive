---
title: "what is gtk-sharp?"
date: 2007-06-15
forum: General Help
---

### Post by alex1974 on 2007-06-15
Hello,

can anybody explain what gtk-sharp is. In the last time I get messages like:

alex@alex-leisser:~$ tomboy --help

** (/usr/lib/tomboy/Tomboy.exe:738: WARNING **: The following assembly referenced from /usr/lib/mono/gac/gtk-sharp/2.10.0.0__35e10195dab3c99f/gtk-sharp.dll could not be loaded:
Assembly: atk-sharp (assemblyref_index=4)
Version: 2.10.0.0
Public Key: 35e10195dab3c99f
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/mono/gac/gtk-sharp/2.10.0.0__35e10195dab3c99f).


** (/usr/lib/tomboy/Tomboy.exe:738: WARNING **: Could not load file or assembly 'atk-sharp, Version=2.10.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'atk-sharp, Version=2.10.0.0, Culture=neutral, PublicKeyToken=35e10195dab3c99f' or one of its dependencies.

It's the same with beagle. But what did I do wrong?
I tried to reinstall gtk-sharp but without results.
Any suggestions what I can do now?
Thanks,
Alex

---

### Post by marrabld on 2007-12-29
I know that this is a late reply but I post the solution in case someone is trawling for answers.

GTK-SHARP is the GTK+ bindings for applications written in C# using the .net libraries.  both Tomboy and beagle are written in C#.  I had this problem for some reason, to solve:  go to synaptic package manager and search for gtk-sharp2, you may need to reinstall them.

Just reinstalling gtk-sharp wont do as you will need version 2.

Hope this helps

---

