---
title: "Problem compiling latest Tomboy"
date: 2007-04-10
forum: General Help
---

### Post by zarathustra on 2007-04-10
I've been having problems compiling the latest versions of Tomboy and all come with the same error:

> make[2]: Entering directory `/home/nick/downloads/tomboy-0.6.3/help'
xsltproc -o tomboy-C.omf --stringparam db2omf.basename tomboy --stringparam db2omf.format 'docbook' --stringparam db2omf.dtd "-//OASIS//DTD DocBook XML V4.1.2//EN" --stringparam db2omf.lang C --stringparam db2omf.omf_dir "/usr/local/share/omf" --stringparam db2omf.help_dir "/usr/local/share/gnome/help" --stringparam db2omf.omf_in "`pwd`/./tomboy.omf.in" `/usr/bin/pkg-config --variable db2omf gnome-doc-utils` C/tomboy.xml
xsltproc: symbol lookup error: /usr/local/lib/libxslt.so.1: undefined symbol: xmlXPathCompiledEvalToBoolean
make[2]: *** [tomboy-C.omf] Error 127
make[2]: Leaving directory `/home/nick/downloads/tomboy-0.6.3/help'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nick/downloads/tomboy-0.6.3'
make: *** [all] Error 2

Am I missing something that needs to be installed, or is there a bug?

---

### Post by Arisna on 2007-04-10
I think I see the problem.  The makefile seems to be looking for an xslt object in /usr/local/lib.  On my system, this object is in /usr/lib.  Look in your Makefile for a reference to xslt and ensure that libxslt.so.1 will be looked for in /usr/lib.

Edit:  Actually, do a `locate libxslt.so.1' beforehand.  If it's in /usr/lib, proceed with what I said above.  If it's in /usr/local/lib, I've got nothing.

---

### Post by zarathustra on 2007-04-10
I found out that I had compiled my own version of libxslt and had forgotten about it, which was causing the error. I couldn't find any intelligible reference to where it was looking, so I thought I would try reinstalling the libraries and found the offending package (fortunately I had installed it via check install) and removed it. It's compiled fine now, many thanks.

---

### Post by zarathustra on 2007-04-15
Now I am having slightly different problem with Tomboy. It won't start up any more, and this is the output when I try from the command line: 

> nick@ubuntu:~$ tomboy
[DEBUG]: NoteManager created with note path "/home/nick/.tomboy".

Unhandled Exception: System.ComponentModel.Win32Exception: The per-user inotify watches limit of 8192 has been reached. If you're experiencing problems with your application, increase that limit in /proc/sys/fs/inotify/max_user_watches.
at System.IO.InotifyWatcher.StartMonitoringDirectory (System.IO.InotifyData data, Boolean justcreated) [0x00000]
at System.IO.InotifyWatcher.StartDispatching (System.IO.FileSystemWatcher fsw) [0x00000]
at System.IO.FileSystemWatcher.Start () [0x00000]
at System.IO.FileSystemWatcher.set_EnableRaisingEvents (Boolean value) [0x00000]
at (wrapper remoting-invoke-with-check) System.IO.FileSystemWatcher:set_EnableRaisingEvents (bool)
at Tomboy.PluginManager..ctor (System.String plugins_dir) [0x00000]
at Tomboy.NoteManager.CreatePluginManager () [0x00000]
at Tomboy.NoteManager..ctor (System.String directory, System.String backup_directory) [0x00000]
at Tomboy.NoteManager..ctor (System.String directory) [0x00000]
at Tomboy.Tomboy.Main (System.String[] args) [0x00000]

I realise it tells me to alter something but I don't know what this actually means, exactly how to do it and what repercussions this might have for the rest of the system or even why I've reached this limit.

---

