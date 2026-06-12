---
title: "Can't swtich JREs"
date: 2007-10-09
forum: General Help
---

### Post by dbokan on 2007-10-09
Hello all,

I'm trying to switch to using the Sun JRE. From what I can find on the web the proper way to do this is (I've already 'apt-get'ted it) to run 

update-java-alternatives --set java-6-sun

I get the following output from this command: 
```

Using `/usr/lib/jvm/java-6-sun/bin/appletviewer' to provide `appletviewer'.
Using `/usr/lib/jvm/java-6-sun/bin/apt' to provide `apt'.
Using `/usr/lib/jvm/java-6-sun/bin/extcheck' to provide `extcheck'.
Using `/usr/lib/jvm/java-6-sun/bin/HtmlConverter' to provide `HtmlConverter'.
Using `/usr/lib/jvm/java-6-sun/bin/idlj' to provide `idlj'.
Using `/usr/lib/jvm/java-6-sun/bin/jarsigner' to provide `jarsigner'.
Using `/usr/lib/jvm/java-6-sun/bin/jar' to provide `jar'.
Using `/usr/lib/jvm/java-6-sun/bin/javac' to provide `javac'.
Using `/usr/lib/jvm/java-6-sun/bin/javadoc' to provide `javadoc'.
Using `/usr/lib/jvm/java-6-sun/bin/javah' to provide `javah'.
Using `/usr/lib/jvm/java-6-sun/bin/javap' to provide `javap'.
Using `/usr/lib/jvm/java-6-sun/bin/java-rmi.cgi' to provide `java-rmi.cgi'.
Using `/usr/lib/jvm/java-6-sun/bin/jconsole' to provide `jconsole'.
Using `/usr/lib/jvm/java-6-sun/bin/jdb' to provide `jdb'.
Using `/usr/lib/jvm/java-6-sun/bin/jhat' to provide `jhat'.
Using `/usr/lib/jvm/java-6-sun/bin/jinfo' to provide `jinfo'.
Using `/usr/lib/jvm/java-6-sun/bin/jmap' to provide `jmap'.
Using `/usr/lib/jvm/java-6-sun/bin/jps' to provide `jps'.
Using `/usr/lib/jvm/java-6-sun/bin/jrunscript' to provide `jrunscript'.
Using `/usr/lib/jvm/java-6-sun/bin/jsadebugd' to provide `jsadebugd'.
Using `/usr/lib/jvm/java-6-sun/bin/jstack' to provide `jstack'.
Using `/usr/lib/jvm/java-6-sun/bin/jstatd' to provide `jstatd'.
Using `/usr/lib/jvm/java-6-sun/bin/jstat' to provide `jstat'.
Using `/usr/lib/jvm/java-6-sun/bin/native2ascii' to provide `native2ascii'.
Using `/usr/lib/jvm/java-6-sun/bin/rmic' to provide `rmic'.
Using `/usr/lib/jvm/java-6-sun/bin/schemagen' to provide `schemagen'.
Using `/usr/lib/jvm/java-6-sun/bin/serialver' to provide `serialver'.
Using `/usr/lib/jvm/java-6-sun/bin/wsgen' to provide `wsgen'.
Using `/usr/lib/jvm/java-6-sun/bin/wsimport' to provide `wsimport'.
Using `/usr/lib/jvm/java-6-sun/bin/xjc' to provide `xjc'.
No alternatives for ControlPanel.
update-alternatives: Cannot find alternative `/usr/lib/jvm/java-6-sun/bin/java'.

No alternatives for java_vm.
No alternatives for javaws.
No alternatives for jcontrol.
update-alternatives: Cannot find alternative `/usr/lib/jvm/java-6-sun/jre/bin/keytool'.

No alternatives for orbd.
No alternatives for pack200.
No alternatives for policytool.
No alternatives for rmid.
update-alternatives: Cannot find alternative `/usr/lib/jvm/java-6-sun/jre/bin/rmiregistry'.

No alternatives for servertool.
No alternatives for tnameserv.
No alternatives for unpack200.
No alternatives for firefox-javaplugin.so.
No alternatives for iceape-javaplugin.so.
No alternatives for iceweasel-javaplugin.so.
No alternatives for mozilla-javaplugin.so.

```

