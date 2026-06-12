---
title: "bin/unpack200 not found"
date: 2007-06-13
forum: General Help
---

### Post by gervase on 2007-06-13
When trying to install the accounting program Moneydance I get the following error message:
 
  /home/gervase# ./moneydance_linux_x86wj.sh 
 Unpacking JRE ... 
 Preparing JRE ... 
 ./moneydance_linux_x86wj.sh: 217: bin/unpack200: not found 
 Error unpacking jar files. Aborting. 
 You might need administrative priviledges for this operation. 
 
Moneydance similarly does not install whether I am using administrator privileges or not.  For those not familiar with Moneydance it is a java based program and there are two download packages, with or without java.  The above is with java, but again it fails to install using the without java package.

This question has been posted before by someone else on the Moneydance forum without finding a solution.  It seems to be a recent ubuntu based problem as Moneydance would install on some earlier versions.

I really need access to my Moneydance accounts.  Grateful for any help.

Gervase

---

### Post by canzel on 2008-04-16
I too had this problem but I solved it by installing ia32-sun-java6-bin. I'd installed all the others but still got error message "bin/unpack200 not found" I used the Moneydance download that comes with java - Moneydance......wj.sh

To install MoneyDance, Download and install 
javaBlackdown, 
ia32-sun-java6-bin, 
j2re, 
j2sdkl, 
java-common, 
sun-java6-xxx

Good luck!

---

