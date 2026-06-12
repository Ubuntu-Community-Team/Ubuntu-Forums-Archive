---
title: "Problems installing java 1.5"
date: 2005-07-22
forum: General Help
---

### Post by vinodh on 2005-07-22
I am trying to install java 1.5 with apt-get. I get the following dependancy problem. Any help in solving the dependancy problem is appreciated.

 $ sudo apt-get install sun-j2re1.5
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  sun-j2re1.5: Depends: libasound2 (> 1.0.8) but 1.0.5-1ubuntu1 is to be installed
E: Broken packages

---

### Post by Perfect Storm on 2005-07-22
Got the same problem, plus problems with other back-ports packages. As I search for the package it seems missing. They most have some truble at the back-ports or something.

---

### Post by klutzini on 2005-07-22
I also get the same trying to install Mozilla!!

Hope we find a solution..

---

### Post by Hairy_Palms on 2005-07-22
i had the same problems, id recommend downloading it from suns website, i did that and installed with no problems at all

---

### Post by klutzini on 2005-07-22
Seems to have been solved .. No package errors now..

---

### Post by proxess on 2005-07-22
i get this:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5

and changed the source list as shown on the ubuntuguide

any alternative? dont say download from sun... i cant, dotn know why.

---

### Post by proxess on 2005-07-22
ok i guess its working now, sorry for the inconvenience

---

### Post by vinodh on 2005-07-25
I was finally able to install java  \\:D/ following the instructions in :
[https://wiki.ubuntu.com//Java15](https://wiki.ubuntu.com//Java15)

Installing Sun's Java on Hoary (expanding on Gabriel Bauman's comment from above)
==================
Download Sun's JDK (.bin format) from [WWW] [http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp). Choose either the JDK or JRE link. Execute these commands (assuming you downloaded the file 'jdk-1_5_0_02-linux-i586.bin'):

% sudo apt-get install java-package fakeroot
% fakeroot make-jpkg jdk-1_5_0_02-linux-i586.bin
% sudo dpkg -i sun-j2sdk1.5_1.5.0+update02_i386.deb

Test installation:

% java -version
java version "1.5.0_02"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_02-b09)
Java HotSpot(TM) Client VM (build 1.5.0_02-b09, mixed mode, sharing)

Note: I also had to install gcc which was required for the 'make'

---

### Post by nomad311 on 2005-07-27
when i try to follow these instructions i get to:
```
% fakeroot make-jpkg jdk-1_5_0_02-linux-i586.bin
``` 
i get this error:
```

Creating temporary directory: /tmp/make-jpkg.XXXXreJnsM
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk.sh

No matching plugin was found.

```

errrr whats the deal

---

### Post by supanova on 2005-07-27
Hi All

I also need to install java and I'm doing a bit of investigation before proceeding which led me to this thread

Sorry but I'm new to Ubuntu/Debian and therefore apt-get

what does fakeroot refer to.... I can't see anything on the man pages refering to anything that you can place after the package name

Thanks

---

### Post by supanova on 2005-07-27
Sorry for a second post, but there is something strange

If I go to [http://ubuntujava.yimports.com/](http://ubuntujava.yimports.com/) and click on the documetation hyperlink explorer closes :rolleyes: 

Looking at the source for the page I found the following...

```
<a href="http://ubuntujava.yimports.com/Documentation.shtml" onmouseover="shutdown();">
``` 

Now that is really strange!  :roll: 

Ciao

---

### Post by FluffyElmo on 2005-07-27
<EDIT>
Sorry! I usually hang out in the AMD64 Users forum and assumed that's where I was. If you're running 32bit, download the following file and adjust the following paths accordingly: ***jdk-1_5_0_04-linux-i586.bin***
</EDIT>

I haven't had any problems installing Java, and while I haven't read the how-to's or used apt, here is what I did...for what it's worth. (Italics are typed from the command prompt.)
[list=1]
[*]Go to [http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp) and select '**JDK 5.0 Update 4**'.
[*]Download the following file for AMD64 (not the RPM):   '**jdk-1_5_0_04-linux-amd64.bin**'
[*]Go to where you downloaded it and make it executable: ***chmod 777 ./jdk-1_5_0_04-linux-amd64.bin***
[*]Run it: ***./jdk-1_5_0_04-linux-amd64.bin***
[*]You should now be able to run Java in the resulting directory (sorry, I'm not on my 64bit box now so the path may be wrong) ***./j2sdk1.5.0_04/bin/java -version***
[*]I usually move it out of the way, but put wherever you want. (again path may be wrong) ***sudo mv j2sdk1.5.0_04/ /usr/local/***
[*]Create a link from the java executable to somewhere on your path. (again path may vary) ***sudo ln -s /usr/local/j2sdk1.5.0_04/bin/java /usr/bin/java***[/list]

You should now be able to run* java -version *from anywhere at a command prompt and see a result. This install is sufficient for running Azureus, Netbeans and pretty much every other Java program I tried.

For Eclipse I also installed the IBM JDK, following pretty much the exact procedure to install it. Note that if you have an .rpm file, you can convert it to a .deb using: *alien filename.rpm* and then install it using: *dpkg -i filename.deb* but I haven't tried that with any JDK.

The 64bit Sun JDK/JRE doesn't include a Firefox Plug-in, you have to install Blackdown for that...I haven't done it myself though so can't help much there.

If I can help...let me know, I should be back at my 64bit box tonight.

---

### Post by FluffyElmo on 2005-07-27
Sorry! I usually hang out in the AMD64 Users forum and assumed that's where I was. If you're running 32bit, download the following file and adjust paths accordingly: ***jdk-1_5_0_04-linux-i586.bin***

---