Which doesn't make sense to me, because all these files do exist. I checked the /etc/alternatives directory and java and other JRE binaries still point to the gcj binaries. Any suggestions? Here's my jinfo file:

```

name=java-6-sun-1.6.0.00
alias=java-6-sun
priority=63
section=non-free

jre ControlPanel /usr/lib/jvm/java-6-sun/jre/bin/ControlPanel
jre java /usr/lib/jvm/java-6-sun/bin/java
jre java_vm /usr/lib/jvm/java-6-sun/jre/bin/java_vm
jre javaws /usr/lib/jvm/java-6-sun/jre/bin/javaws
jre jcontrol /usr/lib/jvm/java-6-sun/jre/bin/jcontrol
jre keytool /usr/lib/jvm/java-6-sun/jre/bin/keytool
jre pack200 /usr/lib/jvm/java-6-sun/jre/bin/pack200
jre policytool /usr/lib/jvm/java-6-sun/jre/bin/policytool
jre rmid /usr/lib/jvm/java-6-sun/jre/bin/rmid
jre rmiregistry /usr/lib/jvm/java-6-sun/jre/bin/rmiregistry
jre unpack200 /usr/lib/jvm/java-6-sun/jre/bin/unpack200
jre orbd /usr/lib/jvm/java-6-sun/jre/bin/orbd
jre servertool /usr/lib/jvm/java-6-sun/jre/bin/servertool
jre tnameserv /usr/lib/jvm/java-6-sun/jre/bin/tnameserv
jdk HtmlConverter /usr/lib/jvm/java-6-sun/bin/HtmlConverter
jdk appletviewer /usr/lib/jvm/java-6-sun/bin/appletviewer
jdk apt /usr/lib/jvm/java-6-sun/bin/apt
jdk extcheck /usr/lib/jvm/java-6-sun/bin/extcheck
jdk idlj /usr/lib/jvm/java-6-sun/bin/idlj
jdk jar /usr/lib/jvm/java-6-sun/bin/jar
jdk jarsigner /usr/lib/jvm/java-6-sun/bin/jarsigner
jdk java-rmi.cgi /usr/lib/jvm/java-6-sun/bin/java-rmi.cgi
jdk javac /usr/lib/jvm/java-6-sun/bin/javac
jdk javadoc /usr/lib/jvm/java-6-sun/bin/javadoc
jdk javah /usr/lib/jvm/java-6-sun/bin/javah
jdk javap /usr/lib/jvm/java-6-sun/bin/javap
jdk jconsole /usr/lib/jvm/java-6-sun/bin/jconsole
jdk jdb /usr/lib/jvm/java-6-sun/bin/jdb
jdk jhat /usr/lib/jvm/java-6-sun/bin/jhat
jdk jinfo /usr/lib/jvm/java-6-sun/bin/jinfo
jdk jmap /usr/lib/jvm/java-6-sun/bin/jmap
jdk jps /usr/lib/jvm/java-6-sun/bin/jps
jdk jrunscript /usr/lib/jvm/java-6-sun/bin/jrunscript
jdk jsadebugd /usr/lib/jvm/java-6-sun/bin/jsadebugd
jdk jstack /usr/lib/jvm/java-6-sun/bin/jstack
jdk jstat /usr/lib/jvm/java-6-sun/bin/jstat
jdk jstatd /usr/lib/jvm/java-6-sun/bin/jstatd
jdk native2ascii /usr/lib/jvm/java-6-sun/bin/native2ascii
jdk rmic /usr/lib/jvm/java-6-sun/bin/rmic
jdk schemagen /usr/lib/jvm/java-6-sun/bin/schemagen
jdk serialver /usr/lib/jvm/java-6-sun/bin/serialver
jdk wsgen /usr/lib/jvm/java-6-sun/bin/wsgen
jdk wsimport /usr/lib/jvm/java-6-sun/bin/wsimport
jdk xjc /usr/lib/jvm/java-6-sun/bin/xjc
plugin mozilla-javaplugin.so /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
plugin firefox-javaplugin.so /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
plugin iceweasel-javaplugin.so /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
plugin iceape-javaplugin.so /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

```

Thanks in advance,
David

---

