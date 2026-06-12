---
title: "Prolem connecting OOo Base to MySQL using JDBC on Hardy"
date: 2008-04-21
forum: General Help
---

### Post by harley_frog on 2008-04-21
I recently had to reinstall Ubuntu, but before I did so, I backed up my MySQL databases.  When I did the reinstall, I decided to upgrade from 7.10 (Gutsy) to 8.04 (Hardy).  I reinstalled MySQL, OpenOffice Base, libmysql-java and the Java JRE, but when I try to set up OOo to connect to my MySQL database using JDBC, I get the following error message:
[I]
OpenOffice.org requires a Java runtime environment (JRE) to perform this task.  The selected JRE is defective.  Please select another version or install a new JRE and select it under Tools - Options - OpenOffice.org - Java.
[/I] 
I did that and have two JREs to choose from: Sun Microsystems Inc. 1.5.0_15 (location: /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre) and Sun Microsystems Inc. 1.6.0._05 (location:/usr/local/bin/jre1.6.0_05).  The first one is from the Ubuntu repository and the second is a local install from Sun's website.  I have tried selecting first one, than the other, each time going through the Database Wizard and coming up with the same error message each time.

This is really getting highly annoying since I am using OOo Base as my front end for data entry to my MySQL database for work.  If I can't connect to the database, I can't enter data and that leaves me in a major bind.

I have the following installed:

libmysql-java  version: 5.1.5+dfsg-2
sun-java-bin  version 1.5.0-15-0ubuntu1
sun-java-jre  version 1.5.0-15-0ubuntu1
OpenOffice.org-Base  version 1:2.4.0-3ubuntu5

Hope that helps.

Any suggestions?

---

### Post by FluffyElmo on 2008-04-21
Try installing the latest Java JDK from the repositories and see if that solves things? The first command should install the JDK, the second lets you set your default JVM. 
```

sudo apt-get install sun-java6-jdk
sudo update-alternatives --config java
```

---

### Post by harley_frog on 2008-04-21
FluffyElmo, I did you you said and tried again and still comes up with the same error message. :(

---

### Post by FluffyElmo on 2008-04-21
This seems to be a bug.... [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/149489]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/149489")

It sounds like the workaround is to make sure a JVM is selected before you try to use a function which needs a JVM. Try going to *Tools->Options->OpenOffice.org->Java* in OO and making sure a JVM is checked before trying to access the database.

---

### Post by UrbanoFreitas on 2008-04-22
Hi!

I have a similar problem, after done a upgrade similar to yours.

In my case the problem, was due to a extension that I was using in OOo, called: OpenOffice.org2GoogleDocs, that require Java.

The problem disappear when I disabled it. No more pop windows with "JRE defective" messages.

So, I my case, it's not a Ubuntu problem.

Hope this can help.

---

### Post by harley_frog on 2008-04-22
FluffyElmo,

Thanks for the bug report.  It looks very much like the problem I'm having.  I tried *Tools->Options->OpenOffice.org->Java* but it never seems to work.  That is, I select the JRE, close the dialog box, reopen and no JRE is selected.  I even tried uninstalling and reinstalling OOo, but still get the same problem.

I hope they fix this soon.

---

### Post by gloonie on 2008-05-05
I had similar issues. The selected jvm would not stay set. The solution I found was that a file existed in my ooo directory that pointed to a nonexistent jvm. I simply deleted it:

rm ~/.openoffice.org2/user/config/javasettings_Linux_x86.xml

When I restarted Openoffice, it picked up the right jre and kept it.

HTH,


Glenn

---

