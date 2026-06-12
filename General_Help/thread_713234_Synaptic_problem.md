---
title: "Synaptic problem"
date: 2008-03-02
forum: General Help
---

### Post by BossGreen on 2008-03-02
When i try to open synaptic package manager from Applications->system-> synaptic package manager  I get and error message that says this

```
An error occured

The following details are provided:

E: dpkg was interrupted, you must manually run
 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

When I try to run 'dpkg --configure -a'
it says this

```
nicholas@Nicholas:~$ sudo dpkg --configure -a
Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

```

any help?

---

### Post by BossGreen on 2008-03-02
can anyone help me?
I've asked on two forums already.
Is this an unsolvable problem?

---

### Post by nu2ubuntoo on 2008-03-05
I'm having the same problem. 

Can anyone please help us ?????

---

### Post by pointone on 2008-03-05
Have you tried doing what it asks? Visit "http://java.sun.com/javase/downloads/", click "Download" beside where it says "Java SE 6 Documentation", accept the license agreement, and download "jdk-6-doc.zip". Then,

```
sudo chown root:root jdk-6-doc.zip
sudo cp jdk-6-doc.zip /tmp
```

... and try again.

---