### Post by smaller on 2007-10-27
Did you ever get this sorted mate? I'm struggling with a similar issue, which I posted in [this thread]("http://ubuntuforums.org/showthread.php?t=592934&highlight=Cannot+find+alternative")

At this point in time there's no answer there yet, I'm just cross referencing the threads. I should have looked harder yesterday and posted in this thread instead.

Didn't updating the symbolic links in /etc/alternatives manually work for you? I think it should solve your issue. For me it doesn't, however things are possibly slightly more complicated for me as it's also got something to do with the firefox plugin detection. So I'm hoping that the update-java-alternatives does something more then just update the symbolic links in /etc/alternatives...

---

### Post by elchuppa on 2007-12-02
I'm having this problem too.  Installed the beta java 7 jdk.  

I created a .java-7-sun.jinfo file with the following contents
```

name=java-7-sun
alias=java-7-sun
priority=100
section=non-free

jre ControlPanel /usr/lib/jvm/java-7-sun/jre/bin/ControlPanel
jre java /usr/lib/jvm/java-7-sun/jre/bin/java
jre java_vm /usr/lib/jvm/java-7-sun/jre/bin/java_vm
jre javaws /usr/lib/jvm/java-7-sun/jre/bin/javaws
jre jcontrol /usr/lib/jvm/java-7-sun/jre/bin/jcontrol
jre keytool /usr/lib/jvm/java-7-sun/jre/bin/keytool
jre pack200 /usr/lib/jvm/java-7-sun/jre/bin/pack200
jre policytool /usr/lib/jvm/java-7-sun/jre/bin/policytool
jre rmid /usr/lib/jvm/java-7-sun/jre/bin/rmid
jre rmiregistry /usr/lib/jvm/java-7-sun/jre/bin/rmiregistry
jre unpack200 /usr/lib/jvm/java-7-sun/jre/bin/unpack200
jre orbd /usr/lib/jvm/java-7-sun/jre/bin/orbd
jre servertool /usr/lib/jvm/java-7-sun/jre/bin/servertool
jre tnameserv /usr/lib/jvm/java-7-sun/jre/bin/tnameserv
jdk HtmlConverter /usr/lib/jvm/java-7-sun/bin/HtmlConverter
jdk appletviewer /usr/lib/jvm/java-7-sun/bin/appletviewer
jdk apt /usr/lib/jvm/java-7-sun/bin/apt
jdk extcheck /usr/lib/jvm/java-7-sun/bin/extcheck
jdk idlj /usr/lib/jvm/java-7-sun/bin/idlj
jdk jar /usr/lib/jvm/java-7-sun/bin/jar
jdk jarsigner /usr/lib/jvm/java-7-sun/bin/jarsigner
jdk java-rmi.cgi /usr/lib/jvm/java-7-sun/bin/java-rmi.cgi
jdk javac /usr/lib/jvm/java-7-sun/bin/javac
jdk javadoc /usr/lib/jvm/java-7-sun/bin/javadoc
jdk javah /usr/lib/jvm/java-7-sun/bin/javah
jdk javap /usr/lib/jvm/java-7-sun/bin/javap
jdk jconsole /usr/lib/jvm/java-7-sun/bin/jconsole
jdk jdb /usr/lib/jvm/java-7-sun/bin/jdb
jdk jhat /usr/lib/jvm/java-7-sun/bin/jhat
jdk jinfo /usr/lib/jvm/java-7-sun/bin/jinfo
jdk jmap /usr/lib/jvm/java-7-sun/bin/jmap
jdk jps /usr/lib/jvm/java-7-sun/bin/jps
jdk jrunscript /usr/lib/jvm/java-7-sun/bin/jrunscript
jdk jsadebugd /usr/lib/jvm/java-7-sun/bin/jsadebugd
jdk jstack /usr/lib/jvm/java-7-sun/bin/jstack
jdk jstat /usr/lib/jvm/java-7-sun/bin/jstat
jdk jstatd /usr/lib/jvm/java-7-sun/bin/jstatd
jdk native2ascii /usr/lib/jvm/java-7-sun/bin/native2ascii
jdk rmic /usr/lib/jvm/java-7-sun/bin/rmic
jdk schemagen /usr/lib/jvm/java-7-sun/bin/schemagen
jdk serialver /usr/lib/jvm/java-7-sun/bin/serialver
jdk wsgen /usr/lib/jvm/java-7-sun/bin/wsgen
jdk wsimport /usr/lib/jvm/java-7-sun/bin/wsimport
jdk xjc /usr/lib/jvm/java-7-sun/bin/xjc
plugin firefox-javaplugin.so /usr/lib/jvm/java-7-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
plugin iceape-javaplugin.so /usr/lib/jvm/java-7-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
plugin iceweasel-javaplugin.so /usr/lib/jvm/java-7-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
plugin mozilla-javaplugin.so /usr/lib/jvm/java-7-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
plugin midbrowser-javaplugin.so /usr/lib/jvm/java-7-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
plugin xulrunner-javaplugin.so /usr/lib/jvm/java-7-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so

```

