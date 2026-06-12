---
title: "vmware error"
date: 2007-03-27
forum: General Help
---

### Post by x.1.alvin on 2007-03-27
Hello, i have this error when installing vmware on dapper:

Unable to get the access rights of source file "./vmware-vix/bin".

Any suggestions! Thanks!

---

### Post by useResa on 2007-03-27
> **x.1.alvin said:**
> Hello, i have this error when installing vmware on dapper:
Unable to get the access rights of source file "./vmware-vix/bin".
Any suggestions! Thanks!

There is (quite a lengthy ;)) thread on this matter, which you can find [here](http://ubuntuforums.org/showthread.php?t=183209)

In post [#530](http://ubuntuforums.org/showpost.php?p=1499222&postcount=530) the same issue as described by you is indicated.
It seems that the error is caused by the fact that the **bin** subdirectory was not created by the install script.

Suggestion to solve this is to create it yourself.
Hope this helps you further.

---

