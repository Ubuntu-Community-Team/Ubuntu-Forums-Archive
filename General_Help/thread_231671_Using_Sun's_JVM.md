---
title: "Using Sun's JVM"
date: 2006-08-07
forum: General Help
---

### Post by kernco on 2006-08-07
I am trying to use Sun's JVM instead of the default gcj.  I went to add/remove and selected "Sun Java 5.0 Runtime" and installed it.  When I run Eclipse, however, the log says that it is still using gcj.  How can I change this?

---

### Post by sgtBiafra on 2006-08-07
If you don't mind using Sun's JVM for all Java applications on your system, you can modify the java symbolic link in /etc/alternatives to point at Sun instead of gcj.

"sudo rm /etc/alternatives/java"
"sudo ln -s /usr/lib/jvm/java-1.5.0-sun/bin/java /etc/alternatives/java"

As an alternative to that, I suppose you could create a script (or modify the eclipse startup script) to explicitly reference the Sun JVM as well.

---

### Post by vijirajan on 2006-08-07
You could use **update-alternatives** command to do this.

---

### Post by jmeadows111 on 2006-08-07
This is the command I use to start eclipse and force it to use the Sun JVM:

/usr/bin/eclipse  -vm /usr/lib/j2sdk1.5-sun/jre

---

### Post by Ocxic on 2006-08-07
just do "sudo update-alternatives java"

and select the version you want to yous and you done.

---

### Post by asimon on 2006-08-08
The new sun-java5 packages also come with a new 'update-java-alternatives' command which makes it easier to switch to an other java implementation.

```
$ update-java-alternatives -l
update-java-alternatives -l
java-1.5.0-sun 53 /usr/lib/jvm/java-1.5.0-sun
java-gcj 1041 /usr/lib/jvm/java-gcj

```
shows the available java implementations on your system and
```
$ sudo update-java-alternatives -s java-1.5.0-sun
Using `/usr/lib/jvm/java-1.5.0-sun/bin/appletviewer' to provide `appletviewer'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/apt' to provide `apt'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/extcheck' to provide `extcheck'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/HtmlConverter' to provide `HtmlConverter'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/idlj' to provide `idlj'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jarsigner' to provide `jarsigner'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jar' to provide `jar'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/javac' to provide `javac'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/javadoc' to provide `javadoc'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/javah' to provide `javah'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/javap' to provide `javap'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/java-rmi.cgi' to provide `java-rmi.cgi'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jconsole' to provide `jconsole'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jdb' to provide `jdb'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jinfo' to provide `jinfo'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jmap' to provide `jmap'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jps' to provide `jps'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jsadebugd' to provide `jsadebugd'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jstack' to provide `jstack'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jstatd' to provide `jstatd'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/jstat' to provide `jstat'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/native2ascii' to provide `native2ascii'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/rmic' to provide `rmic'.
Using `/usr/lib/jvm/java-1.5.0-sun/bin/serialver' to provide `serialver'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/ControlPanel' to provide `ControlPanel'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java_vm' to provide `java_vm'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/javaws' to provide `javaws'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/keytool' to provide `keytool'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/orbd' to provide `orbd'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/pack200' to provide `pack200'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/policytool' to provide `policytool'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/rmid' to provide `rmid'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/rmiregistry' to provide `rmiregistry'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/servertool' to provide `servertool'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/tnameserv' to provide `tnameserv'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/unpack200' to provide `unpack200'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `firefox-javaplugin.so'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `mozilla-javaplugin.so'.
Using `/usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `mozilla-snapshot-javaplugin.so'.

```
for example sets Sun's java as default. As you can see it takes care of all java related alternatives in one go. Very convenient!

See the 'man update-java-alternatives' for more options.

---

### Post by hod139 on 2006-08-10
This howto explains the process: [http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)

---

### Post by kops on 2007-06-04
I followed hod139's advice and it worked for me....thanks a lot hod139..
this is the link that he had suggested..
[http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)

Before doing this i had tried playing around with /usr/alternative/java without any favorable output...
Cheers,
Kapil

---