verified that all these files actually do exist in their respective locations, however I get an 
'update-alternatives: Cannot find alternative /usr/lib/jvm/,,'  error for each entry in the jinfo file.

---

### Post by elchuppa on 2007-12-02
ok, some further digging seems to imply that creating the .jinfo file is not enough.

update-alternatives needs to have the new files installed as options.  Seems labor intensive so I'm not sure if this is the right way to do it but:
```

 sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/java-7-sun/jre/bin/java 50

```

allowed the java portion of the update-java-alternatives to execute correctly.

Basically if when you run 
```

update-alternatives --config {filename}

```
you don't see your file as an option, then even putting a reference to it in the .jinfo will not help, you need to install it as an option using the above update-alternatives syntax for it to work.

Hopefully someone with better knowledge can explain a better way to do it, as I think having to run update-alternatives --install for each file is a pain.

---

### Post by bangkok on 2008-02-13
i am not exactly having the issues posted in this thread... but what i need to be able to do is actually be able to switch between older releases (1.3.1_06 & 1.4.2_15) for work. 

i work on equipment t that i interface using java to configure. the problem is depending on the release of s/ware the equipment is running on i need to use either of the two releases i listed above. 

i would then like to be able to switch back to latest & greatest java when i am not working on equipment at work for security purposes.

i am currently having to do this with a winblowzXP partition running on my xubunu feisty work laptop. 

i am thinking once i find out what exactly is required to swap between java releases it will be easy to write a script to make all the changes required for the switch?

any help or pointers in the right direction is muchos appreciated. googled for it, but not much out there about swapping between java releases.

---

### Post by imoatama on 2008-02-26
I just cut and pasted the .jinfo file I'd made, and a few minutes of find/replace and vim i turned it into a shell script that will add all those files in update-alternatives. It's by no means elegant, and assumes you have the jdk installed to /usr/lib/jvm/java-7-sun, but it does work.

