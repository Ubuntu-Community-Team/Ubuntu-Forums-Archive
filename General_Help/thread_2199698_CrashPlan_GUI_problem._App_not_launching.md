---
title: "CrashPlan GUI problem. App not launching"
date: 2014-01-15
forum: General Help
---

### Post by Christodoulou_Marios on 2014-01-15
Hi all. I bought a two year backup plan from CrashPlan. I unfortunately did not check first to see if their software for linux works, i took it on their word. Before any talk of refund and going for another service I would like to give a try at fixing the app. I already tried the solutions proposed on the web but no result yet. The following is an example of what happens from  /usr/local/crashplan/log/ui_output.log

[01.15.14 15:46:41.556 ERROR   main                 root                                     ] Failed to launch CPDesktop;  java.lang.UnsatisfiedLinkError: Could not load SWT library. Reasons:      Can't load library: /tmp/.cpswt/libswt-gtk-4234.so     Can't load library: /tmp/.cpswt/libswt-gtk.so     no swt-gtk-4234 in java.library.path     no swt-gtk in java.library.path     /tmp/.cpswt/libswt-gtk-4234.so: /tmp/.cpswt/libswt-gtk-4234.so:  failed to map segment from shared object: Operation not permitted

so it seems that it cannot run the swt thing from the tmp folder. running the command as root makes no difference. there seems to be a solution proposed[ here]("http://askubuntu.com/questions/183256/crashplan-not-starting-fails-to-find-swt-gtk") but i do not understand it (if anyone can clarify the use of tmpfs here it would be great). The service (CrashPlanEngine) seems to be running fine, it is the java based GUI app (CrashPlanDesktop) that is not launching (without giving any information on the terminal).

Any help much appreciated!

runnning on Ubuntu 12.04, ask for any other info that might be relevant

---

### Post by Christodoulou_Marios on 2014-01-15
to add that if i run 
```
locate swt-gtk
``` 
to see where these .so files that it is searching for are, I get

```

/usr/lib/java/swt-gtk-3.7.2.jar
/usr/lib/jni/libswt-gtk-3740.so
/usr/share/doc/libswt-gtk-3-java
/usr/share/doc/libswt-gtk-3-jni
/usr/share/doc/libswt-gtk-3-java/README.Debian
/usr/share/doc/libswt-gtk-3-java/README.gz
/usr/share/doc/libswt-gtk-3-java/changelog.Debian.gz
/usr/share/doc/libswt-gtk-3-java/copyright
/usr/share/doc/libswt-gtk-3-jni/changelog.Debian.gz
/usr/share/doc/libswt-gtk-3-jni/copyright
/usr/share/java/swt-gtk-3.7.jar
/usr/share/java-config/libswt-gtk-3-java
/usr/share/lintian/overrides/libswt-gtk-3-java
/var/cache/apt/archives/libswt-gtk-3-java_3.7.2-2_amd64.deb
/var/cache/apt/archives/libswt-gtk-3-jni_3.7.2-2_amd64.deb
/var/lib/dpkg/info/libswt-gtk-3-java.list
/var/lib/dpkg/info/libswt-gtk-3-java.md5sums
/var/lib/dpkg/info/libswt-gtk-3-java.postinst
/var/lib/dpkg/info/libswt-gtk-3-java.prerm
/var/lib/dpkg/info/libswt-gtk-3-jni.list
/var/lib/dpkg/info/libswt-gtk-3-jni.md5sums

```

There is another a solution proposed [here]("http://askubuntu.com/questions/199622/cannot-load-swt-library-unsatisfiedlinkerror-no-swt-gtk-4233") but in my case I could not figure out what to do.  This seems to be the file that would be needed: /usr/lib/jni/libswt-gtk-3740.so  but it is a different version than the on it is searching...

---

### Post by fbugnon on 2014-06-06
I was having the same problem after a regular installation of CrashPlan on my Ubuntu 14.04 (GUI would quit after few seconds, without any error message).

I found the solution on CrashPlan's site:  [http://support.code42.com/CrashPlan/Latest/Troubleshooting/CrashPlan_Client_Closes_In_Some_Linux_Installations](http://support.code42.com/CrashPlan/Latest/Troubleshooting/CrashPlan_Client_Closes_In_Some_Linux_Installations)

And now it works without a problem.

I'll copy the solution in here just in case the page became unaccessible:

[INDENT]Recommended Solution[/INDENT]

[INDENT]1. Edit the run.conf file in your CrashPlan app installation directory
[Default location]("http://support.code42.com/Administrator/3.6_And_4.0/Monitoring_And_Managing/File_And_Folder_Hierarchy#Linux_2"): [COLOR="#008000"]/usr/local/crashplan/bin/[/COLOR]
2. Navigate to the end of the GUI_JAVA_OPTS section
3. Add this line, inside the quotes:
[COLOR="#008000"]-Dorg.eclipse.swt.browser.DefaultType=mozilla[/COLOR]
Example:[/INDENT]

[INDENT]```
SRV_JAVA_OPTS="-Dfile.encoding=UTF-8 -Dapp=CrashPlanService -DappBaseName=CrashPlan -Xms20m -Xmx512m -Djava.net.preferIPv4Stack=true -Dsun.net.inetaddr.ttl=300 -Dnetworkaddress.cache.ttl=300 -Dsun.net.inetaddr.negative.ttl=0 -Dnetworkaddress.cache.negative.ttl=0 -Dc42.native.md5.enabled=false"
GUI_JAVA_OPTS="-Dfile.encoding=UTF-8 -Dapp=CrashPlanDesktop -DappBaseName=CrashPlan -Xms20m -Xmx512m -Djava.net.preferIPv4Stack=true -Dsun.net.inetaddr.ttl=300 -Dnetworkaddress.cache.ttl=300 -Dsun.net.inetaddr.negative.ttl=0 -Dnetworkaddress.cache.negative.ttl=0 -Dc42.native.md5.enabled=false -Dorg.eclipse.swt.browser.DefaultType=mozilla"
```[/INDENT]

---

### Post by rewyllys on 2014-08-22
@fbugnon:  Very helpful post.  Many  thanks  for making it.

---

### Post by Moonshooter on 2014-11-05
Worked for me. Thanks for posting.

---

### Post by wscott on 2015-01-22
I had a similar problem and after I deleted the /tmp/.cpswt directory things started working again.  I guess it had become corrupted.

---

