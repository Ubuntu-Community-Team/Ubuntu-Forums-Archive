---
title: "LIbreOffice Base crashes Ubuntu 16.04"
date: 2017-06-20
forum: General Help
---

### Post by alaric-cundy on 2017-06-20
I have been using Ubuntu Base for many years without any trouble.  All of a sudden this evening I have been hit by a weird problem.  I open the - any odb - document without any problems, and it will let me inspect 'Forms', 'Queries', and 'Reports' but the moment I click on the 'Tables' tab, it crashes out of LibreOffice.  I went back to the latest back-up of the document, with the same effect.  I have tried it on 4 different computers, with the same effect on all of them.  It seems to have started to happen immediately following the update to the latest Linux Kernel, though that could be coincidental.  Any suggestions?

---

### Post by #&amp;thj^% on 2017-06-20
Just a thought... maybe see if "Hardware Acceleration" and OpenGL in Tools-> Option? is enabled
OpenGL is enabled by default and it sometimes produces weird behavior's of LibreOffice under Ubuntu 16.04.

---

### Post by alaric-cundy on 2017-06-21
Ah! I am a bit short of time to explore this issue properly BUT this morning I tried a quick check: I booted under Kernel version 4..4.0-79 and found that the problem went away. When booted under 4.4.0.81 it comes back again......  Should this problem be filed as a bug report? I'm unsure how to do that.

---

### Post by #&amp;thj^% on 2017-06-21
> **alaric-cundy said:**
> Ah! I am a bit short of time to explore this issue properly BUT this morning I tried a quick check: I booted under Kernel version 4..4.0-79 and found that the problem went away. When booted under 4.4.0.81 it comes back again......  **_Should this problem be filed as a bug report? I'm unsure how to do that._**

Just **"my" **view here,...I have no problems with LO in any kernels used.
But your tests with 4 other computers showing the same makes me wonder??
And before you file a bug against Libreoffice Please read this.
Many tips here to help.
[https://wiki.ubuntu.com/LibreOfficeBugWrangling](https://wiki.ubuntu.com/LibreOfficeBugWrangling)

Beginners Guide to Filing Bug Reports
[https://ubuntuforums.org/showthread.php?t=1011078](https://ubuntuforums.org/showthread.php?t=1011078)

---

### Post by alaric-cundy on 2017-06-25
Thanks for those comments

I have a viable short-term work-around, which is to boot under an earlier kernel version, when everything then works just as expected.  This problem with LO Base is completely reproducible across all four computers that I have access to, all of which are running, by default, under kernel version 81 with 16.04 LTS.  The issue is accompanied by a 'Ubuntu Internal error' message and I have been invited to file a crash report, which I have done.  I will file a bug report for LO too.

---

### Post by osbornehouse on 2017-08-17
> **alaric-cundy said:**
> I have been using Ubuntu Base for many years without any trouble.  All of a sudden this evening I have been hit by a weird problem.  I open the - any odb - document without any problems, and it will let me inspect 'Forms', 'Queries', and 'Reports' but the moment I click on the 'Tables' tab, it crashes out of LibreOffice.  I went back to the latest back-up of the document, with the same effect.  I have tried it on 4 different computers, with the same effect on all of them.  It seems to have started to happen immediately following the update to the latest Linux Kernel, though that could be coincidental.  Any suggestions?

New to this, so hope I'm following correct procedure.
I have had a similar issue to the one you describe and waited to see if subsequent ubuntu updates will fixed it. I am now running 4.4.0-92, but no joy. The moment I try to access a table via an existing query, form or report, or indeed select the 'table' tab - it crashes. After a while I get a message box "Sorry Ubuntu 16.04 has experienced an internal problem". Is there something I am missing to solve this problem? Is there a fix available? Any help would be appreciated. Thanks.

---

### Post by alaric-cundy on 2017-08-18
> **osbornehouse said:**
> New to this, so hope I'm following correct procedure.
I have had a similar issue to the one you describe and waited to see if subsequent ubuntu updates will fixed it. I am now running 4.4.0-92, but no joy. The moment I try to access a table via an existing query, form or report, or indeed select the 'table' tab - it crashes. After a while I get a message box "Sorry Ubuntu 16.04 has experienced an internal problem". Is there something I am missing to solve this problem? Is there a fix available? Any help would be appreciated. Thanks.

I have been tearing my hair out with this issue ever since I first posted it.  I have followed various suggestions I have found elsewhere on the forums and in the LibreOffice forums, but to no avail.  If, via the Grub menu, I boot under kernel version 4.4.0.79 or older everything is absolutely fine, but under any more recent version it crashes out as soon as I attempt to access the list of tables.  Help! Surely someone out there can help?  Please!!!!!!!!!  What happened with 4.4.0.81 that caused Base to go wrong?

POST-SCRIPT: I have found something that might help someone to help those of us who are suffering from this problem.  And, by the way, in different threads and in different forums, I have found loads of people experiencing the same effect.  I found two copies of a system database called biblio.odb. 

The one located at usr/lib/libreoffice/presets/database is shown as owner 'root'; I can happily open that document and I can access the single table that it contains, though I can't make any changes to the table because I am not the owner.  

There is also a copy at home/username/.config/libreoffice/4/user/database.  'Properties' then 'Permissions' shows that I am the owner of that copy; that version crashes as soon as I try to access the list of tables - just as is the case with my own databases.  

However, if I copy the root-owned version to, say, Documents, the ownership of the copy changes to 'Me', but I find that if I open this copy, not only can I access the table, I also have full read / write access so I can add new tables and update the existing one - i.e., it behaves perfectly.

Do these observations throw any light on the matter?

---

### Post by alaric-cundy on 2017-08-18
Further to my previous update: the biblio database - that is the one that works fine - is a dbase file; all of those that crash are HSQLDB embedded files.

---

### Post by alaric-cundy on 2017-08-19
I think I have an explanation for these woes, but not a solution.

HSQLDB format databases depend on Oracle Java.  I found this comment on another Forum: "**Oracle Java (JVM/JDK) will not be available in the Debian / Ubuntu  repositories anymore because Oracle retired the "Operating System  Distributor License for Java" (JDL) and the only release available in  the repositories will be OpenJDK**."  My system update logs show multiple recent failures of the installation of Java.  So we need to remove Oracle Java and use OpenJDK instead, but I can't anywhere find out how to do that.

---

### Post by psherlocksdb on 2017-08-25
I came across this post on the Libre Office site:
[https://ask.libreoffice.org/en/question/120447/libreoffice-base-crashes-on-32bit-linux/](https://ask.libreoffice.org/en/question/120447/libreoffice-base-crashes-on-32bit-linux/) 

As the first answer describes, I added the extra parameter 'stack_guard_gap=1' to the grub file and LibreOffice Base is now working again for me. I had previously uninstalled and reinstalled LibreOffice, but this may not be necessary. The answer recommends removing this parameter when future upgrades to the kernel or LibreOffice resolve the problem.

---

