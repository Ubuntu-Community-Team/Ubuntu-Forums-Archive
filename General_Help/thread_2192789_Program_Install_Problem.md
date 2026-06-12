---
title: "Program Install Problem"
date: 2013-12-09
forum: General Help
---

### Post by courseinmiracles2 on 2013-12-09
I have a big RED CIRCLE with a white line through it at the top of my desktop. It is telling me that a program has not installed properly. It asks me to open packeage manager to see what went wrong. When I open the PM I get this...

An error occurred

The following details are provided:
E: The package **ckan-dataset-cablegate** needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

When I close the message PM also closes and now I am unable to open the software center. Or should I say it opens, I get a look at it THEN it closes.

I also tried _sudo apt-get install ckan-dataset-cablegate_ in the terminal and I get this :

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package ckan-dataset-cablegate needs to be reinstalled, but I can't find an archive for it.



 Any thoughts??

---

### Post by ian-weisser on 2013-12-09
You installed some PPA or other Non-Ubuntu package with CKAN (Comprehensive Knowledge Archive Network) functionality.
Do you know where it came from?

---

### Post by courseinmiracles2 on 2013-12-09
I got it from the software center.

---

### Post by ian-weisser on 2013-12-09
1) What is it called? I can't find any CKAN applications in Software Center.
2) What version of Ubuntu are you running?
3) Did you do any special voodoo to make it visible?
4) Did you purchase it? Or was it free?

---

### Post by courseinmiracles2 on 2013-12-09
I am using 13.10. It's full name is [B]ckan-dataset-cablegate

[/B]The software center said it didn't install properly so I went here: [http://sourceforge.net/projects/sigmaee/](http://sourceforge.net/projects/sigmaee/)  which lead me here [http://stack.lod2.eu/deb/lod2/](http://stack.lod2.eu/deb/lod2/)  and downloaded
"ckan-dataset-cablegate_20110831_all.deb"

And used the software center to open it. Still would not install.
It's free software.

P.S. Thanks for looking at this with me

P.P.S I was trying to install this  "virtuoso-opensource-6.1"

---

### Post by ian-weisser on 2013-12-09
Okay, so it seems like:
1) You downloaded Non-Ubuntu software, and 
2) Tried to install it, and it broke your system, and
3) You didn't notice the breakage until the next time you tried to install something.

That happens with Non-Ubuntu software sometimes.
Since the ckan-dataset-cablegate package isn't from a known repository, apt-get's error message makes sense.

Please try the following command and show us the entire output.
```
dpkg --audit
```

---

### Post by courseinmiracles2 on 2013-12-09
$ sudo dpkg --audit

The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 ckan-dataset-cablegate CKAN dataset cablegate as an LOD2 stack package (29146

---

### Post by ian-weisser on 2013-12-09
Ewww....

Well, let's get your system working again:
Try```
sudo dpkg --remove ckan-dataset-cablegate
```

If it returns an error, then stop and show us the complete output.
If it works, then try```
sudo apt-get update && sudo apt-get upgrade
```

If it returns an error (near the end), then show us that complete output.
It it works, then your system is fixed. Don't install that package again.

---

### Post by courseinmiracles2 on 2013-12-09
dpkg: error processing ckan-dataset-cablegate (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 ckan-dataset-cablegate

---

### Post by ian-weisser on 2013-12-09
Okay, we'll get out the BIG hammer. 
Try```
sudo dpkg --force-remove-reinstreq ckan-dataset-cablegate
```
I use "--force" flags sparingly in dpkg, and only after trying the alternatives first - they are break-the-sky medicine if misused.

---

### Post by courseinmiracles2 on 2013-12-09
dpkg: error: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !

Is the sky falling???

---

### Post by ian-weisser on 2013-12-09
Gah. Sorry for the typo:
```
sudo dpkg --remove --force-remove-reinstreq ckan-dataset-cablegate
```

---

### Post by courseinmiracles2 on 2013-12-09
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 307666 files and directories currently installed.)
Removing ckan-dataset-cablegate ...
---- starting postrm remove

*** Error S2801: [Virtuoso Driver]CL033: Connect failed to localhost:1111 = localhost:1111.
at line 0 of Top-Level:

dpkg: error processing ckan-dataset-cablegate (--remove):
 subprocess installed post-removal script returned error exit status 3
Errors were encountered while processing:
 ckan-dataset-cablegate


P.S. I just did a restart, no change as yet.

---

### Post by courseinmiracles2 on 2013-12-09
What about manually deleting all the "virtuoso-opensource-6.1" folders and files?

---

### Post by ian-weisser on 2013-12-09
Is the package still installed? Usually the "--force" flag overrides such errors.
```
dpkg -l | grep ckan
```
The result code will tell us.

Manually deleting other packages is possible, but I don't see where ckan-dataset-cablegate is a dependency of virtuoso-opensource-6.1...so I don't see how it would help.

---

### Post by courseinmiracles2 on 2013-12-09
dpkg -l | grep ckan
rHR ckan-dataset-cablegate                    20110831                                   all          CKAN dataset cablegate as an LOD2 stack package (29146 triple)

---

### Post by ian-weisser on 2013-12-09
Okay, let's do a workaround.
I looked at the failing script, and I saw nothing terribly important in it, so let's bypass it:
```
sudo mv /var/lib/dpkg/info/ckan-dataset-cablegate.postrm /tmp/
```

Then let's try the removal again:
```
sudo dpkg --remove --force-remove-reinstreq ckan-dataset-cablegate
```

---

### Post by courseinmiracles2 on 2013-12-09
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 307659 files and directories currently installed.)
Removing ckan-dataset-cablegate ...

I will do another restart, fingers crossed

---

### Post by ian-weisser on 2013-12-09
I don't quite understand the restart. I don't see anything here the affects the kernel or otherwise would need a restart. Perhaps I'm missing something?
(Indeed a restart may be counterproductive - the workaround moved that balking file to /tmp in case we need to restore it...and /tmp gets erased at restart)

If the package is gone, then try ```
sudo apt-get update && sudo apt-get upgrade
```to see if your package manager is working properly.

---

### Post by courseinmiracles2 on 2013-12-09
[size=7]yes![/size]

---

### Post by ian-weisser on 2013-12-09
Glad we could help you out.

---

### Post by courseinmiracles2 on 2013-12-09
Package manager now accessable and so is software center.
Ian you rock!
Thank you so much.

---

