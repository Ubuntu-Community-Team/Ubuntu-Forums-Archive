---
title: "having trouble with mysqldump and 7zip"
date: 2014-12-08
forum: General Help
---

### Post by lance bermudez on 2014-12-08
Mysqldump –u root –ppassword databasename | 7z a -si -t7z outputfile.sql.7z -mx9

the above work but I want to use deflate64 with zip

mysqldump -u root –ppassword databasename | 7z a -si -tzip -mm=deflate databasename.zip
7-Zip 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,1 CPU)
Creating archive databasename.zip

Compressing  [Content]    0%

System error:
E_NOINTERFACE                
mysqldump: Got errno 32 on write

---

### Post by kpatz on 2014-12-08
From the 7z documentation:> Note: The current version of 7-Zip support reading of archives from stdin only for xz, lzma, tar, gzip and bzip2 archives.

If you need to use deflate64, write your sqldump to a temp file and then zip that.

```

mysqldump -u root –ppassword databasename >/tmp/databasename.sql
7z a -tzip -mm=deflate64 databasename.zip /tmp/databasename.sql
rm /tmp/databasename.sql

```

---

