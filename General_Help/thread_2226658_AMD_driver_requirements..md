---
title: "AMD driver requirements."
date: 2014-05-28
forum: General Help
---

### Post by maazmahmood on 2014-05-28
I have Radeon 7850. And was reading release notes for the linux drivers and the requirements ar
[LIST]
[*]Xorg/Xserver 7.4 and above (up to 1.14) 
[*]Linux kernel 2.6 or above (up to 3.11) 
[/LIST]
My kernel version is like 3.14. So do I have to downgrade to be able to use the 14.6 beta driver? the Xorg part makes no sense 7.4 to 1.14?

Another question. I was following this tutorial on how to install AMD drivers, and the guy used the GUI path. But in the video he had selected "Install driver" I was told to select "generate driver specific distro packages". Because that way you were able to generate all the required packages. So how was he able to do it and have it work?

[https://www.youtube.com/watch?v=evqpassbyqA](https://www.youtube.com/watch?v=evqpassbyqA)

**Update** And according to this site (towards bottom), it says for you to install the driver specific distro packages. how do I go about installing those packages then?

[http://support.amd.com/en-us/kb-articles/Pages/Catalyst-Linux-Installer-Notes.aspx](http://support.amd.com/en-us/kb-articles/Pages/Catalyst-Linux-Installer-Notes.aspx)

---

### Post by pqwoerituytrueiwoq on 2014-05-28
open your 'software and updates' application and click on additional drivers
if you need to do something more advanced look here
[https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD)

---

### Post by QIII on 2014-05-28
Hello!  In the wiki referenced above (also see my signature), I have given the instructions for using the command line, which I recommend over the GUI method.  Be aware that I have had a problem with fglrx-updates this time around in that my GPU runs substantially hotter. You may be better off using the straight fglrx versions rather than the fglrx-updates.  Also be sure to read the section I put in there about adding hardware acceleration.

Cheers.

---

### Post by grahammechanical on 2014-05-28
The expression "distribution specific packages" is a reference to the fact that different distributions have different package formats.

Distributions based upon Redhat, such as Fedora use RPM (Rehat Package Manager). So, a person would look for a package with .rpm at the end of the file name.

Ubuntu is based upon Debian which uses the deb format (Debian Software Package). So, a person would look for a package with .deb at the end of the file name. Often we will see links to downloads listed specifically for Ubuntu. That is what it is best to look for. The package name will also end in .deb.

We cannot install a .rpm package on Ubuntu.

Regards.

---

### Post by pqwoerituytrueiwoq on 2014-05-28
> **grahammechanical said:**
> We cannot install a .rpm package on Ubuntu.

but this software exist[SUP] (below image is a link to software center)[/SUP]
[[IMG]http://i.imgur.com/Dq7kOocm.png[/IMG]]("apt:alien")

---

### Post by maazmahmood on 2014-05-29
So the generate distro packages isn't that important? And where does it  generate? And since it'll be .deb packages I can just isntall them with  dpkg -i right?

---

