---
title: "Java"
date: 2004-10-26
forum: General Help
---

### Post by BlackFenix on 2004-10-26
How i can make  ubuntu package for java (j2sdk 1.5 - sun) ?
I don't found this package with apt-cache.

---

### Post by ulrich on 2004-10-26
this should answer your questions :)

[http://wiki.ubuntulinux.org/Java](http://wiki.ubuntulinux.org/Java)

---

### Post by adbak on 2004-10-26
I found that the Java How-to in the How-to section worked just fine for me.

[http://ubuntuforums.org/showthread.php?t=198](http://ubuntuforums.org/showthread.php?t=198)

---

### Post by burque on 2004-10-26
This worked for me okay. I'll try to be clear in my instructions, although this is not my nature  :smile: 

1) Look in the instructions for Quick Install at [http://wiki.ubuntulinux.org/Java](http://wiki.ubuntulinux.org/Java)

2) You'll have to have multiverse in your sources.list. The directions should say:
# apt-get install java-package   
download the sun jdk from java.sun.com
** edit /usr/share/java-package/sun-j2sdk.sh to reflect the actual JDK 1.5 release version.
# make-jpkg jdk-1_5_0-linux-i586.bin
# dpkg -i sun-j2sdk1.5_1.5.0_i386.deb
# apt-get install sun-j2sdk1.5debian
# update-alternatives --config java

3) The troublesome part is editing the sun--j2sdk.sh. The instructions above didn't make it really clear to me. The size of the .bin file as of today is about 44MB, so you have to change that too. Edit sun-j2sdk.sh now, adding the stuff between the bracketed entries (don't put those in!) where the 1.5 beta entry used to be:

[earlier version stuff here . . .]

        "jdk-1_5_0-linux-i586.bin")
            j2se_version=1.5.0
            j2se_expected_min_size=43 #  This reflects the smaller file size
            found=true
            ;;

[rest of shell script here]

4) NOW you can execute:
     sudo make-jpkg jdk-1_5_0-linux-i586.bin

5) I had to jump through a hoop or two here: NOW execute:
     sudo dpkg -i sun-j2sdk1.5_1.5.0_i386.deb

6) You may get error messages: I did, as below:

Selecting previously deselected package sun-j2sdk1.5.
(Reading database ... 73614 files and directories currently installed.)
Unpacking sun-j2sdk1.5 (from sun-j2sdk1.5_1.5.0_i386.deb) ...
dpkg: dependency problems prevent configuration of sun-j2sdk1.5:
 sun-j2sdk1.5 depends on sun-j2sdk1.5debian; however:
  Package sun-j2sdk1.5debian is not installed.
dpkg: error processing sun-j2sdk1.5 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-j2sdk1.5

7) Not to worry. Even if you tried this before and got dependency errors, do it now:
     sudo apt-get install sun-j2sdk1.5debian
It should now install without dependency errors.

Eight -smiley trouble 8)) NOW, again, do "sudo dpkg -i sun-j2sdk1.5_1.5.0_i386.deb"

9) You should be good to go. Execute "java -version" to make sure.

10) I went ahead and executed "update-alternatives --config java", but it turned out not to be necessary. I got the following message:

"There is only 1 program which provides java
(/usr/lib/j2sdk1.5-sun/bin/java). Nothing to configure."

Hope this helps,
Burque

---

