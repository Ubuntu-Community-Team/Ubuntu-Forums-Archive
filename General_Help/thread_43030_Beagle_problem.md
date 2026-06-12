---
title: "Beagle problem"
date: 2005-06-20
forum: General Help
---

### Post by arunsub on 2005-06-20
I get the following warnings when i start beagled:

** (beagled:14229): WARNING **: The following assembly referenced from /usr/lib/beagle/BeagleDaemonLib.dll could not be loaded:
     Assembly:   gmime-sharp    (assemblyref_index=8)
     Version:    1.0.0.0
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/beagle).


** (beagled:14229): WARNING **: The class GMime.StreamFs could not be loaded, used in /usr/lib/beagle/BeagleDaemonLib.dll (token 0x01000099)

** (beagled:14229): WARNING **: The class GMime.Parser could not be loaded, used in /usr/lib/beagle/BeagleDaemonLib.dll (token 0x0100009b)

** (beagled:14229): WARNING **: The following assembly referenced from /usr/lib/beagle/BeagleDaemonLib.dll could not be loaded:
     Assembly:   evolution-sharp    (assemblyref_index=13)
     Version:    1.0.0.0
     Public Key: 457eed85bd9370df
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/beagle).


** (beagled:14229): WARNING **: The class Evolution.Book could not be loaded, used in /usr/lib/beagle/BeagleDaemonLib.dll (token 0x010000eb)

** (beagled:14229): WARNING **: The class Evolution.BookView could not be loaded, used in /usr/lib/beagle/BeagleDaemonLib.dll (token 0x010000ed)

** (beagled:14229): WARNING **: The class Evolution.BookQuery could not be loaded, used in /usr/lib/beagle/BeagleDaemonLib.dll (token 0x010000ec)

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in (unmanaged) 0x80e00a9
in <0x00017> Beagle.Daemon.Queryable:Start ()
in <0x000d6> Beagle.Daemon.QueryDriver:Start ()
in <0x000ef> Beagle.Daemon.BeagleDaemon:StartupProcess ()
in <0x00048> (wrapper delegate-invoke) System.MulticastDelegate:invoke_bool ()
in <0x0002a> IdleProxy:Handler ()
in <0x0002b> (wrapper native-to-managed) IdleProxy:Handler ()
in (unmanaged) 0xb7f6da02
in <0x00004> (wrapper managed-to-native) Gtk.Application:gtk_main ()
in <0x00007> Gtk.Application:Run ()
in <0x0052e> Beagle.Daemon.BeagleDaemon:Main (string[])

Error while starting best:

** (/usr/lib/beagle/Best.exe:14274): WARNING **: The following assembly referenced from /usr/lib/beagle/Tiles.dll could not be loaded:
     Assembly:   gecko-sharp    (assemblyref_index=8)
     Version:    1.0.0.0
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/beagle).


** (/usr/lib/beagle/Best.exe:14274): WARNING **: The class Gecko.WebControl could not be loaded, used in /usr/lib/beagle/Tiles.dll (token 0x0100003c)

** ERROR **: file class.c: line 2119 (mono_class_setup_parent): should not be reached
aborting...

Can someone help?

---

### Post by otherdave on 2005-06-20
The error messages tell you (sort of) what the problem is:

```
** (beagled:14229): WARNING **: The following assembly referenced from /usr/lib/beagle/BeagleDaemonLib.dll could not be loaded:
Assembly: gmime-sharp
```

It can't find GMime so you need to install the Gmime library.

When you are looking for something with a **-sharp** in the title the library will be called libraryname-CIL (Common Intermediate Language)

So you'll want to install Gmime-CIL

