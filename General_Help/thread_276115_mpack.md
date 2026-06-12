---
title: "mpack"
date: 2006-10-12
forum: General Help
---

### Post by jrogers360 on 2006-10-12
I have dapper installed, and did a "sudo apt-get install mpack", which is a utility that I commonly use to send a file via email from the command line (or from a cronned script).

```
jrogers@rafiki:~/bin$ mpack -s "Here is the file" testfile jrogers@rafiki.com
execv: No such file or directory
jrogers@rafiki:~/bin$ ls -l testfile
-rwxr-xr-x 1 jrogers jrogers 2736 2006-09-12 09:40 testfile

```

Any ideas what "execv: No such file or directory" is about?  I'm not sure which file the program is looking for.  I've installed mpack many times on previous debian installations w/out any problem.  I'm not sure where to start looking.

Thanks for any direction you can offer,
Josh

---

### Post by jrogers360 on 2006-10-20
nudge.

Any ideas?

---

### Post by jrogers360 on 2007-03-13
Just did a format and clean install of dapper, and this problem persists.

---

### Post by jrogers360 on 2007-06-08
I figured this out after doing an strace.  I'm not sure how to submit a bug to the package maintainer, but setting TMPDIR fixed the problem.  According to the man page, TMPDIR's default is /var/tmp, however that appears to not be the case.

```
export TMPDIR=/var/tmp
```

---

### Post by timshadel on 2008-01-26
This error message went away for me once I uninstalled mpack, installed ssmtp and configured it to send basic email, and then reinstalled mpack.  YMMV.

---

### Post by jrogers360 on 2008-01-27
I also haven't seen this problem since upgrading to the feisty

.

---

