---
title: "Need advice"
date: 2007-02-15
forum: General Help
---

### Post by mistypotato on 2007-02-15
Can someone tell me what this error means and how to fix it?

Thanks



[SIZE="3"][COLOR="DarkRed"]/bin/sh: cc: command not found[/COLOR][/SIZE]

---

### Post by dcstar on 2007-02-15
> **mistypotato said:**
> Can someone tell me what this error means and how to fix it?

Thanks



[SIZE="3"][COLOR="DarkRed"]/bin/sh: cc: command not found[/COLOR][/SIZE]

It means the **cc **command was not found.

Tell us what you were trying to do and there may be a chance of a useful answer.

---

### Post by mistypotato on 2007-02-15
Sorry, I'm so newbie I don't even know what to ask :( 

I'm trying to install ossec and I get to the part where I run "sudo -s install.sh" but it fails and I keep getting this error.  I have no clue what to do.

Here is more that might help... thanks.

5- Installing the system
- Running the Makefile

*** Making zlib (by Jean-loup Gailly and Mark Adler) ***
make[1]: Entering directory `/home/meuser/src/ossec-hids-1.0/src/external/zlib-1.2.3'
cc -c -Wall -I../../ -I../../headers -DDEFAULTDIR=\"/var/ossec\" -DARGV0=\"zlib\" -DXML_VAR=\"var\" -DOSSECHIDS *.c
**[COLOR="Red"]/bin/sh: cc: command not found[/COLOR]**
make[1]: *** [shared] Error 127
make[1]: Leaving directory `/home/meuser/src/ossec-hids-1.0/src/external/zlib-1.2.3'
make[1]: Entering directory `/home/meuser/src/ossec-hids-1.0/src/external/zlib-1.2.3'
cp -pr zlib.h zconf.h ../../headers/
cp -pr libz.a ../
cp: cannot stat `libz.a': No such file or directory
make[1]: *** [ossec] Error 1
make[1]: Leaving directory `/home/meuser/src/ossec-hids-1.0/src/external/zlib-1.2.3'



*** Making os_xml ***

make[1]: Entering directory `/home/meuser/src/ossec-hids-1.0/src/os_xml'
cc -DXML_VAR=\"var\" -Wall -I../ -I../headers -DDEFAULTDIR=\"/var/ossec\" -DARGV0=\"os_xml\" -DXML_VAR=\"var\" -DOSSECHIDS -c os_xml.c os_xml_access.c os_xml_node_access.c os_xml_variables.c
make[1]: cc: Command not found
make[1]: *** [xml] Error 127
make[1]: Leaving directory `/home/meuser/src/ossec-hids-1.0/src/os_xml'

Error Making os_xml
make: *** [all] Error 1

Error 0x5.
Building error. Unable to finish the installation.

---

### Post by dcstar on 2007-02-15
> **mistypotato said:**
> Sorry, I'm so newbie I don't even know what to ask :( 

I'm trying to install ossec and I get to the part where I run "sudo -s install.sh" but it fails and I keep getting this error.  I have no clue what to do.
........
Error 0x5.
Building error. Unable to finish the installation.

Do you have the **build-essential** install environment meta-package installed on your system?

If not, go into Synaptic and install it.

---

### Post by mistypotato on 2007-02-15
Wow!

You're a Linux Genius :KS 

It was not installed.  I'm installing it now.

Thank you for your help!

---

