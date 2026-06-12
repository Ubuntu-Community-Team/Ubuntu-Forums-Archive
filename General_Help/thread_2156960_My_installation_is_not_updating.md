---
title: "My installation is not updating"
date: 2013-06-23
forum: General Help
---

### Post by Extol11 on 2013-06-23
So I haven't had internet at home for a few weeks now and when I try to update wherever I take my laptop where ever there's internet it does not let me. I tried to do it manually and this is the message that it is giving me. ```
W: GPG error: http://pr.archive.ubuntu.com raring Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/raring/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/pr.archive.ubuntu.com_ubuntu_dists_raring_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

```
Can anyone tell me how to fix this problem?

---

### Post by oldos2er on 2013-06-23
[http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

---

### Post by Extol11 on 2013-06-25
Non worked. =/ I'll just reinstall I guess.

---

### Post by oldos2er on 2013-06-25
No need to reinstall. Can you post the output from the commands?

---

### Post by Extol11 on 2013-06-26
I reinstalled. It just said that the command aptitude could not be found... or something like that.

---

### Post by oldos2er on 2013-06-26
You should have tried Method #1. aptitude is no longer installed by default, but it's there in the repositories if you want to install it. If that error pops up again you'll know what to do.

---

