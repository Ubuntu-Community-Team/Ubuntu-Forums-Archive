---
title: "Netbeans without OpenJDK"
date: 2008-06-22
forum: General Help
---

### Post by Jens_Li on 2008-06-22
Im trying to install Netbean, it tells me its going to install OpenJDK to, but i already have the Suns jdk installed and its working fine.

In the dependencies for Netbeans i find:

openjdk-6-jdk | sun-java6-jdk,

no dependencies on thats only on openjdk.

How can I make it understand I dont need OpenJDK?

---

### Post by diaa on 2008-06-22
I don't think that's possible, as far as I can tell your only option is to use the netbeans installer from [http://netbeans.org](http://netbeans.org), and you'll get the latest version as a bonus :)

---

### Post by Jens_Li on 2008-06-22
Allright, cheers Ill check into that. The strange thing is none of the packages seems to be dependent on OpenJDK, they all seem to take sun jdk as an alternative. (using Synaptic to check for this)

But do you think Ill be able to uninstall OpenJDK afterwords, without Netbeans going also?

---

### Post by diaa on 2008-06-23
> **Jens_Li said:**
> But do you think Ill be able to uninstall OpenJDK afterwords, without Netbeans going also?

Yes I think so, I tried Netbeans from the website installer and it detects JDK during installation so it doesn't depend on OpenJDK I think.

---

### Post by tpischke on 2008-07-03
The libnb-svnclientadapter-java package depends on openjdk.  A bug should be filed to allow it to use sun's java 6

---

### Post by tpischke on 2008-07-03
[https://bugs.launchpad.net/ubuntu/+source/libnb-javaparser-java/+bug/225711](https://bugs.launchpad.net/ubuntu/+source/libnb-javaparser-java/+bug/225711)

---

### Post by Jens_Li on 2008-07-16
> **tpischke said:**
> The libnb-svnclientadapter-java package depends on openjdk.  A bug should be filed to allow it to use sun's java 6

Yeah, brilliant, thats it! Seems like I over looked that one. Great to have that reported to.

---

### Post by Jens_Li on 2008-07-30
Id still prefer to install NetBeans through the package manager.

Is there a way to edit the dependensies by hand to get around this bug? 

( would be nice to know for the future to... )

---

