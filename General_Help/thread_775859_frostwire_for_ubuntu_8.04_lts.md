---
title: "frostwire for ubuntu 8.04 lts"
date: 2008-04-30
forum: General Help
---

### Post by krysia on 2008-04-30
has anyone been successful loaded frostwire in the new 8.04 lts distro.
If so please tell me how you have done it,please keep it simple.
tanks.
krysia.

---

### Post by cchester on 2008-04-30
> **krysia said:**
> has anyone been successful loaded frostwire in the new 8.04 lts distro.
If so please tell me how you have done it,please keep it simple.
tanks.
krysia.

From the command line terminal are you getting this?

Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: cannot access /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: cannot access /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)

That is what I get and I have java installed. Looks like Frostwire can't see where java is installed.

---

### Post by cchester on 2008-04-30
Hi I found this elsewhere in the forums and the instructions work.

"Make sure all of the applications are marked in add/remove, then look for Sun Java, install that then type in a terminal sudo update-alternatives --config java and pick sun java instead of openjdk."

I have tested and verified this and it works and I have Frostwire running in Ubuntu 8.04.

Enjoy.

---

### Post by charlieab1 on 2008-04-30
hi i had the same problem. 
but that was a great help. have test on my desktop and works well 
all the best

---

### Post by foska on 2008-05-01
Thanks chester. It worked for me to.

---

### Post by dRock1286 on 2008-05-02
...and worked for me too!  :-)

---

### Post by cchester on 2008-05-02
> **foska said:**
> Thanks chester. It worked for me to.

Glad to help.

---

### Post by cchester on 2008-05-02
> **dRock1286 said:**
> ...and worked for me too!  :-)


Glad to help.

---

### Post by cchester on 2008-05-02
> **charlieab1 said:**
> hi i had the same problem. 
but that was a great help. have test on my desktop and works well 
all the best


Glad to help.

---

