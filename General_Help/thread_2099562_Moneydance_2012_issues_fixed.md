---
title: "Moneydance 2012 issues fixed"
date: 2012-12-29
forum: General Help
---

### Post by dcstar on 2012-12-29
I recently upgraded my Moneydance financial software (it is a paid multi-platform Java based personal accounting software) and immediately experienced the unresolved problems reported by other Ubuntu 12.04 (and various other Linux) users. The main issue in Moneydance 2012 involves making a manual backup of the data files (as the auto-backup to an specified file path has been removed in this version) not working because of a Java IO error.

To cut a long story and many hours of research and frustration short, you have to manually stop Moneydance from using the version of Java it installs and force it to use the latest native JRE that actually works with Ubuntu. So you need to do the following after installing Moneydance:
```
sudo mv /opt/Moneydance/jre /opt/Moneydance/jre.save
```
Now install the **openjdk-7-jre-headless** & **openjdk-7-jre** packages. Next is the most important:

Update the Java version to be used by the system in the "Alternatives":
```
man update-java-alternatives
```
Or use the **galternatives** package tool for this (much easier!) and set it to the Java 7 option.

Now when you run Moneydance it should show that is is using Java version 1.7.0 and there should be no Java IO errors in the Console Window.

This issue has multiple "non-solutions" in the Moneydance support forums and many Ubuntu users seem to have recently abandoned this software because of it. I have actually downgraded to [Moneydance 2011]("http://moneydance.com/download/2011/installers/moneydance.deb") because that version still allows **you** to back up **your data** to a place where **you** want it to be rather than have that function removed in Moneydance 2012 which forces you to use Dropbox as the **only** backup option (another example of terrible fad-based software "development"). The Moneydance 2011 x86 .DEB package works fine on 64-bit systems.

The overall functionality of the Moneydance software is great and when you buy a licence you are allowed to run it on multiple platforms simultaneously but their strategy of removing valuable features on newer versions is something to be wary of.

---