Here:
```
#!/bin/sh
update-alternatives --install /usr/bin/ControlPanel ControlPanel /usr/lib/jvm/java-7-sun/jre/bin/ControlPanel 50
update-alternatives --install /usr/bin/java java /usr/lib/jvm/java-7-sun/jre/bin/java 50
update-alternatives --install /usr/bin/java_vm  java_vm /usr/lib/jvm/java-7-sun/jre/bin/java_vm 50
update-alternatives --install /usr/bin/javaws  javaws /usr/lib/jvm/java-7-sun/jre/bin/javaws 50
update-alternatives --install /usr/bin/jcontrol  jcontrol /usr/lib/jvm/java-7-sun/jre/bin/jcontrol 50
update-alternatives --install /usr/bin/keytool  keytool /usr/lib/jvm/java-7-sun/jre/bin/keytool 50
update-alternatives --install /usr/bin/pack200  pack200 /usr/lib/jvm/java-7-sun/jre/bin/pack200 50
update-alternatives --install /usr/bin/policytool  policytool /usr/lib/jvm/java-7-sun/jre/bin/policytool 50
update-alternatives --install /usr/bin/rmid  rmid /usr/lib/jvm/java-7-sun/jre/bin/rmid 50
update-alternatives --install /usr/bin/rmiregistry  rmiregistry /usr/lib/jvm/java-7-sun/jre/bin/rmiregistry 50
update-alternatives --install /usr/bin/unpack200  unpack200 /usr/lib/jvm/java-7-sun/jre/bin/unpack200 50
update-alternatives --install /usr/bin/orbd  orbd /usr/lib/jvm/java-7-sun/jre/bin/orbd 50
update-alternatives --install /usr/bin/servertool  servertool /usr/lib/jvm/java-7-sun/jre/bin/servertool 50
update-alternatives --install /usr/bin/tnameserv  tnameserv /usr/lib/jvm/java-7-sun/jre/bin/tnameserv 50
update-alternatives --install /usr/bin/HtmlConverter  HtmlConverter /usr/lib/jvm/java-7-sun/bin/HtmlConverter 50
update-alternatives --install /usr/bin/appletviewer  appletviewer /usr/lib/jvm/java-7-sun/bin/appletviewer 50
update-alternatives --install /usr/bin/apt  apt /usr/lib/jvm/java-7-sun/bin/apt 50
update-alternatives --install /usr/bin/extcheck  extcheck /usr/lib/jvm/java-7-sun/bin/extcheck 50
update-alternatives --install /usr/bin/idlj  idlj /usr/lib/jvm/java-7-sun/bin/idlj 50
update-alternatives --install /usr/bin/jar  jar /usr/lib/jvm/java-7-sun/bin/jar 50
update-alternatives --install /usr/bin/jarsigner  jarsigner /usr/lib/jvm/java-7-sun/bin/jarsigner 50
update-alternatives --install /usr/bin/java-rmi.cgi  java-rmi.cgi /usr/lib/jvm/java-7-sun/bin/java-rmi.cgi 50
update-alternatives --install /usr/bin/javac  javac /usr/lib/jvm/java-7-sun/bin/javac 50
update-alternatives --install /usr/bin/javadoc  javadoc /usr/lib/jvm/java-7-sun/bin/javadoc 50
update-alternatives --install /usr/bin/javah  javah /usr/lib/jvm/java-7-sun/bin/javah 50
update-alternatives --install /usr/bin/javap  javap /usr/lib/jvm/java-7-sun/bin/javap 50
update-alternatives --install /usr/bin/jconsole  jconsole /usr/lib/jvm/java-7-sun/bin/jconsole 50
update-alternatives --install /usr/bin/jdb  jdb /usr/lib/jvm/java-7-sun/bin/jdb 50
update-alternatives --install /usr/bin/jhat  jhat /usr/lib/jvm/java-7-sun/bin/jhat 50
update-alternatives --install /usr/bin/jinfo  jinfo /usr/lib/jvm/java-7-sun/bin/jinfo 50
update-alternatives --install /usr/bin/jmap  jmap /usr/lib/jvm/java-7-sun/bin/jmap 50
update-alternatives --install /usr/bin/jps  jps /usr/lib/jvm/java-7-sun/bin/jps 50
update-alternatives --install /usr/bin/jrunscript  jrunscript /usr/lib/jvm/java-7-sun/bin/jrunscript 50
update-alternatives --install /usr/bin/jsadebugd  jsadebugd /usr/lib/jvm/java-7-sun/bin/jsadebugd 50
update-alternatives --install /usr/bin/jstack  jstack /usr/lib/jvm/java-7-sun/bin/jstack 50
update-alternatives --install /usr/bin/jstat  jstat /usr/lib/jvm/java-7-sun/bin/jstat 50
update-alternatives --install /usr/bin/jstatd  jstatd /usr/lib/jvm/java-7-sun/bin/jstatd 50
update-alternatives --install /usr/bin/native2ascii  native2ascii /usr/lib/jvm/java-7-sun/bin/native2ascii 50
update-alternatives --install /usr/bin/rmic  rmic /usr/lib/jvm/java-7-sun/bin/rmic 50
update-alternatives --install /usr/bin/schemagen  schemagen /usr/lib/jvm/java-7-sun/bin/schemagen 50
update-alternatives --install /usr/bin/serialver  serialver /usr/lib/jvm/java-7-sun/bin/serialver 50
update-alternatives --install /usr/bin/wsgen  wsgen /usr/lib/jvm/java-7-sun/bin/wsgen 50
update-alternatives --install /usr/bin/wsimport  wsimport /usr/lib/jvm/java-7-sun/bin/wsimport 50
update-alternatives --install /usr/bin/xjc  xjc /usr/lib/jvm/java-7-sun/bin/xjc 50

```

---

