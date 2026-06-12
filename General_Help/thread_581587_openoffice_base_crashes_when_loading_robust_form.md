---
title: "openoffice base crashes when loading robust form"
date: 2007-10-19
forum: General Help
---

### Post by thebrotherofasis on 2007-10-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/154491](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/154491) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Background:
I recently installed ubuntu 7.10. I had previously developed a robust database in openoffice.org 
This bug has been present since previous versions of openoffice in ubuntu (7.04 at least).

Problem:
When trying to load a form which is built upon many queries, and which stems from different tables, openoffice.org base, when trying to run the queries to execute the form, simply takes too long, and suddenly starts coming up with java bugs, telling me that I can't find this or the other primary keys, and it simply seems too much of a form for it to open it in a clean and easy manner.

I think it is due to the default JRE openoffice comes with. I ran the same odb file in a suse 10.3 machine and it took it 5 seconds to open the database, with no single error. I'm not sure, but I think it uses a different Java Runtime Environment, which is implicated in the execution of queries. I assume this also because the errors ubuntu openoffice.org base comes up with are like this:

"the contents of a combo box or list could not be determined. General Error: java.lang.NullPointerException".

When trying to open the specific form for several (many) times, it finally loads it with no problems. I assume this is because it somehow loads it in RAM or cache, and can finally execute it after attempting for several times.

Something else: If I execute the queries first, and THEN, I try to load the form, it doesn't crash. It takes way more time than in other distros, but it works good.

Thank you for your help.

---

### Post by thebrotherofasis on 2007-10-21
My problem was solved when I installed Sun Java 5.0 Runtime through synaptic, and then, went to Openoffice tools -> Options, under Openoffice.org -> Java -> activated Sun Microsystems Inc. 1.5.0_13

This seems to be some kind of an engine under which OO performs queries much faster, and much better. Now I don't have the above problem anymore.

Hope this helps. Also beware that installing Sun Java 5.0 implies understanding the legal issues behind.

Blessings.

---

### Post by brolin on 2008-06-19
Your advice seems to have solved my problem.  Thank you.

I am using OpenOffice.org v2.4.0 on Ubuntu v8.04.  I was having problems using my contacts database with Base:  when I opened my "contacts" table, I got a java.lang.NullPointerException error dialog.  After my second attempt to open my "contacts" table, Base opened the table, but it was very slow:  it took seconds to draw all the rows, then more seconds to draw the toolbar and other parts of the window.

I checked the Java options in OpenOffice.org:  a Free Software Foundation (FSF) JRE was being used.  I immediately suspected this to be the cause of my problems because I have always used Sun's JRE, not the FSF's.

I used aptitude to install sun-java5-jre v1.5.0-15-0.  I restarted OpenOffice.org, then checked the Java options again:  Sun's JRE was now being used.

I no longer receive any error messages when opening my "contacts" table.  The rows and toolbar are drawn much quicker, but still slowly enough that I can notice the drawing progress.  It is fast enough, though.

My contacts database is very small-scale: 2 tables, 1 query, and 1 report.  I do not need any forms because I am the only user of this database:  I use the table editor to enter new records.

Because of your legal warning, I completely read the Operating System Distributor License for Java v1.1 (DLJ) whilst installing sun-java5-bin.  I can certainly understand why Ubuntu cannot include Sun's JRE in the base installation:  for example, Canonical must stop distributing Sun's JRE if they have not resolved any user-reported issues with Sun's JRE within 90 days!

PS:  "OpenOffice" is colloquial and incorrect:  the correct name is "OpenOffice*.org*".

---

