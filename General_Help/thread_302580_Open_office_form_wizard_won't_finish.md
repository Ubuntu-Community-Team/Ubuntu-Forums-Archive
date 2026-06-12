---
title: "Open office form wizard won't finish"
date: 2006-11-18
forum: General Help
---

### Post by piti118 on 2006-11-18
I'm using Edgy and Open office2.04 that comes with edgy. 

I open Open Office Database and set it up so that it connect to mysql server on the same machine. Everything works fine util I tried the create form wizard. I follow the step on the the wizard. But when I click the finish button nothing happens. It just stay on the last wizard page.

I tried both java 1.4 and 1.5.

Any idea how to solve this?

---

### Post by bkline on 2007-06-30
I just ran into the same problem.  I'm a little discouraged that no one ever replied to the OP after seven months.  I'll dig further and if I don't find anything helpful I'll file a bug report.

---

### Post by McHenry on 2007-07-06
This problem still exists in Feisty.
The report wizard does not run eith but simply displays a bank sheet with a header.

---

### Post by freesitebuilder on 2007-07-26
This bug is still only marked as Medium in Launchpad!

I followed Joel Parker's instructions [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/72262/](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/72262/)
but OO doesn't appear in my menus.

If I click an .odt file, it opens in Archive Manager. If I click a .doc file, it opens the "add/remove apps" dialogue. It recommends OO, and displays the version that I've just installed:
Writer module for OpenOffice.org 2.2
Writer module for OpenOffice.org 2.2
(Converted from a rpm package by alien version 8.65.)
Version: 2.2.1-9162 (openoffice.org-writer)
but clicking OK doesn't open OO. 

Synaptic shows it as installed, and properties for Calc (as an example) shows:
> 
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/openoffice.org-calc
/usr/share/doc/openoffice.org-calc/changelog.Debian.gz
/usr/share/doc/openoffice.org-calc/copyright
/opt
/opt/openoffice.org2.2
/opt/openoffice.org2.2/share
/opt/openoffice.org2.2/share/registry
/opt/openoffice.org2.2/share/registry/modules
/opt/openoffice.org2.2/share/registry/modules/org
/opt/openoffice.org2.2/share/registry/modules/org/openoffice
/opt/openoffice.org2.2/share/registry/modules/org/openoffice/Setup
/opt/openoffice.org2.2/share/registry/modules/org/openoffice/Setup/Setup-calc.xcu
/opt/openoffice.org2.2/share/registry/modules/org/openoffice/TypeDetection
/opt/openoffice.org2.2/share/registry/modules/org/openoffice/TypeDetection/Types
/opt/openoffice.org2.2/share/registry/modules/org/openoffice/TypeDetection/Types/fcfg_calc_types.xcu
/opt/openoffice.org2.2/share/registry/modules/org/openoffice/TypeDetection/Filter
/opt/openoffice.org2.2/share/registry/modules/org/openoffice/TypeDetection/Filter/fcfg_calc_filters.xcu
/opt/openoffice.org2.2/share/registry/modules/org/openoffice/Office
/opt/openoffice.org2.2/share/registry/modules/org/openoffice/Office/Common
/opt/openoffice.org2.2/share/registry/modules/org/openoffice/Office/Common/Common-calc.xcu
/opt/openoffice.org2.2/share/registry/modules/org/openoffice/Office/Embedding
/opt/openoffice.org2.2/share/registry/modules/org/openoffice/Office/Embedding/Embedding-calc.xcu
/opt/openoffice.org2.2/share/registry/schema
/opt/openoffice.org2.2/share/registry/schema/org
/opt/openoffice.org2.2/share/registry/schema/org/openoffice
/opt/openoffice.org2.2/share/registry/schema/org/openoffice/Office
/opt/openoffice.org2.2/share/registry/schema/org/openoffice/Office/UI
/opt/openoffice.org2.2/share/registry/schema/org/openoffice/Office/UI/CalcCommands.xcs
/opt/openoffice.org2.2/share/registry/schema/org/openoffice/Office/UI/CalcWindowState.xcs
/opt/openoffice.org2.2/share/registry/data
/opt/openoffice.org2.2/share/registry/data/org
/opt/openoffice.org2.2/share/registry/data/org/openoffice
/opt/openoffice.org2.2/share/registry/data/org/openoffice/Office
/opt/openoffice.org2.2/share/registry/data/org/openoffice/Office/UI
/opt/openoffice.org2.2/share/registry/data/org/openoffice/Office/UI/CalcCommands.xcu
/opt/openoffice.org2.2/share/registry/data/org/openoffice/Office/UI/CalcWindowState.xcu
/opt/openoffice.org2.2/share/xdg
/opt/openoffice.org2.2/share/xdg/calc.desktop
/opt/openoffice.org2.2/help
/opt/openoffice.org2.2/help/en
/opt/openoffice.org2.2/help/en/scalc.db
/opt/openoffice.org2.2/help/en/scalc.cfg
/opt/openoffice.org2.2/help/en/scalc.tree
/opt/openoffice.org2.2/help/en/scalc.idx
/opt/openoffice.org2.2/help/en/scalc.idx/POSITIONS
/opt/openoffice.org2.2/help/en/scalc.idx/SCHEMA
/opt/openoffice.org2.2/help/en/scalc.idx/OFFSETS
/opt/openoffice.org2.2/help/en/scalc.idx/EDGE
/opt/openoffice.org2.2/help/en/scalc.idx/DOCS.TAB
/opt/openoffice.org2.2/help/en/scalc.idx/CONTEXTS
/opt/openoffice.org2.2/help/en/scalc.idx/DICTIONARY
/opt/openoffice.org2.2/help/en/scalc.idx/DOCS
/opt/openoffice.org2.2/help/en/scalc.idx/LINKNAMES
/opt/openoffice.org2.2/help/en/scalc.jar
/opt/openoffice.org2.2/help/en/scalc.key
/opt/openoffice.org2.2/help/en/scalc.ht
/opt/openoffice.org2.2/program
/opt/openoffice.org2.2/program/resource
/opt/openoffice.org2.2/program/resource/sc680en-US.res
/opt/openoffice.org2.2/program/resource/analysis680en-US.res
/opt/openoffice.org2.2/program/resource/date680en-US.res
/opt/openoffice.org2.2/program/resource/bf_sc680en-US.res
/opt/openoffice.org2.2/program/libcalc680li.so
/opt/openoffice.org2.2/program/libbf_sc680li.so
/opt/openoffice.org2.2/program/libscd680li.so
/opt/openoffice.org2.2/program/libsc680li.so
/opt/openoffice.org2.2/program/scalc
/opt/openoffice.org2.2/program/libscui680li.so
/opt/openoffice.org2.2/program/libdate680li.so
/opt/openoffice.org2.2/program/libanalysis680li.so

