---
title: "make[1]: no: Command not found"
date: 2007-03-26
forum: General Help
---

### Post by moshy on 2007-03-26
Hi,
When I try to compile the package telepathy-sharp from source, which I got from

[http://tapioca-voip.sourceforge.net/wiki/index.php/Landell](http://tapioca-voip.sourceforge.net/wiki/index.php/Landell)

I get this error

```

james@james-desktop:~/telepathy-sharp$ make
Making all in dbus-sharp
make[1]: Entering directory `/home/james/telepathy-sharp/dbus-sharp'
no -target:library -out:NDesk.DBus.dll -debug -unsafe Address.cs AssemblyInfo.cs Authentication.cs Bus.cs BusObject.cs Connection.cs DBus.cs DProxy.cs ExportObject.cs Introspection.cs IntrospectionSchema.cs Mapper.cs Message.cs MessageFilter.cs MessageReader.cs MessageWriter.cs Protocol.cs Server.cs Signature.cs Transport.cs UnixMonoTransport.cs UnixNativeTransport.cs Wrapper.cs -r:Mono.Posix
make[1]: no: Command not found
make[1]: *** [NDesk.DBus.dll] Error 127
make[1]: Leaving directory `/home/james/telepathy-sharp/dbus-sharp'
make: *** [all-recursive] Error 1

```

---

### Post by undertherift on 2007-03-26
edit:  totally misread your post.

Sorry - i've never seen that error before.

---

### Post by hod139 on 2007-03-29
Have you followed the steps in the install guide? 
[http://tapioca-voip.sourceforge.net/wiki/index.php/Installation_Guide](http://tapioca-voip.sourceforge.net/wiki/index.php/Installation_Guide)

Make sure you install all the dependencies.

---

### Post by hardyn on 2007-03-29
It looks like you are having dependancy issues... looks like it is trying to find a bunch of files... make you have all the required libs installed, and all the source is where it is supposed to be.

---

### Post by lnostdal on 2007-03-29
I think `no' is part of Perl.

---

### Post by WW on 2007-03-29
I think you need to install the package **mono-gmcs**.

The telepathy-sharp source code directory contains the file configure.ac, and this file contains the macro **AC_PATH_PROG(CSC, gmcs, no)**.  In the dbus-sharp directory, the file Makefile.am uses the macro $(CSC) as a command.  It appears that the AC_PATH_PROG(...) statement failed to find gmcs, and instead gave CSC the value "no", but then the script doesn't check if this happens.

---

### Post by moshy on 2007-04-08
I got this fixed up a while ago, but thanks all anyway. I think it actually was the mono_gcms package

---

