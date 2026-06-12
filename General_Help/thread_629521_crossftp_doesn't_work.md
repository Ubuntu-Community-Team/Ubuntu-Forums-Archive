---
title: "crossftp doesn't work"
date: 2007-12-02
forum: General Help
---

### Post by Nigggo on 2007-12-02
After trying nearly every ftp client available for linux i think crossftp is the only one acceptable.
but if i try to connect to an ftp server it says 
```
[R] 220 DrFTPD+ 2.0-SVN $Revision: 1760 $ http://drftpd.org
[R] AUTH SSL
[R] 234 AUTH SSL successful
[R] Negotiating Security Session...
[R] RSA premaster secret error
[R] Connection lost.
```
does anyone has an idea how to solve this problem?

---

### Post by morningboat on 2007-12-05
This problem seems to be caused by USA's Import/Export restrictions on the security algorithms.

You need to check your Java version. If your system's Java is Sun Java 1.5, Due to import control restrictions, the version of JCE policy files that are bundled in the JDK(TM) 5.0 environment allow "strong" but limited cryptography to be used. In this case, download and install the Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files version 5.0. [http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp)

If you are using Java 1.6, maybe the problem can be solved. Not very sure, you can have a try.

---

### Post by Nigggo on 2007-12-12
i downloaded those files but dont know where to put them in.
btw i am not really shure if i installed java correctly.
i installed :
java webstart 6.0
java webstart 6.0 32bit
java runtime 5.0
ubuntu restricted extras

some of them i installed with automatix and some other simply with the install funktion of ubuntu.

on my pc i installed nearly everything i cound find including java in its name via synaptic but i thin that made everything worse... on my laptop i only installed the components i listed above...

---

### Post by morningboat on 2007-12-14
You need to know which Java your system is using now. <java-home> refers to the directory where the Java SE Runtime Environment (JRE) was installed. You may use the locate command to find where is your Java Home, or the best way is to use "javaws -viewer" to check what is your current Java version the system is using.

Java 6's Java Cryptography Extension (JCE) Unlimited Strength Jurisdiction Policy Files 6 can be downloaded at:  [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)

Here are the installation instruction for installing JCE policy (as shown in its readme):

1)  Download the unlimited strength JCE policy files.

2)  Uncompress and extract the downloaded file.

    This will create a subdirectory called jce.
    This directory contains the following files:

        README.txt                   This file
        COPYRIGHT.html               Copyright information
        local_policy.jar             Unlimited strength local policy file
        US_export_policy.jar         Unlimited strength US export policy file

3)  Install the unlimited strength policy JAR files.

    To utilize the encryption/decryption functionalities of
    the JCE framework without any limitation, first make a copy of
    the original JCE policy files (US_export_policy.jar and
    local_policy.jar in the standard place for JCE
    jurisdiction policy JAR files) in case you later decide
    to revert to these "strong" versions. Then replace the strong
    policy files with the unlimited strength versions extracted in the
    previous step.

    The standard place for JCE jurisdiction policy JAR files is:

        <java-home>/lib/security            [Unix]
        <java-home>\lib\security           [Win32]

---

### Post by Nigggo on 2008-01-31
finally i came back to this problem and did what you said, java 1.6 is the version running, so i overwrote these security files with those from JCE.
but this didnt solve the problem. crossftp does show the same error as before...

i thunk it was correct to start nautilus with "sudo nautilus" and then simply overwrite the security files in the folder shown in java control panel.
Any other ideas?

---

