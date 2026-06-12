---
title: "Detect all file changes, new files, deleted files caused by software install"
date: 2014-09-25
forum: General Help
---

### Post by Gottier on 2014-09-25
I've used Git quite a bit, so I'm wondering if there is something similar that would allow me to view the difference between my entire filesystem before then after a software installation. I suppose Git could be used, although it would be terribly slow, and the size of the .git directory would be as big as the entire filesystem, right? That doesn't sound like a good decision.

So what does a system administrator do when they want to see such a diff? I did see that there was a program called auditd, but it looked like it was only showing files changed, not the actual diff. It also looked like auditd would only log info for files that were designated for watching.

---

### Post by TheFu on 2014-09-25
Backups. Versioned backups.

Comparing backups is part of what a good backup tool does.

There is always the **find** command using the atime/mtime/ctime options, but for a comparison, the prior file will be necessary, right?  Backups.

Seeing the actual differences for binary files isn't really useful. It is only useful for scripts and text data which is a tiny amount on most systems.  

[http://ossec-docs.readthedocs.org/en/latest/manual/syscheck/](http://ossec-docs.readthedocs.org/en/latest/manual/syscheck/) is one option for monitoring systems. I've never used it.
 [https://www.owasp.org/index.php/OWASP_File_Hash_Repository](https://www.owasp.org/index.php/OWASP_File_Hash_Repository) is another.

There used to be a tool that made a DB of md5sums for all files, then would would maintain that file daily - showing suspect changes if asked.

**logwatch** is what I use these days. It monitors log files and reports on any newly installed stuff.  A quick 'find' command.


But if all you want to know is which files are modified/installed just look at the package manifest. You can use dpkg to ask which files are part of any valid package.  Hardly worth scanning 8+G of files when only 10 files are actually touched.

---

### Post by ian-weisser on 2014-09-25
I think TheFu is right.
dpkg -L <packagename> will tell you what the change is without scanning the entire system.
That's one reason to use packages.

---

### Post by Gottier on 2014-09-25
Thanks for the info. I've always wondered how to do this, so I'm going to check out your suggestions.

---

