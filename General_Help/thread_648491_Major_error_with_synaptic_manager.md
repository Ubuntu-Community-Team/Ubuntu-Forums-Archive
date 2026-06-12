---
title: "Major error with synaptic manager?"
date: 2007-12-23
forum: General Help
---

### Post by shucks on 2007-12-23
_**I know this is alot but please, please read all of it before trying to help me. I listed all that I've done, and what I've tried to do about it.**_

It all started with trying to install sun-java through synaptic manager through the advice of someone on the #ubuntu irc chat. When I tried to install it was going fine, and then an error came up, I forgot what exactly, I think it has to do with doing end process on system moniter for synaptic manager because it said it was already running when I tried to start it again. but ever since then I get 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

when I try to run synaptic manager. Of course my first step was to run sudo dpkg --configure -a on terminal. When I tried that however, I got:

sam@sam-laptop:~$ sudo dpkg --configure -a
[sudo] password for sam:
Setting up sun-java5-doc (1.5.0-13-0ubuntu1) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/j2se/1.5.0/download.html](http://java.sun.com/j2se/1.5.0/download.html)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]

This problem seems to effect almost everything I try on ubuntu, like uninstalling/reinstalling synaptic manager. I just don't know what to do anymore.

:(

---

### Post by shucks on 2007-12-23
ok solved it, just need to download the documents, close thread plz

---

