---
title: "Beagle problem"
date: 2005-06-13
forum: General Help
---

### Post by arunsub on 2005-06-13
Did anyone install Beagle in Ubuntu? I installed it through synaptic. I started the beagle deamon and when i tried to open BEST, I'm getting the following error.

** (/usr/lib/beagle/Best.exe:19182): WARNING **: The following assembly referenced from /usr/lib/beagle/Tiles.dll could not be loaded:
    Assembly:   gecko-sharp    (assemblyref_index=8)
    Version:    1.0.0.0 
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/beagle).


** (/usr/lib/beagle/Best.exe:19182): WARNING **: The class Gecko.WebControl could not be loaded, used in /usr/lib/beagle/Tiles.dll (token 0x0100003c)

** ERROR **: file class.c: line 2119 (mono_class_setup_parent): should not be reached
aborting...

Does anyone know what the problem could be?  ](*,)

---

### Post by desdinova on 2005-06-13
[QUOTE=arunsub]Did anyone install Beagle in Ubuntu? I installed it through synaptic. I started the beagle deamon and when i tried to open BEST, I'm getting the following error.

** (/usr/lib/beagle/Best.exe:19182): WARNING **: The following assembly referenced from /usr/lib/beagle/Tiles.dll could not be loaded:
    Assembly:   gecko-sharp    (assemblyref_index=8)
    Version:    1.0.0.0 
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/beagle).


** (/usr/lib/beagle/Best.exe:19182): WARNING **: The class Gecko.WebControl could not be loaded, used in /usr/lib/beagle/Tiles.dll (token 0x0100003c)

** ERROR **: file class.c: line 2119 (mono_class_setup_parent): should not be reached
aborting...

Does anyone know what the problem could be?  ](*,)[/QUOTE]
 Install gecko-sharp...

---

### Post by arunsub on 2005-06-13
[QUOTE=desdinova]Install gecko-sharp...[/QUOTE]
Thanks for the quick reply.
apt-get install gecko-sharp will work?

---

