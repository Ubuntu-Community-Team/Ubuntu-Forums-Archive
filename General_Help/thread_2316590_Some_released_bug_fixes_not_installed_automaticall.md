---
title: "Some released bug fixes not installed automatically"
date: 2016-03-09
forum: General Help
---

### Post by buisteric on 2016-03-09
Hi,

I am experiencing issue [https://bugs.launchpad.net/ubuntu/+source/unity-webapps-launchpad/+bug/1369208](https://bugs.launchpad.net/ubuntu/+source/unity-webapps-launchpad/+bug/1369208) almost each time I am starting my Ubuntu box. This is really annoying and there is no workaround other than ditching Unity and use GNOME3 which causes a lot more problems for me. The issue was moved to Fix released, but apt-get update + apt-get dist-upgrade doesn't get any fix. According to the report shown on screen, which I cannot find any way to copy/paste, version of the offending unity-webapps-launchpad application is version 4.2.0-30.36-generic-4.2.8-ckt3. The fixed version is 2.4.16+16.04.20151119-0ubuntu1, so uses a completely different version scheme.

How can I get the fixed unity-webapps-launchpad version then? Do I have to enable other repositories? Why aren't these repositories always enabled?

---

### Post by mastablasta on 2016-03-09
versioning smells like it was made for Ubuntu 16.04 version.

A PPA might also be available to pull in the solution, if you can not simply manually download and add the package.

what is your Ubuntu version?

---

### Post by buisteric on 2017-01-03
I was using 15.10 at that time, so the fix was only released for the upcoming 16.04. I ended up removing unity-webapp-launchpad package and that solved the problem.

---

