---
title: "Trying to set Java JDK 7 as default application for .jar files &amp; have hit a snag"
date: 2013-05-26
forum: General Help
---

### Post by Gorgofdoom on 2013-05-26
Java does not appear in the list of usable programs. I tried using the 'find programs online' button but it spit out an error (in a GUI text box):

GDBus.Error:org.freedesktop.DBus.Python.xdg.Exceptions.ParsingError: Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/defer/__init__.py", line 489, in _inline_callbacks
    result = gen.send(result)
  File "/usr/lib/python2.7/dist-packages/sessioninstaller/core.py", line 1030, in _install_mime_types
    path))
  File "/usr/lib/python2.7/dist-packages/xdg/DesktopEntry.py", line 33, in __init__
    self.parse(filename)
  File "/usr/lib/python2.7/dist-packages/xdg/DesktopEntry.py", line 42, in parse
    IniFile.parse(self, file, ["Desktop Entry", "KDE Desktop Entry"])
  File "/usr/lib/python2.7/dist-packages/xdg/IniFile.py", line 81, in parse
    raise ParsingError("Invalid line: " + line, filename)
ParsingError: ParsingError in file '/usr/share/app-install/desktop/workrave:workrave.desktop', Invalid line: - RSI (Repetitive Strain Injury) oraz wspomaga rekonwalescencj\u0119

I'll note that I just wiped my hard drive and installed Ubuntu 13.04 a few weeks ago. I update as updates are supplied.
I installed JDK 7 using the software center.

---

### Post by kostkon on 2013-05-26
It should be already the default app by default.

Nevertheless, you could try setting it again as the default jvm, something along the lines of
```
sudo update-java-alternatives -s java-1.7.0-openjdk-i386
```
you can see the list of installed jvms like this
```
sudo update-java-alternatives -l
```

Hope that helps.

---

### Post by Gorgofdoom on 2013-05-27
Odd. I have

"java-1.7.0-openjdk-i386 1071 /usr/lib/jvm/java-1.7.0-openjdk-i386"

but when i try
 
sudo update-java-alternatives -s java-1.7.0-openjdk-i386 it returns:

> 
update-alternatives: error: no alternatives for appletviewer
update-alternatives: error: no alternatives for extcheck
update-alternatives: error: no alternatives for idlj
update-alternatives: error: no alternatives for jar
update-alternatives: error: no alternatives for jarsigner
update-alternatives: error: no alternatives for javac
update-alternatives: error: no alternatives for javadoc
update-alternatives: error: no alternatives for javah
update-alternatives: error: no alternatives for javap
update-alternatives: error: no alternatives for jcmd
update-alternatives: error: no alternatives for jconsole
update-alternatives: error: no alternatives for jdb
update-alternatives: error: no alternatives for jhat
update-alternatives: error: no alternatives for jinfo
update-alternatives: error: no alternatives for jmap
update-alternatives: error: no alternatives for jps
update-alternatives: error: no alternatives for jrunscript
update-alternatives: error: no alternatives for jsadebugd
update-alternatives: error: no alternatives for jstack
update-alternatives: error: no alternatives for jstat
update-alternatives: error: no alternatives for jstatd
update-alternatives: error: no alternatives for native2ascii
update-alternatives: error: no alternatives for rmic
update-alternatives: error: no alternatives for schemagen
update-alternatives: error: no alternatives for serialver
update-alternatives: error: no alternatives for wsgen
update-alternatives: error: no alternatives for wsimport
update-alternatives: error: no alternatives for xjc
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/appletviewer
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/extcheck
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/idlj
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/jarsigner
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/jar
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/javac
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/javadoc
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/javah
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/javap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/jcmd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/jconsole
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/jdb
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/jhat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/jinfo
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/jmap
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/jps
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/jrunscript
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/jsadebugd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/jstack
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/jstatd
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/jstat
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/native2ascii
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/rmic
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/schemagen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/serialver
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/wsgen
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/wsimport
update-java-alternatives: jdk alternative does not exist: /usr/lib/jvm/java-7-openjdk-i386/bin/xjc


I take that as that it cannot find the specified file. :confused:

---

### Post by efflandt on 2013-05-27
I have 64-bit 12.04, but do not even see those (files or directories?) in a similar location or cannot find them with the "locate" command (like "locate appletviewer"):
```
efflandt@xps8100-1204:~$ ls /usr/lib/jvm/java-1.7.0-openjdk-amd64/bin
java  java-rmi.cgi  javaws  keytool  orbd  pack200  policytool  rmid  rmiregistry  servertool  tnameserv  unpack200
```But the only thing I use java for is minecraft client or server (or something else on a Raspberry Pi that needed parameters), so I used a script to launch those until I figured out how to do it in a launcher. For example this is what I use in a desktop or Unity launcher for the new beta minecraft launcher:```
sh -c 'java -Xmx2G -Xms1G -jar ~/MC-client/MinecraftDev.jar'
```

I do not know how to have a .jar automatically execute when you double click on it (maybe it needs execute permission) because even an executable script then asks if you want to run it or open it in a text editor. By default when I right click on a .jar the default is "Open With Archive Manager"

But it also offers:
Open With Archive Mounter
Open With OpenJDK 7 Runtime
Open With Other Application

---

### Post by Rebelli0us on 2013-05-27
In synaptic there is a file-type utlity called "assogiate".

---

### Post by HiImTye on 2013-05-27
```
sed -ie 's|\(Applications]\)|\1\napplication/java-archive=openjdk-7-java.desktop|' ~/.local/share/applications/mimeapps.list
```
should do what you're looking for

[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by Gorgofdoom on 2013-05-30
Someone knows his Ubuntu. Thanks!

---

### Post by HiImTye on 2013-05-30
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
you're welcome!
please mark as solved (edit original, advanced, change prefix to [SOLVED]) so that others may benefit!

---

