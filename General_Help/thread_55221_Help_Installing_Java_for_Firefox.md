---
title: "Help Installing Java for Firefox"
date: 2005-08-07
forum: General Help
---

### Post by Penguinette on 2005-08-07
Does anyone know which folder I need to install Java for firefox in to make it actually work with Firefox?  I really wish I could sign in as root actually get some work done instead of being stuck doing everything from the root command line.

(Sorry, just frustrated)

Thanks to anyone that can help.

---

### Post by Strangerdave on 2005-08-08
So you are not allowed to act as root?  Then I am not sure your problem can be solved.  However, should you gain root access, [this](http://ubuntuguide.org/#jre) should do it for you.

-SD-

---

### Post by mbweb on 2005-08-08
[QUOTE=Strangerdave]So you are not allowed to act as root?  Then I am not sure your problem can be solved.  However, should you gain root access, [this](http://ubuntuguide.org/#jre) should do it for you.

-SD-[/QUOTE]
 If I get you, you do have the root pwd and know how to use the terminal command line "su" but what you need to know is where to place java.

I put java under /usr/java and it worked fine.  The key was creating a symbolic link under the firefox installation folder:

 $ ln -s [path-to-java-plugin]  <firefox>/plugins/

I found detailed instructions when I downloaded and installed the jsdk 5.0 from java.sun.com.  Look here for complete  details:

[http://java.sun.com/j2se/1.5.0/manual_install_linux.html](http://java.sun.com/j2se/1.5.0/manual_install_linux.html)

---

### Post by eelozano on 2005-08-08
[http://ubuntuguide.org/#jre](http://ubuntuguide.org/#jre)

---

