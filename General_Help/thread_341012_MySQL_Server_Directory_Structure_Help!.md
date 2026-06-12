---
title: "MySQL Server Directory Structure? Help!"
date: 2007-01-18
forum: General Help
---

### Post by pak33m on 2007-01-18
Hello,

I am just into the intro to the MySQL Press MySQL Tutorial book & installed MySQL Server (& deps) via apt-get, but I don't find the directory structure that they refer to in the book under the datadir, i.e the bin, data, scripts, etc. folders.

I install MySQL on Windows, Red Hat & Suse at work & have always worked in the folders that seem missing from my install.

The only difference that I see is that the book refers to 4.0 & 4.1 & this is what I install at work even, but my install via apt-get was 5.0.

Could anybody at least share some knowledge with me?

---

### Post by phossal on 2007-01-18
/var/lib/mysql
 /etc/mysql

---

### Post by pak33m on 2007-01-18
Thank you phossal for your input.

I found out from my company DBA that if you install from a distro the directory structure is scattered all over the file system.  Obviously,if you compile from source you can install to where ever you want.

Oh, well.

---

### Post by phossal on 2007-01-18
Yeah, but, even scattered, you can find those directories and work with your files. Or you can download MySQL directly and install it yourself.

---

