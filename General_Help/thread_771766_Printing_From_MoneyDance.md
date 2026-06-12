---
title: "Printing From MoneyDance"
date: 2008-04-27
forum: General Help
---

### Post by rahnen on 2008-04-27
I tried using Money Dance in Gutsy and I liked it very much except for the fact that I couldn't print anything.  With upgrading to Hardy I thought my problems might be solved when I saw all the CUPS upgrades...but alas still can't print via MoneyDance:(

Can anybody out there give me some guidance as to why trying to print from Money dance is such a non-starter in Ubuntu? (it works fine on my XP boot)

---

### Post by OMRebel on 2008-05-04
Go to System - Administration - Printing.

Select your printer, then the Job Options tab.  Change the "Orientation" to Landscape.  Save that change.

Close out of Moneydance and then go back in and try to print.

---

### Post by Tanker Bob on 2008-09-07
I am also unable to print from Moneydance 2008r2 (build 617). The suggestion above doesn't work here. I am using Kubuntu 8.04.1 with CUPS 1.3.7 (current) and Sun Java 6.06. Java is correctly installed and working for all else. I have tried the workaround at [the CUPS site](http://www.cups.org/articles.php?L433+TFAQ+P1+Q), but it didn't work for me. I worked on this for about 7 hours last night, trying everything that I could find here and through Google, including some other JVM versions. Nothing worked. The Java included with some Moneydance distributions never installs correctly.

Has anyone been able to print from Moneydance or any other Java app under CUPS 1.3.7 with Sun Java 6.06 or any other Java available from the Hardy repositories? TIA.

---

### Post by Tanker Bob on 2008-09-08
Solved!!! I found the solution to the printing issue in Java apps, including Moneydance. Simply install the OpenJDK-6 Java VM instead of Sun's Java-5 or -6 VMs. OpenJDK-6 b11 from the Hardy repositories fixed the latest printing disconnect between Java and CUPS. After uninstalling Sun Java 1.6 and installing OpenJDK 1.6, printing works fine in Moneydance. The rest of the program runs correctly as well, though the font spacing isn't quite as nice under OpenJDK.

---

