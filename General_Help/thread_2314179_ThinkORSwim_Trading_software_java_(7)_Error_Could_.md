---
title: "ThinkORSwim Trading software java (7) Error: Could not create the Java Virtual Mach"
date: 2016-02-19
forum: General Help
---

### Post by ubuntark on 2016-02-19
Help please, not sure if I even posted in the correct area, this forum is huge! 

Unrecognized VM option 'MetaspaceSize=128m'
Error: Could not create the Java Virtual Machine.
Error: A fatal exception has occurred. Program will exit.


Somewhat new to using Ubuntu as my only/ primary OS due to constant problems such as this. 
Using TDameritrade's trading platform known as Think or Swim ( TOS) 


I am getting the java  errors I posted at the top of this message when I try and fire up the TOS trading platform On a new install of Ubuntu 15.04  ( I had this running for the past 6 months with some glitches but now that I tried to re-install on to new ubuntu install I am having no succes). 

per thinkorswims install notes I am using Java 7 and the following instructions to install TOS [https://mediaserver.thinkorswim.com/installer/install.html](https://mediaserver.thinkorswim.com/installer/install.html)[TABLE="width: 100%"]
[TR]
[TD][IMG]https://mediaserver.thinkorswim.com/installer/InstData/images/linux.gif[/IMG] **Linux Instructions:**[/TD]
[TD="align: right"][Install thinkDesktop (10 MB)]("https://mediaserver.thinkorswim.com/installer/InstFiles/thinkorswim_installer.sh")[/TD]
[/TR]
[TR]
[TD="colspan: 2"]                                             Thinkorswim needs Java7 to run. To install java7 on the machine:                                                  
[LIST]
[*]sudo apt-add-repository ppa:webupd8team/java 
[*]sudo apt-get update 
[*]sudo apt-get install oracle-java7-installer 
[/LIST]
                                             To install Thinkorswim:
                                                
[LIST]
[*]Click "Install thinkdesktop" to download the thinkorswim installer to a directory on your PC. 
[*]After downloading open a shell and CD to the directory where you downloaded the installer. 
[*]At the prompt type: sh ./thinkorswim_installer.sh 
[/LIST]
                                                 **Note: **For clients who  intend to run the software on Linux, Solaris or other Unix variants,  manual update of the software may be required on these systems and we  have no official support for configuring these operating systems.[/TD]
[/TR]
[/TABLE]


Thanks in advance for any help you can pass my way.  :)  hopefully prior to me pushing computer onto floor  :) 

_______________________________________________________
Ubuntu 15.04
Memory 15.6 GiB
Processor Intel® Core™ i7-4700MQ CPU @ 2.40GHz × 8
Graphics Intel® Haswell Mobile
OS type 64-bit
Disk 1.1 TB plus a solid state drive where the OS is loaded

---

### Post by Scott Deagan on 2016-02-20
Firstly, is there any reason why you're using Ubuntu 15.04? 15.04 is not an LTS and is no longer supported. I would recommend upgrading to Ubuntu 15.10.

In regards to installing Java, you could always try installing Java 8:

[FONT=courier new]sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer[/FONT]

If you go down the path of installing Java 8, you might want to uninstall Java 7 first:

[FONT=courier new]sudo apt-get remove oracle-java7-installer[/FONT]

I have Java 8 installed on Ubuntu 15.10, and was able to run the installer and run ThinkOrSwin (I don't have an account, so was not able to get past the login window).

Good luck!

---

### Post by xkalibur on 2016-05-20
I was having the same issue and installing Java version 8 seems to fix it.
Thanks Scott!

---

### Post by jim_deadlock on 2016-05-21
You don't actually need to mess about with that repository, the following works (I just tested it):

```
sudo apt install icedtea-plugin openjfx
```

The problem is that JavaFX isn't included in icedtea any more but you only need to install it separately.

---

