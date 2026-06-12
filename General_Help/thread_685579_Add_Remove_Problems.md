---
title: "Add/ Remove Problems"
date: 2008-02-02
forum: General Help
---

### Post by lkirlin on 2008-02-02
Hi, This is the first time I have received this problem, so Im not sure what to do with it; When I go to the Add/ Remove section from the applications menu, it boots like normal, however when it checks for more available installed updates, I get this:

Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

So when I check with synaptic, i get another error that tells me this when i first start the manager:

```
 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

After trying to run the code in terminal I get this:

```
kirlin@kirlin-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege
kirlin@kirlin-desktop:~$ 

 
```

How do I gain a superuser privilege and what exactly can i do to completely solve this problem?

I appreciate everyones help in this matter

---

### Post by SpiderGorilla on 2008-02-02
Super-User privilege is obtained through use of "sudo". So you'd prepend your command with this:

sudo dpkg --configure -a

And try that. It'll ask for a password. It's your login password or it SHOULD be. Give that a shot and tell us if it works.

(It should be noted that I have absolutely zero idea what dpkg --configure -a does so I don't take responsibility if that messes things up.)

---

### Post by lkirlin on 2008-02-02
After getting that figured out, I get the code

```
 kirlin@kirlin-desktop:~$ sudo dpkg --configure -a
[sudo] password for kirlin:
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-03-0ubuntu2); however:
  Package sun-java6-bin is not installed.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-plugin
kirlin@kirlin-desktop:~$ 

```

So I attempt to install java through terminal and it opens to package configuration that looks like a user agreement form, the only thing is I cant seem to agree to that or bypass it in any way, however it looks like I do need the software installed:

 &#9474; Operating System Distributor License for Java v1.1 (DLJ)                  &#8593;  
 &#9474;                                                                           &#9646;  
 &#9474; Operating System Distributor License for Java version 1.1 (DLJ)           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA PLATFORM    &#9618;  
 &#9474; STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO YOU ONLY UPON  &#9618;  
 &#9474; THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS LICENSE  &#9618;  
 &#9474; AGREEMENT (THE "AGREEMENT").  PLEASE READ THE AGREEMENT CAREFULLY.  BY    &#9618;  
 &#9474; INSTALLING, USING, OR DISTRIBUTING THIS SOFTWARE, YOU ACCEPT ALL OF THE   &#9618;  
 &#9474; TERMS OF THE AGREEMENT.                                                   &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; 1.  DEFINITIONS. "Software" means the code identified above in binary     &#9618;  
 &#9474;     form, any other machine readable materials including, but not         &#9618;  
 &#9474;     limited to, libraries, source files, header files, and data files),   &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>                                        
 &#9474;                                                                           &#9474;  
This is sort of what it looks like. So now, how do I get past this page and will this software solve my problem?

---

### Post by dexter on 2008-02-02
Is that text located in a terminal? Try using the arrow keys, page down or space to scroll down.

---

### Post by lkirlin on 2008-02-02
I solved my problem. Thank you for your help

---

