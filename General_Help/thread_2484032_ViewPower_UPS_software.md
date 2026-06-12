---
title: "ViewPower UPS software"
date: 2023-02-15
forum: General Help
---

### Post by maintech123 on 2023-02-15
I don't know if this is the right forum for this thread but I need some help/guidance. I have a UPS that needs configuration. There are 2 for Linux and Ubuntu is on their list for being tested for install. The name of the software is ViewPower. Maybe it once did work on Ubuntu but not on mine. There is a GUI version and a text version of the program. The GUI version doesn't even get started and it exits. The text will at least run for a second before exiting. Here is a copy of the run:

Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
strings: '/lib/libc.so.6': No such file

Launching installer...

Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.NoClassDefFoundError: Could not initialize class java.awt.Toolkit
    at java.awt.Component.<clinit>(Component.java:593)
    at com.zerog.ia.installer.util.BidiUtilImpl.setDefaultLocale(DashoA10*..)
    at ZeroGbb.a(DashoA10*..)
    at com.zerog.ia.installer.LifeCycleManager.q(DashoA10*..)
    at com.zerog.ia.installer.LifeCycleManager.b(DashoA10*..)
    at com.zerog.ia.installer.LifeCycleManager.a(DashoA10*..)
    at com.zerog.ia.installer.Main.main(DashoA10*..)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:498)
    at com.zerog.lax.LAX.launch(DashoA10*..)
    at com.zerog.lax.LAX.main(DashoA10*..)
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

I did check to see if I was really missing that file '/lib/libc.so.6'.  Actually does exist. Why the file could not be found by the program I don't understand because the file was in the place the program was looking for it and it was named what the program was looking for. I am no programmer. Maybe the issue is clear to someone who does. The actual files is "installViewPowerHTML_Linux_text_x86.bin".

The GUI version as stated earlier is even worse. Here is the output:

Preparing to install
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...


Graphical installers are not supported by the VM. The console mode will be used instead...


=======================================================

Installer User Interface Mode Not Supported

Unable to load and to prepare the installer in console or silent mode.

=======================================================

Anyone that can help me is greatly appreciated. If you can direct me to a web page that instructs how to make this install successful that would be good enough. ANY help will be very much appreciated. If you would like a copy of the program here is the URL: **[https://www.v7world.com/viewpower](https://www.v7world.com/viewpower) ... **[COLOR=#000000][FONT=Arial]Software for Linux[/FONT][/COLOR][COLOR=#000000][FONT=Arial] (V.HTML 1.04-21353) ... [COLOR=#000000][FONT=Arial]Graphic mode operation: and [/FONT][/COLOR][/FONT][/COLOR][COLOR=#000000][FONT=Arial]Text mode operation: (downloads) for Linux (which includes Ubuntu  [/FONT][/COLOR][COLOR=#000000][FONT=Arial]10/ 11/ 12/ 14/ 15/ 16/ 18/ 19/ 20 (64bit). Both are 64 bit.

Thank you very much!
[/FONT][/COLOR]

---

### Post by MAFoElffen on 2023-02-15
You got further than me.

I spun up a new Ubuntu 20.04.3 VM Instance to try to replicate your problem, so I could try to help you...

On 'installViewPowerHTML_Linux_x86.bin' I got this
```

root@ubuntu-2004:/tmp# ./VP/installViewPowerHTML_Linux_x86.bin
Preparing to install
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

JRE libraries are missing or not compatible....

Exiting....

```
Where it said it extarcted the JRE, then couldn't find it...

On 'installViewPowerHTML_Linux_text_x86.bin' I got this
```

root@ubuntu-2004:/tmp# ./VP/installViewPowerHTML_Linux_text_x86.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

./VP/installViewPowerHTML_Linux_text_x86.bin: 2432: exec: /tmp/install.dir.7737/Linux/resource/jre/bin/java: not found
root@ubuntu-2004:/tmp# ls /tmp/install.dir.7737/Linux/resource/jre/bin/
ControlPanel  javaws    jjs      orbd     policytool  rmiregistry  tnameserv
java          jcontrol  keytool  pack200  rmid        servertool   unpack200
root@ubuntu-2004:/tmp# ls /tmp/install.dir.7737/Linux/resource/jre/bin/java
/tmp/install.dir.7737/Linux/resource/jre/bin/java

```
Where you can see it extracted it's own version of Java, then could not find it. But you can see it was there, where it extracted it.

If it were me, I would be contacting their support and ask what is going on. There is a problem with both of their installer binaries.

Note: I Installed Java and declared a $JAVA_HOME, where both installers ignore that...

I did see this, which might help some of what you were talking about: [https://www.thestuffweuse.com/2017/05/15/ubuntu-and-ups/](https://www.thestuffweuse.com/2017/05/15/ubuntu-and-ups/)

---

### Post by SeijiSensei on 2023-02-16
If you have an APC UPS, you can install the hoary but effective apcupsd. Might support other power supplies as well; I've only ever used APCs.

```
sudo apt install apcupsd
```

---

