---
title: "MoneyDance - no print service found"
date: 2007-01-12
forum: General Help
---

### Post by OMRebel on 2007-01-12
Does anyone here using MoneyDance?  I just started using it, and when I try to print anything, I get "print service not found".  I did some googling, but couldn't come up with a real resolution.  Any help would be appreciated. 

Thanks.

---

### Post by dcstar on 2007-01-12
> **OMRebel said:**
> Does anyone here using MoneyDance?  I just started using it, and when I try to print anything, I get "print service not found".  I did some googling, but couldn't come up with a real resolution.  Any help would be appreciated. 

Thanks.

Mine works fine, my Linux printer comes up in the list of printers and I can send print jobs to it.

You must have a CUPS printer installed and working.

---

### Post by OMRebel on 2007-01-12
My printer is installed and working with Cups.  From searching online, seems to be something with how Java talks with Cups to send the print jobs?

---

### Post by dcstar on 2007-01-12
> **OMRebel said:**
> My printer is installed and working with Cups.  From searching online, seems to be something with how Java talks with Cups to send the print jobs?

What Java do you have in your system, I have the sun-java5-bin & sun-java5-jre packages installed?

There is also a printing setup in Preferences, mine is set to Java 2.

---

### Post by measekite on 2007-10-24
> **OMRebel said:**
> Does anyone here using MoneyDance?  I just started using it, and when I try to print anything, I get "print service not found".  I did some googling, but couldn't come up with a real resolution.  Any help would be appreciated. 

Thanks.

i have the same exact problem.  I am running Feisty.  I have a cups printer and it works great with all other applications.  Printing is what is stopping me from purchasing a license for moneydance.  Other than that I think it is very good.

I went to synaptic and installed what ever run time JRE they had and then money dance did not work at all so I had to remove it.

Anybody have any idea?  Nothing posted so far works but I do suspect Java.

---

### Post by measekite on 2007-10-28
> **dcstar said:**
> Mine works fine, my Linux printer comes up in the list of printers and I can send print jobs to it.

You must have a CUPS printer installed and working.


I am running cups.  This printer is shared and being accessed locally and well as by a wirelss computer through ipp and with a windows computer using windows smb.

What other way is there? How are you doing it?

---

### Post by measekite on 2007-10-28
> **dcstar said:**
> What Java do you have in your system, I have the sun-java5-bin & sun-java5-jre packages installed?

There is also a printing setup in Preferences, mine is set to Java 2.

Apparently JRE6 and JRE5 do not work with CUPS 1.2 but there is a work around but after doing the work around the jobs get stopped in the Q.

Does anyone running Feisty 7.04 have this combination working with either Moneydance or any other Java application.

The printer works fine from open office and other applications.

---

### Post by punkybouy on 2008-02-19
The only fix for me was a complete reinsatll of Feisty and installing JAVA 1.4 and nothing higher.  Possibly a version of JRE 1.5 would work but otherwise it is an ongoing problem for Moneydance users with no apparent fix.  Sun won't budge and there really is nothing wrong with CUPS its just that they changed it so later versions of JAVA don't work with it.

---

### Post by punkybouy on 2008-02-23
I believe I have a fix for this (I can't take credit I found it on the web) but the issue is page orientation.  I was able to fix printing in Ubuntu Gutsy 7.10 by going to System/Administration/Printing and selecting my printer.  From there select the "job options" tab and for an option called "orientation" select any other option BUT "automatic rotation" and printing should work although when I printed a report the margins were cut off so the date on the far left margin had a day an year but month was chopped off.

---

