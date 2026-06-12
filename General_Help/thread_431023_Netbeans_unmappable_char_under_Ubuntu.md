---
title: "Netbeans unmappable char under Ubuntu"
date: 2007-05-02
forum: General Help
---

### Post by jdogzilla on 2007-05-02
Hello, I have Ubuntu 7.04, jdk 1.6 and netbeans 5.5

I'm trying to compile code from a project at sourceforge.net.  I'm getting the following compile time error under Netbeans:

/projects/x360mediaserve/x360mediaserve/net/sourceforge/x360mediaserve/utils/StringUtils.java:7: unmappable character for encoding UTF8 
result.replace("&#65533;","&iuml;"); 
                         ^ 
13 errors 

(note that the caret points to the special character "&#65533;" )

For some reason, the special character is not recognized under Ubuntu.  However, the same code compiles with no warnings or anything under Windows on my laptop.  Any suggestions on what I need to do, either under Netbeans, or under the Ubuntu environment, to make this compile cleanly? 

THanks

---

### Post by dante.regis on 2007-05-02
Take a look at this site: [Netbeans and UTF8 encoding]("http://ditoinfo.wordpress.com/2007/02/26/netbeans-and-utf8-encoding-2/")

It might help you.

---

### Post by jdogzilla on 2007-05-07
Hello ... thanks for the suggestion ... and thanks for putting this in the Netbeans Wiki too ... I made the change, and even the other env change suggested by Netbeans ... rebooted, but still no luck.  They say this will be resolved with Netbeans 6, but I'm hoping I can resolve this now.  Any other suggestions?

Thanks

---

### Post by ckullmann on 2007-09-27
I had a similar problem and for me worked setting Netbeans to ISO-8859-1.
You can do that either in the compiler options using 

-encoding ISO-8859-1

or you follow the instructions as in the link given by dante, but setting not to UTF 8 but to ISO-8859-1

So here the summary:
Go to <netbeanfolder>/etc/netbeans.conf
Go to the line with the "netbeans_default_options"
add "-J-Dfile.encoding=ISO-8859-1" at the end inside the quotation marks.

This worked for me, might work for you as well :)
Cheers
Chris

---