(I think, I'm trying to go from memory)

Give that a try for all the libraries in question and see if it helps.

---

### Post by Majlo on 2005-06-20
You must install all dependencies ..
Follow this 

[http://www.beaglewiki.org/Ubuntu_Installation](http://www.beaglewiki.org/Ubuntu_Installation)

---

### Post by arunsub on 2005-06-21
[QUOTE=otherdave]The error messages tell you (sort of) what the problem is:

It can't find GMime so you need to install the Gmime library.

When you are looking for something with a **-sharp** in the title the library will be called libraryname-CIL (Common Intermediate Language)

So you'll want to install Gmime-CIL

(I think, I'm trying to go from memory)

Give that a try for all the libraries in question and see if it helps.[/QUOTE]
I tried apt-get install gmime-cil and it didn't get anything. i tried with other options also. I have installed all the libraries listed in [http://www.beaglewiki.org/Ubuntu_Installation](http://www.beaglewiki.org/Ubuntu_Installation). how do i install gmime and other CIL files?

---

### Post by xalphas on 2005-06-21
Exactly the same problem for me too.. Also installed every package mentioned in the beagle ubuntu page. 

Any help would be good.

Thx.

---

### Post by yage on 2005-06-21
havard@giant:~$ sudo apt-cache search mono |grep cil
libdbus-cil - .NET binding for D-BUS interprocess messaging system
libwine-cil - WINE bindings for Mono


havard@giant:~$ sudo apt-cache search gmime
libgmime-cil - .NET binding for the gmime MIME library
libgmime0 - MIME library
libgmime0-dev - MIME library - development files
libgmime1 - MIME library
libgmime1-dev - MIME library - development files
libgmime2.1 - MIME library, unstable version
libgmime2.1-dev - MIME library, unstable version - development files

_So what you want to install here is: _
**sudo apt-get install libdbus-cil libwine-cil libgmime-cil**

---

### Post by arunsub on 2005-06-21
I did what you said and tried beagled in the terminal. I got the following error:

** (beagled:25774): WARNING **: The following assembly referenced from /usr/lib/beagle/BeagleDaemonLib.dll could not be loaded:
     Assembly:   gmime-sharp    (assemblyref_index=8)
     Version:    1.0.0.0
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/beagle).


** (beagled:25774): WARNING **: The class GMime.StreamFs could not be loaded, used in /usr/lib/beagle/BeagleDaemonLib.dll (token 0x01000099)

** (beagled:25774): WARNING **: The class GMime.Parser could not be loaded, used in /usr/lib/beagle/BeagleDaemonLib.dll (token 0x0100009b)

** (beagled:25774): WARNING **: The following assembly referenced from /usr/lib/beagle/BeagleDaemonLib.dll could not be loaded:
     Assembly:   evolution-sharp    (assemblyref_index=13)
     Version:    1.0.0.0
     Public Key: 457eed85bd9370df
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/usr/lib/beagle).


** (beagled:25774): WARNING **: The class Evolution.Book could not be loaded, used in /usr/lib/beagle/BeagleDaemonLib.dll (token 0x010000eb)

** (beagled:25774): WARNING **: The class Evolution.BookView could not be loaded, used in /usr/lib/beagle/BeagleDaemonLib.dll (token 0x010000ed)

** (beagled:25774): WARNING **: The class Evolution.BookQuery could not be loaded, used in /usr/lib/beagle/BeagleDaemonLib.dll (token 0x010000ec)

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
in (unmanaged) 0x80e00a9
in <0x00017> Beagle.Daemon.Queryable:Start ()
in <0x000d6> Beagle.Daemon.QueryDriver:Start ()
in <0x000ef> Beagle.Daemon.BeagleDaemon:StartupProcess ()
in <0x00048> (wrapper delegate-invoke) System.MulticastDelegate:invoke_bool ()
in <0x0002a> IdleProxy:Handler ()
in <0x0002b> (wrapper native-to-managed) IdleProxy:Handler ()
in (unmanaged) 0xb7f6da02
in <0x00004> (wrapper managed-to-native) Gtk.Application:gtk_main ()
in <0x00007> Gtk.Application:Run ()
in <0x0052e> Beagle.Daemon.BeagleDaemon:Main (string[])

---

### Post by arunsub on 2005-06-22
any suggestion?

---

### Post by arunsub on 2005-06-22
OK. I got fed up with Beagle problem. I installed Cortex from [http://collectivecortex.com/](http://collectivecortex.com/) The installation was pretty smooth and user friendly. No dependency problem. I have written about my experience with installation in my blog. [http://www.arun-prabha.com/myblog/](http://www.arun-prabha.com/myblog/).

---

### Post by xalphas on 2005-06-22
[QUOTE=yage]havard@giant:~$ sudo apt-cache search mono |grep cil
libdbus-cil - .NET binding for D-BUS interprocess messaging system
libwine-cil - WINE bindings for Mono


havard@giant:~$ sudo apt-cache search gmime
libgmime-cil - .NET binding for the gmime MIME library
libgmime0 - MIME library
libgmime0-dev - MIME library - development files
libgmime1 - MIME library
libgmime1-dev - MIME library - development files
libgmime2.1 - MIME library, unstable version
libgmime2.1-dev - MIME library, unstable version - development files

_So what you want to install here is: _
**sudo apt-get install libdbus-cil libwine-cil libgmime-cil**[/QUOTE]


@yage thx man. Now beagled runs. And Best also runs with no problem or error. Now i installed beagle.xpi to firefox. An example search from best it show me the results. So it indexes ff. np. But what about files. Even i know some recent names of file types or names it doesn't show. Will it take some time to index /home directory? 

Thx for all the help here.

---

### Post by arunsub on 2005-06-22
[QUOTE=xalphas]@yage thx man. Now beagled runs. And Best also runs with no problem or error. Now i installed beagle.xpi to firefox. An example search from best it show me the results. So it indexes ff. np. But what about files. Even i know some recent names of file types or names it doesn't show. Will it take some time to index /home directory? 

Thx for all the help here.[/QUOTE]
I got those errors i listed above your reply even after trying what he said. How come you didn't get those?

---

### Post by xalphas on 2005-06-22
Maybe you are missing some packages. Check for gmime and with packages ending with -cil again. My advice will be like this. 

I don't know maybe i am lucky  :)  Try again i hope you figure it with success..

Regards

---

### Post by arunsub on 2005-06-22
I do have libgmime.cil installed. I couldn't figure it out, so i went to Cortex.

---

### Post by manicka on 2005-06-23
[QUOTE=arunsub]OK. I got fed up with Beagle problem. I installed Cortex from [http://collectivecortex.com/](http://collectivecortex.com/) The installation was pretty smooth and user friendly. No dependency problem. I have written about my experience with installation in my blog. [http://www.arun-prabha.com/myblog/](http://www.arun-prabha.com/myblog/).[/QUOTE]
 Cortex installs easily and is easy to config. My testing so far indicates that it doesn't index the new .odt file format for OOo or open .sxw files in OOo. That's too big a bug for me.

Program itself looks promising though. Nice clean interface

---

### Post by arunsub on 2005-06-23
It's still in Beta. It might get better when released.

---

