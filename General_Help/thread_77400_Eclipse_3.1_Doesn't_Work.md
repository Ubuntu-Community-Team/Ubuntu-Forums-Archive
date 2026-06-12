---
title: "Eclipse 3.1 Doesn't Work"
date: 2005-10-16
forum: General Help
---

### Post by robrmd9 on 2005-10-16
Hello all,

I loaded Ubuntu 5.10 yesterday, and installed Eclipse 3.1 via the "Add Applications" feature.

I can load up Eclipse fine, but when I try to create a new Java project, it gives me a "Problem Opening Wizard" screen that gives the following reason:

"Plug-in org.eclipse.jdt.ui was unable to load class org.eclipse.jdt.internal.ui.wizards.JavaProjectWizard."

Can anyone help me resolve this problem, so I can use Eclipse properly?

Thanks in advance,
Rob

---

### Post by pickle on 2005-10-16
I just tried this, and I figured out that upgrading to Breezy changed my Java environment settings.

I have in my /etc/bash/bash.rc the following:
JAVA_HOME=/usr/java/jre1.5.0_02
export JAVA_HOME
export PATH=$PATH:$JAVA_HOME/bin

But after upgrading to Breezy, my JVM settings get overriden by gij, 1.4.2.  So, java -version returns:

java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

I have no idea if Eclipse will run with gij, or if gij has a Java 1.5 compatible version, but Eclipse 3.1 will not run with this version.

So, being the crude Linux newbie that I am, I wrote a shell script for launching Eclipse:

/usr/share/eclipse/eclipse -vm /usr/java/jre1.5.0_02/bin/java

which seems to work for Eclipse 3.1

---

### Post by veraction on 2005-10-16
somehow I was able to get eclipse to run in breezy, but it seems much laggier. Same version and everything. 

Anyone else notice this or is it just me?

---

### Post by pickle on 2005-10-16
BTW, I now think the gij thing part of the OpenOffice2 upgrade.  If you haven't done that upgrade, you might not have had your java path affected.

---

### Post by Aquatopia on 2005-10-18
[QUOTE=pickle]
I have in my /etc/bash/bash.rc the following:
JAVA_HOME=/usr/java/jre1.5.0_02
export JAVA_HOME
export PATH=$PATH:$JAVA_HOME/bin

But after upgrading to Breezy, my JVM settings get overriden by gij, 1.4.2.  So, java -version returns:

java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

I have no idea if Eclipse will run with gij, or if gij has a Java 1.5 compatible version, but Eclipse 3.1 will not run with this version.

So, being the crude Linux newbie that I am, I wrote a shell script for launching Eclipse:

/usr/share/eclipse/eclipse -vm /usr/java/jre1.5.0_02/bin/java

which seems to work for Eclipse 3.1[/QUOTE]

I sat over this problem for a while myself, but I was able to find a very elegant solution.

First of all you have to install the jre using this guide here: [http://www.ubuntuforums.org/showthread.php?t=76735]("http://www.ubuntuforums.org/showthread.php?t=76735")

If you have used a similar guide make sure that you've run the update-alternatives line in order to have the sun jre as the default java runtime.

Next edit /etc/eclipse/java_home with your favorite editor and comment out all of the JVM's except the one you are using. 

I hope this works for you :)

---

### Post by dreamminder on 2005-12-07
You only need to set the JAVA_HOME enviroment at the bash profile, under the /etc/bash.bashrc

---

