---
title: "how to install a program?"
date: 2008-05-12
forum: General Help
---

### Post by mbdriver on 2008-05-12
I am a noob in linux, and I don't understand how to install software I have to use in my job. It is symantec pcanywhere 12.1, and I understand that I can use in in linux. here is some info.

To install Symantec pcAnywhere CrossPlatform, follow these steps:

    * JAVA Virtual machine version 1.4.2 or later is required and needs to be in your global $PATH in order to run.
    * Open a Terminal Window and change directory to the Symantec pcAnywhere CrossPlatform folder located on the CD
    * Run the following command line:
          o  java -jar SetupLinuxMac.jar
    * Follow installation wizard instructions
    * After installation, navigate to /usr/bin directory and launch ./pcAnywhere


I hope someone can tel me how to do this step by step.

---

### Post by bobblehat on 2008-05-12
* Open a Terminal Window
(Applications->Accessories->Terminal)

* JAVA Virtual machine version 1.4.2 or later is required and needs to be in your global $PATH in order to run.
Should be installed by default. To confirm, open a terminal  then type 
java -version 
You should get some info indicating v 1.5 or similar

* Open a Terminal Window and change directory to the Symantec pcAnywhere CrossPlatform folder located on the CD
the path to your CD drive is most likely /media/cdrom so in the terminal cd  /media/cdrom/[wherever the software is on the cd]


* Run the following command line:
java -jar SetupLinuxMac.jar
* Follow installation wizard instructions
* After installation, navigate to /usr/bin directory and launch ./pcAnywhere

cd /usr/bin
then just type ./pcAnywhere

I hope that isn't going too much into basics :)

---

### Post by mbdriver on 2008-05-12
here is the address of the file: /media/cdrom0/Symantec pcAnywhere CrossPlatform. Here is the error message: No such file or directory

copy from terminal: mrb@mrb-laptop:~$ cd /media/cdrom0/Symantec pcAnywhere CrossPlatform
bash: cd: /media/cdrom0/Symantec: No such file or directory
mrb@mrb-laptop:~$ cd /media/cdrom0/Symantec_pcAnywhere_CrossPlatform
bash: cd: /media/cdrom0/Symantec_pcAnywhere_CrossPlatform: No such file or directory


I have java ver: 1.6, so it should be ok.

---

### Post by mbdriver on 2008-05-12
ok I got it to work, but after install it says. cant find jvm. error. i guess it is java virtual machine. where can I find it? i have tried synaptic.

---

### Post by Catz3705 on 2008-07-20
I have the identical issue with pcAnywhere 12.1 and Java VM error. (Setting up Linux CrossPlatform and deploying Thin Host) 

After using both the graphic and console interface wizards, the CrossPlatform installer contacts Symantec and attempts to download the Thin Host. At around 75% to 85% through the ~7.4mb download the installer quits with the "VM not found" error message and shuts down.

(I got the installer to run in graphic mode by highlighting "SetupLinuxMac.jar" in the /cdrom directory and having it open with Java 6 runtime app.) 

The attempt does not leave any files in the target location other than a log file (when run in console mode) with the error summary. (Not very much info there to assist in troubleshooting.)

It appears that the Symantec installer cannot or fails to detect the Java VM. A version call confirms Java 6 and its VM are loaded. I've added Cacao and alternatively Kaffe which are also Java VM's. No success getting the installer to recognize these programs.

_*bobblehat:*_
> java -version 
You should get some info indicating v 1.5 or similar


After reviewing forum threads on this subject it would appear that getting the location of java_vm in the global path statement is prerequisite to solving the proper installer activity.

*_mbdriver wrote:_*
> * JAVA Virtual machine version 1.4.2 or later is required and needs to be in your global $PATH in order to run. (from the installer notes)

I've loaded the $PATH variable with pointers to the java and java_vm executibles directories. Variables JAVA_HOME AND PLUGIN_HOME have also been loaded with appropriate directory paths. A system reboot shows that the changes are permanently installed (and hopefully available.) Additional attempts to install pcAnywhere Thin Host fail with the VM not found error.

I've also tried the following update procedure to configure a specific Java distro and its VM:
> $ update-alternatives --config java 
*# The configuration works, but the effect on the pcAnywhere installer does not cure the Java VM detection error.*

The default/selected Java version used is "java-6-sun" (Java 1.6.0.06). 

1)  The question is whether or not anyone has had success in manipulating this particular setup program and achieving a complete install.
2)  What are the work-arounds, if required, to get the installer to work if there are errors? 
3)  How is the Global environment variable applicable in this case managed if a Java VM detection error keep occuring? 
    (Calling Symantec will be the last resort.)

