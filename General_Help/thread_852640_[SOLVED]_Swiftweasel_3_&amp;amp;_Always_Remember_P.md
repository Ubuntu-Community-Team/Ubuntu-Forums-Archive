---
title: "[SOLVED] Swiftweasel 3 &amp;amp; Always Remember Password Hack"
date: 2008-07-07
forum: General Help
---

### Post by DapperMe17 on 2008-07-07
Hello,

I recently updated to Firefox3 & Swiftweasel3, from both versions of #2.

I used the "Always Remember Password" extension in both #2 versions just fine.

Since this extension does not work with FF3, I manually edited the nsLoginManager.js file under /xulrunner 1.9... and the hack works great.

However, Swiftweasel doesn't recognize the above hack. 

Is there a different location for the nxLoginManager.js file in Swiftweasel?

---

### Post by DapperMe17 on 2008-07-08
Any?

---

### Post by DapperMe17 on 2008-07-14
bump

---

### Post by DapperMe17 on 2008-07-30
Still looking for some info...

---

### Post by DapperMe17 on 2008-08-24
Come on people...where is the file nxLoginManager.js file hiding in swiftweasel?

---

### Post by y-lee on 2008-08-24
I use switweasel But i don't use said extension. the file nxLoginManager.js is not on my system anywhere. But linux provides two ways to search for files, these are the **locate** command and the **find** command. The linux man pages are the standard way to get information on using most linux commands. Open a terminal and type **man find **or **man locate**. Note** q** exits the man page. 

I know this information given by the man pages is sometime confusing, so try the command ```
find . -name nxLoginManager.js
``` to search the current folder for the file nxLoginManager.js.

If using locate and or man is confusing for you there are GUI tools to perform searches for you, see [catfish]("http://software.twotoasts.de/index.php?/pages/catfish_summary.html") for one. Catfish should be in the repos so to install it use:

```
sudo apt-get install catfish
```

Btw catfish is not the only tool that does this, but it works well. Look around in add and remove, synaptic and try google for others.

Hope this helps.

---

### Post by DapperMe17 on 2008-08-24
Thanks y-lee!

For Swiftweasel, I was able to locate it under /usr/local/swiftweasel3/components.

The file name is actually nsLoginManager.js

Thanks again for your time & efforts!

---

