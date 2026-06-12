---
title: "How to launch a Java program installed through .bin that doesn't appear in the menu?"
date: 2018-06-04
forum: General Help
---

### Post by ricky22 on 2018-06-04
Hello,

I've installed a Java application called ELAN from a .bin file.

[https://tla.mpi.nl/tools/tla-tools/elan/download/](https://tla.mpi.nl/tools/tla-tools/elan/download/)

It does not appear in the Whisker menu as applications installed from repositories normally do. Could someone tell me how I can start it? This is the content of the application folder in my home folder:

 ELAN_5.2                 'Media playback Read Me.txt'   extensions
 ELAN_5.2.lax              Uninstall_ELAN_5.2            jmf__Vlin2.1.1fcs
 ELAN_5.2_InstallLog.log   clip-media.txt                lax.jar
 LICENSE-apache-2.0.txt    elan.properties               lib
 LICENSE-gpl-3.0.txt       elanlog.properties            locale
 LICENSES.txt              ext

Below are the first few lines front the two of the files above I suspect should be used to start the application:

ELAN_5.2.lax

#   LaunchAnywhere (tm) Executable Properties File - Macrovision Corp.

#   LAX.APPLICATION.NAME
#   --------------------
#   the default name of this executable -- do not edit

lax.application.name=ELAN_5.2



ELAN_5.2

#!/bin/sh
#################################################################################################
#
# LAXUNIX.SH - LaunchAnywhere (tm) version 7.0
#
# (c) Copyright 1999-2005 Zero G Software, Inc., all rights reserved.
#
#  To run this script you will need to have the following:
#	1) a Java VM installed (however, it will handle a lack of Java nicely).
#	2) a Java-style properties file having the same name as this script 
#		with the suffix .lax.  If this script is appended to the
#		self-extractor, it will look for the properties file in the
#		directory specified by $seLaxPath; otherwise, it will look in
#		the same directory that this script is in.
#	3) a Java program in the file "lax.jar".
#
#  The .lax property file must contain at least the following properties:
#	1)  lax.class.path  classpath (do not include the environment variable $CLASSPATH )
#	2)  lax.nl.java.launcher.main.class  (main class of LaunchAnywhere Executable)
#
#################################################################################################

#################################################################################################
#
# Linux - JMF adaptation by MPI
# The .lax property file can contain the following MPI specific property:
# 	1) lax.nl.mpi.jmf (pointing to the JMF folder in the install dir)
# This script is changed to extract that property and export it as / add it to
# the LD_LIBRARY_PATH
# Jan 2007
# The LD_LIBRARY_PATH also refers to <jre>/lib/i386, <jre>lib/i386/xawt and
# <jre>/lib/i386/client
# In addition the LD_PRELOAD environment variable is exported, pointing to 
# <path to jre>/lib/i386/libjawt.so
#################################################################################################

Any help would be much appreciated.

Patrick

---

### Post by Holger_Gehrke on 2018-06-04
I can't be sure without seeing the rest of the file, but ELAN_5.2 has the 'shebang' of a shell-script as its first line. So open a terminal and use the 'cd'-command to change to the directory where the file is.If it isn't already executable (check with 'ls -l ELAN_5.2'), you can make it executable with 'chmod u+x ELAN_5.2'; after that you can start it with './ELAN_5.2' (the './' is necessary because the current directory is **not** in the PATH searched for executables for security reasons). If that works, you can create a .desktop-file for it in '~/.local/share/applications. Either copy and edit an existing desktop-file (they are simple textfiles with a rather obvious format) or use a menu-editor like menulibre or alacarte. 

Holger

PS: In the future, please use code-tags for better readability ...

---

### Post by ricky22 on 2018-06-04
Hi Holger,

Thanks for the prompt response. I've done what you suggested, this is the result:

p@ppc:~/ELAN_5.2$ ./ELAN_5.2
strings: '/lib/libc.so.6': &#12381;&#12398;&#12424;&#12358;&#12394;&#12501;&#12449;&#12452;&#12523;&#12399;&#12354;&#12426;&#12414;&#12379;&#12435; [no such file]
raw jre dir: /home/p/ELAN_5.2/jre/
jre dir: /home/p/ELAN_5.2/jre/
LD_LIBRARY_PATH: /home/p/ELAN_5.2/jmf__Vlin2.1.1fcs:/home/p/ELAN_5.2/jre/lib/i386:/home/p/ELAN_5.2/jre/lib/i386/xawt:/home/p/ELAN_5.2/jre/lib/i386/client:
LD_PRELOAD: 
-Djava.ext.dirs=/home/p/ELAN_5.2/ext is not supported.  Use -classpath instead.
Error: Could not create the Java Virtual Machine.
Error: A fatal exception has occurred. Program will exit.

I have JRE installed:

p@ppc:~/ELAN_5.2$ java -version
openjdk version "10.0.1" 2018-04-17
OpenJDK Runtime Environment (build 10.0.1+10-Ubuntu-3ubuntu1)
OpenJDK 64-Bit Server VM (build 10.0.1+10-Ubuntu-3ubuntu1, mixed mode)

Thanks in advance,

Patrick

P.S.: Duly noted on the code tags. If there is also specific formatting required for the content of the terminal window, kindly let me know.

---

### Post by Holger_Gehrke on 2018-06-04
I've downloaded and installed ELAN. The good news: that script really seems to be the one to call. The bad news: I can't get it to work either. According to the script, you can pass the option '-i' followed by "text", "console", "gui", "awt" or "swing" to set the user interface. Setting the environment variable LAX_DEBUG to some value makes the script give more output. Using that output i found that the logger of the program tries to write to '~/.elan_data and failed. After I created that directory, the script didn't give anymore errors, but a logfile in that directory said that java could not load some class and the program aborted. There is a forum dedicated to Elan at [https://tla.mpi.nl/forums/software/elan/](https://tla.mpi.nl/forums/software/elan/). One of the newest posters there seems to be in a similar situation to you (Ubuntu, OpenJRE 10) and was told that Elan hasn't been tested on Java 10.

Holger

PS.: Code tags are for any code, including input to or output from programs running in a terminal. You can either use the advanced editor (hit the "Go Advanced" button below the input field), mark the text and click the button with the '#' on it or write 'code' in brackets ('[' and ']') before and '/code' in brackets after the code. Doing this switches display to a non-proportional font and stops html from removing spaces, so tabulated output will be lined up correctly. It also puts the code into an indented box so it's easy to identify.

---

### Post by ricky22 on 2018-06-04
Hi Holger,

Many thanks for your help. In the meantime I've tried installing the version of JRE from Oracle, uninstalling the default one I installed previously, then installing it again (so I'm guessing having both versions in the end, the default one and the Oracle one, both v. 10). The message didn't change when I tried to start the application. The output of 

```

$ java -version

```

didn't change either.

Then I tried installing the older (beta) version, which comes with "Java 1.8 and JavaFX media player", and this one opens OK (I haven't used it much yet).

Thanks for the link to the forum post, I will monitor that, and also try installing older versions of JRE.

And thanks for the tip on code tags, you learn something everyday :-)

All the best,

Patryk

---

### Post by monkeybrain20122 on 2018-06-04
Try to switch to openjdk8 as default. I don't know about your program but on my 18.04 half of my java software didn't work with openjdk10. All work with openjdk8 Normally there is no need for Oracle's

---

### Post by Holger_Gehrke on 2018-06-04
And something else: if you've got multiple versions of Java installed, there's a command to switch between them. Since it works with the Debian alternatives system, it's named 'update-java-alternatives'. I don't know whether the Oracle package integrates itself cleanly with this facility, but you could try
```
update-java-alternatives -l
```
This lists one Java environment per line. The first column is the name, the second is the priority of this variant and the last column gives the path to the directory it's installed in. With
```
update-java-alternatives -s NAME
``` you can switch to another Java. 

Holger

---

### Post by ricky22 on 2018-06-05
Many thanks to both of you, I'll give that a try later and report back.

---