I'm still playing with this, so if anyone else has solved the problem I'd be pleased to hear it!

---

### Post by carusoswi on 2007-09-14
I just did a search on Open Office Database to browse for a solution for the exact same problem.  I cannot use OOdb until I am able to get it to work.

My search term brought up a number of threads along the lines of can you totally switch to Ubuntu from XP and, having Ubuntu, why would you keep XP, etc.

Well, a relational database is key to what I do both on a personal and professional basis.  I would think Ubuntu would ship a working copy of OO on their install disc, but that apparently is not the case.

I understand the whole business about how Ubuntu and OO are developed, so it isn't right to rant at Ubuntu (or anyone else) about this problem.  But, my point is that without a rudimentary relational database, OO is one lame application.

We complain about Gates, MS, and non-free software, but, until we can get truly functioning OS replacements for these very basic functions, then, I will be forced to continue using MSXP.

Caruso

> **piti118 said:**
> I'm using Edgy and Open office2.04 that comes with edgy. 

I open Open Office Database and set it up so that it connect to mysql server on the same machine. Everything works fine util I tried the create form wizard. I follow the step on the the wizard. But when I click the finish button nothing happens. It just stay on the last wizard page.

I tried both java 1.4 and 1.5.

Any idea how to solve this?

---

### Post by Hagar Delest on 2007-09-15
It's a rather known bug and the only fix is to install the official version of OOo instead of the Ubuntu version, see here : [[Ubuntu] Installing OOo on Debian and Co.](http://www.8daysaweek.co.uk/forums/viewtopic.php?t=759)

---

### Post by uh9b on 2007-09-16
Here the same problem. The wizard is not finishing and openoffice base does not work well. First I changed to Ubuntu LTS - there openoffice base works, but the LTS-Version does not provide software like kile, which is important for me. Then I installed debian etch, there base did not work at all. At last I installed fedora. Now it works. 
By the way, with ubuntu I struggled for days to setup my widescreen together with the intel graphics chipset in my computer. With fedora it runs out of the box.

---