(System is Dell GX150 with Intel MOBO and cpu running Ubuntu 8.04 with most current updates including Java 1.6.0, the pcAnywhere sofware installs and runs correctly with Samba Windows XP and W2k shares, sees all the remotes in the workgroup including ubuntu and kubuntu devices)

*BTW as an afterthought. . .a modest addition to bobblehat's response*
> Some suggested terminal commands to locate "SetupLinuxMac.jar" on the Symantec CD are:
$ cd /cdrom 
     *# use your actual location and device<you can do a "dir" here to verify that you're in the right place>* 
$ cd Symantec\<insertsp>pcAnywhere\<insertsp>CrossPlatform\
     *#The back slashes and spaces<insertsp> are required for this folder name to work, a "dir" cmd will reveal how the folder names are formed. I followed the installer's instructions and at first had folder name errors.*
Thanks in advance for any appropriate suggestions  . . .
Catz3705

---

### Post by Catz3705 on 2008-07-26
This is a follow up to the issues surrounding the installation of the CrossPlatform pcAnywhere Thin Host on an Dell GX150 Intel mobo system running Ubuntu 8.04.

I hope these observations help someone with similar problems....there are probably a number of different ways to approach this set of issues. Your results and solutions may vary from mine. Always take proper precautions with any alterations and make backups before proceeding. There's no substitute for "Safe Computing!" 

The procedure used here had good, but partial success in that remote control from the Linux Thin Host to the Windows system that contained the original full install occurred in one direction. 

Problems still remain in getting the Windows machine to remotely control the Linux system. Possible permission or firewall restraints are causing this type of connection to fail. The network machines, which are all Samba shares, see each other and exchange files from shared resources at will.

The solution to getting the pcAnywhere installer to detect and utilize the installed Linux Java VM required (in this specific context and machine) the installation of Java 1.4.2. J2SE 1.4.2 can be found at:

