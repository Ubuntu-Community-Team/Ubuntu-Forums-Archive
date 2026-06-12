---
title: "vsftpd.log and utf-8 multibyte chars"
date: 2007-01-26
forum: General Help
---

### Post by sclaes on 2007-01-26
Why are any utf-8 multibyte chars replaced with question marks in vsftpd.log? (some directory names
and file names have utf-8 multibyte chars)

I tried to find a word containing utf-8 multibyte chars in /var/log and it appears in /var/log/auth.log when I issue
the following command:
 sudo grep -Ril &#1082;&#1088;&#1072;&#1089;&#1085;&#1072;&#1103; /var/log

Any ideas?

---

### Post by sclaes on 2007-01-27
> **sclaes said:**
> Why are any utf-8 multibyte chars replaced with question marks in vsftpd.log? (some directory names
and file names have utf-8 multibyte chars)

I tried to find a word containing utf-8 multibyte chars in /var/log and it appears in /var/log/auth.log when I issue
the following command:
 sudo grep -Ril &#1082;&#1088;&#1072;&#1089;&#1085;&#1072;&#1103; /var/log

Any ideas?

It seems that utf-8 multibyte chars in vsftpd.log are considered as a security risk... IMHO very bizarre: log files are only text files, so how could this possibly be a security issue?

---

