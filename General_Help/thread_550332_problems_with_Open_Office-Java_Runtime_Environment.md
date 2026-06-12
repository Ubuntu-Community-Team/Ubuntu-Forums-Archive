---
title: "problems with Open Office-Java Runtime Environment"
date: 2007-09-13
forum: General Help
---

### Post by Richardinho on 2007-09-13
hello guys.

I'm trying to get Open Office to work. Generally it works fine for some things eg. word processing/ spread sheets for example, but I'm trying to use Database, but when I try and create a Database I get the pop up message along the lines of 'Open office requires Java runtime environment  this selected JRE is defective. Please select another version or install a new JRE and select under tools, options..'

I'm not entirely sure what this means, and what I need to do to fix it? I have already done a search and got the gist of what a JRE is and where I can download a new one, but I would have thought that having downloaded edgy eft (upgraded from dapper drake) that this should all have happened automatically. The fact that part of office works ok makes me wonder if this is a bug?

Any help appreciated.

---

### Post by Irihapeti on 2007-09-13
The version of OpenOffice that comes with the distro doesn't work well in some areas. Database is one of them. You can download the official version from OpenOffice and install it.

Details are here: [http://ubuntuforums.org/showthread.php?t=413392&highlight=Open+Office&nojs=1#goto_threadtools](http://ubuntuforums.org/showthread.php?t=413392&highlight=Open+Office&nojs=1#goto_threadtools)

HTH
Irihapeti

---

### Post by aksu358 on 2008-05-08
Hi,

I had the same problem.

It occured after I upgraded from Gutsy to Hardy.

If fixed it by removing the .openoffice2 directory.  Actually renamed it to _.openoffice2, the effect was the same.

When OO restarts. it recreates the the missing directory, and this solved the problem.  I guess there would have been a conf file somewhere but I was too lazy too look.

After it was working, I copied the contents of my old "templates" folder in the new one.

A bit of dirty hack, but it worked for me.

The other common check (assuming you have a JRE installed (sun-java .. etc)), it to go to "Tools -> Options -> Java" and after a moment, click on one of the radio buttons to choose an installed JRE.

Does either of these solutions work for you?

Cheers,
Alex

---

### Post by anupkshah on 2008-05-17
I was having the same problem (on Kubuntu 8.04) and found that I just needed to remove ~/.openoffice.org2/user/config/javasettings_Linux_x86.xml and then it was okay. (When restarting OpenOffice, this file seems to get recreated).

hth.

---

### Post by purachochada on 2008-06-09
in my case (ubuntu:hardy) this didn't solve the problem!

but found this page: [http://plagatux.es/?p=296]("http://plagatux.es/?p=296") (sorry it's in spanish!)
or this bug report: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/193139]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/193139")

in a nutshell...to solve the problem, install **openoffice.org-java-common**

hope that helps

---

