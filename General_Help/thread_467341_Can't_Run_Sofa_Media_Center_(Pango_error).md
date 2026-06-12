---
title: "Can't Run Sofa Media Center (Pango error)"
date: 2007-06-07
forum: General Help
---

### Post by castironpants on 2007-06-07
I'm able to compile Sofa Media Center, but when I attempt to run it I just get


jeremy@box:~$ sofa
sofa 0.2.2
Copyright (c) 2007 Pierre-Luc Beaudoin
This is free software.  You may redistribute copies of it under the terms of
the GNU General Public License <http://www.gnu.org/licenses/gpl.html>.
There is NO WARRANTY, to the extent permitted by law.


(sofa:2131): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed

(sofa:2131): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed
Segmentation fault (core dumped)

---

### Post by sabrewolf2006 on 2007-06-07
Hi,
sorry I can't help an all..
it doesn't work here either, same error
:(

I tried the 0.2.2 release
Gonna try svn.. see if its been addressed in ChangeLog
[Update]Rats.. that's a no go too
Although I have found an email address and sent a bug report..

[Update]Solution is the schema file needs installing manually..
gconftool-2 --install-schema-file ~/sofa-0.2.2/schema.xml

---

### Post by squidy on 2007-06-09
This bug is corrected in the latest SVN, sofa does not crash if no schema is installed.

Plus, there seems to be a bug in gconfd, if a schema is installed at root, gconfd won't see it until it is restarted ...

---

### Post by castironpants on 2007-06-09
Where can I get the latest SVN?

---

### Post by squidy on 2007-06-10
Have a look at [http://sofa.sf.net](http://sofa.sf.net) under Developer, Project page, SVN

---

### Post by castironpants on 2007-06-10
Well, now it does work (on and off, usually off) but it doesn't load any of the modules. All it has is the dummy one.

---

### Post by squidy on 2007-06-10
Please read the whole tutorial.

> 
Only the demo module is turned on by default. To activate other modules, you have to run sofa-config. You have to place a check in all the modules you want in the column Active.


---

