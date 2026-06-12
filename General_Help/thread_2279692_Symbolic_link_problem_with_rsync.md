---
title: "Symbolic link problem with rsync"
date: 2015-05-25
forum: General Help
---

### Post by zkab on 2015-05-25
I have a crontab task that rsync /etc to a backup dir on a backup server.
It works OK but there is a problem with symlinks.
I don't want to rsync them and have the following command:

sudo rsync -rptgoDv --delete /etc /home/jurka/my_data/BackUp/Div_FARBAUTE/ >> /home/jurka/rsync_etc.log 2>&1

rsyn_etc.log gives - which is good:

skipping non-regular file "etc/blkid.tab"
skipping non-regular file "etc/resolv.conf"
skipping non-regular file "etc/vtrgb"

But when I list the target directory I get:

lrwxrwxrwx  1 jurka            jurka      15 May  1 12:19 blkid.tab -> /dev/.blkid.tab
lrwxrwxrwx  1 jurka            jurka      29 May  1 12:19 resolv.conf -> ../run/resolvconf/resolv.conf
lrwxrwxrwx  1 jurka            jurka      23 May  1 12:19 vtrgb -> /etc/alternatives/vtrgb

It seems that they are copied anyhow ...
I have Ubuntu 14.04.2 LTS on both source & target server.
How do I avoid rsync these symbolic links to the target server ?

---

### Post by hailholyghost on 2015-05-25
If I understand your question correctly, perhaps a perl script to rsync only directories

```

#!/usr/bin/env perl

use strict; use warnings;

opendir("/your/directory/",DIR) or die "Can't read /your/directory/: $!";
while (my $item = readdir(DIR)) {
   unless ((-d $item) && !(-l $item)) {
      system("rsync -avzuP $item ip.address@:/some/dir/");
   }
}
closedir DIR;

```

Code obviously not exact for you.  Would this help you?

-DEC

---

### Post by zkab on 2015-05-25
Thanks - but I want to rsync subdirectories, files but not symbolic links ...

---

