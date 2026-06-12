---
title: "Ubuntu Mirror Setup"
date: 2007-09-26
forum: General Help
---

### Post by hauntedunix on 2007-09-26
Hey guys,

I'm making an Ubuntu mirror for my company at the moment. The script I'm using is:

```
#!/bin/bash

RSYNC="/usr/bin/rsync"
OPTS="--recursive -P --links --perms --times -D --delete --timeout=300 -v  --bwlimit=50"
SRC="whatever"
DST="/repo/ubuntu"

# echo "Started update at" `date` >> $0.log 2>&1
# logger -t rsync "re-rsyncing the gentoo-portage tree"
${RSYNC} ${OPTS} ${SRC} ${DST} 
# >> $0.log 2>&1

#echo "End: "`date` >> $0.log 2>&1

```


Now, this *is* working, but it's pulling down all of the .tar.gz stuff as well. Is there any way that I can grab just the debs? Also, is there any sensible way to limit the architectures and versions I pull?

Thanks in advance, and apologies if I put this in the wrong forum section ;)

Alex.

---

### Post by straps on 2007-09-26
```
OPTS="$OPTS --exclude=*.tag.gz"
```

---

