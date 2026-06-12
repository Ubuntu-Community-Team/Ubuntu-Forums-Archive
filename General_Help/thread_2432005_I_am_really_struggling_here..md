---
title: "I am really struggling here."
date: 2019-11-25
forum: General Help
---

### Post by dan369 on 2019-11-25
I am having a hell of a time getting java installed. I understand that Oracle Java 11 can&#8217;t be directly downloaded from Oracle website any more! Now you **HAVE** to log in and manually download Oracle Java 11 .tar.gz, and place the archive in /var/cache/oracle-jdk11-installer-local/ I did download java manually, however i am having a hard time from there i found this tutorial but it stopped working for me. 
when i followed this tutorial this is what i got [https://www.youtube.com/watch?v=88_a3h2rTk8&t=195s](https://www.youtube.com/watch?v=88_a3h2rTk8&t=195s)

 sudo update-alternatives --install /usr/bin/javac javac /home/gyan/Desktop/jdk-11_linux-x64_bin/jdk-11/bin/java 1
update-alternatives: error: alternative path /home/gyan/Desktop/jdk-11_linux-x64_bin/jdk-11/bin/java doesn't exist



When i found this tutorial this is what i got. [https://www.linuxuprising.com/2019/06/new-oracle-java-11-installer-for-ubuntu.html](https://www.linuxuprising.com/2019/06/new-oracle-java-11-installer-for-ubuntu.html)



dpkg: error processing package icedtea-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 oracle-java11-installer-local
 default-jre
 default-jdk
 default-jdk-headless
 icedtea-netx
 icedtea-8-plugin:amd64
 icedtea-plugin
E: Sub-process /usr/bin/dpkg returned an error code (1)


These tutorials stopped working. or never worked. 

[http://ubuntuhandbook.org/index.php/...u-18-04-18-10/]("http://ubuntuhandbook.org/index.php/2018/11/how-to-install-oracle-java-11-in-ubuntu-18-04-18-10/")
[https://www.wikihow.com/Install-Java-on-Ubuntu](https://www.wikihow.com/Install-Java-on-Ubuntu)
[https://www.wikihow.com/Install-Orac...n-Ubuntu-Linux]("https://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux")
[https://www.wikihow.com/Install-Java-on-Ubuntu](https://www.wikihow.com/Install-Java-on-Ubuntu)
[https://www.wikihow.com/Install-Orac...n-Ubuntu-Linux]("https://www.wikihow.com/Install-Oracle-Java-JRE-on-Ubuntu-Linux") On this one i got Package 'jre' has no installation candidate


basically i need someone to help me. or write a tutorial that works.
I don't expect anyone to help me with this. I think i might be switching back to windows. This is impossible!!! I have been trying for a while now.

---

### Post by wildmanne39 on 2019-11-25
*Thread moved to **New to Ubuntu a more appropriate sub-forum**.*

---

### Post by Holger_Gehrke on 2019-11-26
Is there a reason you want the Oracle JDK ? openjdk-11-jdk is the default Java Development Kit on Ubuntu and should be compatible.

The reason all these instructions are failing is because Oracle is being silly and wants users to jump through **their** hoops when installing. Going through the files at [https://www.oracle.com/technetwork/java/javase/downloads/jdk11-downloads-5066655.html](https://www.oracle.com/technetwork/java/javase/downloads/jdk11-downloads-5066655.html) I see a file named jdk-11.0.5_linux-x64_bin.deb available for download. You could download that and install it either with 'sudo dpkg --install jdk-11.0.5_linux-x64_bin.deb' or by right clicking on it in the file-manager and selecting the option to install it (different depending on DE in use, language and installed tools, on my XUbuntu it says "Mit Anwendungsinstallation öffnen").

Holger

---