(Both Java 1.5.0 and Java 1.6.0 are installed, but fail to provide what the Installer is looking for to complete the pcAnywhere Thin Host download. No good explanation on my part, I'm probably missing some technicality re the use of Java 5 & 6)

> [http://java.sun.com/j2se/1.4.2/](http://java.sun.com/j2se/1.4.2/)

It can be downloaded in two formats i.e. RPM archive or Selfextracting BIN.

The Java 1.4.2 selfextracting .bin file downloaded from Sun was extracted to /usr/lib/jvm. Extraction created directory folder j2re1.4.2_18 at that location.

> /usr/lib/jvm/j2re1.4.2_18 was added to the PATH variable by adding the line to the PATH string:

> PATH=/usr/lib/jvm/j2re1.4.2_18:/usr/lib/jvm:/usr/lib/jvm/java-6-sun/jre:/usr/lib/jvm/java-6-sun/jre/bin:$PATH

at the end of /etc/bash.bashrc file.

The default search order in /etc/jvm was altered with /usr/lib/jvm/j2re1.4.2_18 at the top of the search list.

> /usr/lib/j2re1.4.2_18: was also added to the PATH sting in /etc/environment

The system was rebooted and  "$ echo $PATH" executed in a terminal window indicated the presence of the new Java directory pointer.

From the Super-user terminal the following commands were used to start the pcAnywhere CrossPlatform installer from the CD:

> $ cd /cdrom *# Note: The CD source path should be adjusted for the user's actual media location*
$ cd Symantec\ pcAnywhere\ CrossPlatform\ *# Note: There is no lead back-slash before Symantec, one space after internal "\'s"*
$ /usr/lib/jvm/j2re1.4.2_18/bin/java -jar SetupLinuxMac.jar -console

(used the full path location just be make sure the right java executable was run --- a little overkill. Java 6 Run Time is still the default Java app running on the machine used in this instance.)

(I also found that the GUI interface for the pcAnywhere installer run by Java 6 Run Time will fail to complete the intall with the "JVM not found" error. Pointing at the Java executable in the Java 1.4.2 directory and running in  console text mode results in a completed install.)

The pcAnywhere installer started up in console text mode, contacted Symantec online, and downloaded the necessary files to the target directory without problems and basically in accordance with the pcAnywhere Installer instructions.

Double clicking the executable "pcAnywhere" in /usr/bin and selecting the dialog box "run" option invokes the pcAnywhere Thin Host.

Simple Thin Host configuration directs the Host to contact and take control of a target Windows XP share which has the master Host progam loaded. The WinXP master Host is  located on my LAN which contains 8 machines. (5 are Linux systems.) 

My network is a local LAN and does not require the Host/Remote connection to traverse the internet. Internet connections will require an intermediate Gateway or Webhost to facilitate connection. 

A good example (there are others available) would be the setup offered by Logmein.com. Logmein's free service will allow remote control, but no file transfer. Logmein Pro, a subscription service of Logmein.com, will provide remote control, file transfer and synchronization features. Logmein provides the connection for systems in the User's account which are online and running their software. Worth checking out especially for trial purposes. (I have no connection or financial interest in Logmein.com other than having used their free offer.)

The Windows XP (master Host) in my network can see any of the remotes that are logged into the LAN including their shared directory structures via pcAnywhere. A test between The WinXP master Host and a Win2K remote on the LAN allowed remote control in both directions.

At least there has been some solid progress with some Linux specific issues to be resolved. Anyone with similar experiences is welcome to constructively share notes and specifics . . . 

Catz3705

---

### Post by Eric B on 2008-07-30
I basically stole that last bit from you.

```
sudo /usr/lib/jvm/java-6-sun-1.6.0.06/bin/java -jar SetupLinuxMac.jar -console 
```

Did the trick. Its like the program could not figure out that java 6 was there without doing this.

Many thanks!

---

### Post by hardik123 on 2008-07-31
Thanks loot i tray a loot to install PcAnywhere so many time now finally i got it with your help :lolflag:

---

### Post by Eric B on 2008-07-31
Just a few more details, but it should be obvious. Make sure you have 6 picked with ```
sudo update-alternatives --config java
``` if you have more than one version installed. Otherwise it might wind up trying to open after installation with the java 5 version. The current version of 5 1.5.0.15 is pretty broken. I have found multi posts about it screwing things up.

---

### Post by Catz3705 on 2008-07-31
Hardik123 & Eric B:

Now that you've made a little headway with pcAnywhere, what are you attempting to run/control with it? 

I'd like to see some additional code and dialog regarding the implementation and use this app if you could spare the effort.

Particularly, I'm interested in anything that you've done in a Linux<==>Linux context. I'm especially interested in anything pertaining to Ubuntu/Kubuntu 8.04. As you can surmise, the success or failure in solving a major problem my reside in some very elusive details.

It's been my pleasure --- and a measure of personal validation --- to have been able to contribute a little something to your personal challenges. Thanks for your acknowledgements. I thought for a while I was logging to thin air.

Your exchanges, regardless of how trivial, are sincerely welcomed...

Catz3705
St. Petersburg, Florida

---

### Post by MIKE SILVA on 2009-02-02
Hello,

Thanks for support on this.
I follow your comments and try the suggestions, but stuck on this:

> **Catz3705 said:**
>  
The solution to getting the pcAnywhere installer to detect and utilize the installed Linux Java VM required (in this specific context and machine) the installation of Java 1.4.2. J2SE 1.4.2 can be found at:

(Both Java 1.5.0 and Java 1.6.0 are installed, but fail to provide what the Installer is looking for to complete the pcAnywhere Thin Host download. No good explanation on my part, I'm probably missing some technicality re the use of Java 5 & 6)

It can be downloaded in two formats i.e. RPM archive or Selfextracting BIN.

The Java 1.4.2 selfextracting .bin file downloaded from Sun was extracted to /usr/lib/jvm. Extraction created directory folder j2re1.4.2_18 at that location.

 was added to the PATH variable by adding the line to the PATH string:


at the end of /etc/bash.bashrc file.

The default search order in /etc/jvm was altered with /usr/lib/jvm/j2re1.4.2_18 at the top of the search list.
. Catz3705

I went to get Java 1.4.2 bin and download a the version 19, but i don't know how to make the extraction to /usr/lib/jvm and go further.

At the same time, inside of the JVM folder i cant create folders (no permission).

Linux is a complety new world to me and it's not so easy to pass same difficults.

Waiting for help,

Thanks
Mike

---

### Post by burebista on 2010-10-04
try this:
1. install j2sdk1.4.2_18 in /usr/lib/jvm/j2sdk1.4.2_18
2. run from console:
$sudo -s
$/usr/lib/jvm/j2sdk1.4.2_18/jre/bin/java -jar SetupLinuxMac.jar
and use the gui installer, it works 100%.
3. run from console
$sudo gedit /usr/bin/pcAnywhere
4. replace this line:
java -Djava.CPR.dirs=$PCAPATH -jar /usr/local/lib/pcAnywhere/vprcd.jar
with
/usr/lib/jvm/j2sdk1.4.2_18/jre/bin/java -Djava.CPR.dirs=$PCAPATH -jar /usr/local/lib/pcAnywhere/vprcd.jar
5. save the file /usr/bin/pcAnywhere
6. run from Alt-F2 or from Terminal "pcAnywhere".

That's it.

---

