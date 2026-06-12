---
title: "myphpmoney removal issue"
date: 2005-06-21
forum: General Help
---

### Post by unruly on 2005-06-21
I'm actually having trouble with removing the package myphpmoney.

I ssh into my Ubuntu computer, which is running primarily as a server, and run the command:```
$ sudo apt-get remove --purge myphpmoney
```All seems to go well until it begins removing it, and running it's removal scripts. This is what I get:```
Removing myphpmoney  ...
 * Forcing reload of web server    (Apache 2)...         [ok]
``` and then, it just sits there until I force kill it with ctrl+c.

I know it has to do with it's removal scripts, but I can't seem to find anything wrong with them.  However, I'm not familar with the syntax to them, so, I am very possibly wrong.  Here is the relevant ps alx | grep <pid>:```
4     0 25881 25875  17   0      0     0 exit   Z+   pts/0      0:00 [myphpmoney.prer] <defunct>
```*sorry if that breaks the layout*.

I don't know what to do, I've asked quite a few knowledgable sources, and I can't seem to get anything helpful out of them.  Also, google and the ubuntu bug list don't give anything helpful.

Help!!

---

### Post by unruly on 2005-06-21
sigh.  well, I 'figured it out'.

You have to go into /var/lib/dpkg/info/myphpmoney.prerm and comment out EVERYTHING (precede each line with a #) and then re-run the removal.

What a pain.

---

### Post by Abilnet on 2005-07-10
I was as well losing my hair with this issue, but thanks for your tip - I got rid of the problematic package.

Thanks again!   :grin:

---

### Post by osca1 on 2006-04-14
Save some time - just replace /var/lib/dpkg/info/myphpmoney.prerm with this script

#!/bin/bash
exit 0;

.. then - sudo chmod +x /var/lib/dpkg/info/myphpmoney.prerm

Cheers :D

---

### Post by Marcos.Rufino on 2006-06-15
Thank you guys! 
I'll never install this myphpmoney again!
I can't believe how it is in the repos anyway.

---

