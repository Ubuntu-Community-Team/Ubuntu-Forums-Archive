---
title: "Problems Loading OpenOffice"
date: 2008-04-21
forum: General Help
---

### Post by UrbanoFreitas on 2008-04-21
Hi!

I did the upgrade from Gutsy to Hardy, last Saturday.

Since then, whenever I open any application from OpenOffice I get this message:

"OpenOffice.org requires a Java runtime environment (JRE) to perform this task. The selected JRE is defective. Please select another version or install a new JRE and select it under Tools - Options - OpenOffice.org - Java".

I already seen someone else with this error: 
[http://ubuntuforums.org/showthread.php?p=4760029](http://ubuntuforums.org/showthread.php?p=4760029)

It is even a known bug, but from Gutsy:
[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/149489](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/149489)

I tried start OpenOffice as root trough the command line, and then  I get the message:
"javaldx failed! 
[Java framework]sunjavaplugin.so could not load Java runtime library: 
file:///usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client/libjvm.so.urban@urban-laptop:~$ [Java framework]sunjavaplugin.so could not load Java runtime library: 
file:///usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client/libjvm.so.[Java framework]sunjavaplugin.so could not load Java runtime library: 
file:///usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/i386/client/libjvm.so."

Does anyone know how can I fix this?
OOo does work, but is really annoying get this message every time I start OOo.

Thanks in advance!
Urbano

P.S. - I already did what suggested in the bug;

---

### Post by Bubba64 on 2008-04-21
You might have to go to system administration software sources and open more repositories then go to synaptic and java 6 is in there. You can also update the resources in synaptic. Personally I hava jave turned off on OO because I only use it to write papers. You can turn off java in OO by going to tools-options-open office.org java. It may be that if you open the repositories that your attempt to load via terminal may work. Personally I have in sources, everything open including source and have never had any personal problems accepting every download.

---

### Post by UrbanoFreitas on 2008-04-22
Thanks for answer!

Unfortunately it did not fix my problem.

I even tried to disable Java for a While, but now I get a message (pop-up window) saying:
Title: "Enable JRE"

Message:
"OpenOffice.org requires Java runtime environment (JRE) to perform this task. However, use of a JRE has been disabled. Do you want to enable the use of a JRE now?"

Even if I choose the "_N_o" option, I will get this message every time I try to open OOo. Not matter if it is Writter or Calc.

**Any more help will be deeply appreciated!**

I already tried to remove and install older versions of Java, but still get the same message - "JRE defective". 

And now When I tried to install the latest version of Java trough the command line, by using the: 
sudo apt-get install sun-java6-jdk

I get a few errors:
"Setting up sun-java6-bin (6-06-0ubuntu1) ...
Error: could not open `/usr/lib/jvm/java-6-sun-1.6.0.06/jre/lib/i386/jvm.cfg'
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of sun-java6-jre:
 sun-java6-jre depends on sun-java6-bin (= 6-06-0ubuntu1) | ia32-sun-java6-bin (= 6-06-0ubuntu1); however:
  Package sun-java6-bin is not configured yet.
  Package ia32-sun-java6-bin is not installed.
dpkg: error processing sun-java6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-jdk:
 sun-java6-jdk depends on sun-java6-bin (= 6-06-0ubuntu1); however:
  Package sun-java6-bin is not configured yet.
dpkg: error processing sun-java6-jdk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-bin
 sun-java6-jre
 sun-java6-jdk
E: Sub-process /usr/bin/dpkg returned an error code (1)"


Probably will have to do a fresh install of Hardy :(.

At least is always a nice experience to install Ubuntu :D

But, i repeat my appeal: If anyone know how to fix this error, i will be deeply thankfull!

---

### Post by UrbanoFreitas on 2008-04-22
The problem is due to a extension that I was using in OOo, called: OpenOffice.org2GoogleDocs.

I already disabled it, and the pop window "JRE defective" disappeared.

So it's not a Ubuntu problem.

Problem solved.
Thanks!

---

### Post by UrbanoFreitas on 2008-04-22
Forgot to say that the extension that I mention above need Java to work.

The error came from here.

---

### Post by lolwhites on 2008-04-22
Thanks Urbano. Does this mean we have to wait for a new version of the extension? It was oneof my favourites.

---

### Post by ppedrok on 2008-05-02
Thanks, Urbano, for posting!
I had the same problem after upgrading to Kubuntu Hardy ("selected JRE is defective...") :confused:.
When I found your solution, I started disabling some extensions, and now OOo works without problem, :smile:!

---

