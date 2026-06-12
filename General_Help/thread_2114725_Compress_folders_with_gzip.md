---
title: "Compress folders with gzip"
date: 2013-02-10
forum: General Help
---

### Post by sandyd on 2013-02-10
I am currently looking for a bash script that automatically compresses folders in a directory (one tar.gz for each folder).

For example, if the directory contains
```

sv1 sv2 sv3 sv4
```
the bash script should generate
```

sv1-{date}.tar.gz sv2-{date}.tar.gz sv3-{date}.tar.gz sv4-{date}.tar.gz
```

Any ideas?

---

### Post by SeijiSensei on 2013-02-10
This works, but it archives files as well as directories.  I thought "ls -d *" returns only directories, but that doesn't seem to be the case.  There's a clunky approach using "ls -l | grep ^d | awk '{print $9}'", but maybe someone else knows a better method of getting only directories in the list.

```

#!/bin/bash

# compress all directories in separate folders

TODAY=$(date +%Y%m%d)
# put gzipped archives in this directory; 
# if empty, use current directory
ARCHIVEDIR=

# if directory passed at command prompt, go there
[ "$1" != "" ] && cd $1

for d in $(ls -d *)
do

   if [ "$ARCHIVEDIR" != "" ]
   then
       TARGET="$ARCHIVEDIR/$d-$TODAY.tgz"
    else
       TARGET="$d-$TODAY.tgz"
    fi

    tar -czpf $TARGET $d

done

exit 0

```

---

### Post by papibe on 2013-02-10
Hi sandyd.

Something like this should work:
```
#!/bin/bash

if [ $# != 2 ]; then
        echo "Usage: script SOURCE DESTINATION"
        exit 1
fi

SOURCE="$1"
DESTINATION="$2"

time=$(date +%F)

cd  "$SOURCE"

while IFS= read -r -d '' dir; do

        echo tar cvzf "$DESTINATION/${dir##*/}-$time.tar.gz" "$dir"

done< <(find . -mindepth 1 -maxdepth 1 -type d -print0)
```
Looks for all directories on SOURCE, and compress them separately into DESTINATION.

Note that "as is" is not actually compressing but echoing the command.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by sandyd on 2013-02-20
> **papibe said:**
> Hi sandyd.

Something like this should work:
```
#!/bin/bash

if [ $# != 2 ]; then
        echo "Usage: script SOURCE DESTINATION"
        exit 1
fi

SOURCE="$1"
DESTINATION="$2"

time=$(date +%F)

cd  "$SOURCE"

while IFS= read -r -d '' dir; do

        echo tar cvzf "$DESTINATION/${dir##*/}-$time.tar.gz" "$dir"

done< <(find . -mindepth 1 -maxdepth 1 -type d -print0)
```
Looks for all directories on SOURCE, and compress them separately into DESTINATION.

Note that "as is" is not actually compressing but echoing the command.

Hope it helps. Let us know how it goes.
Regards.

Worked as advertised ;)

I am currently using it to package backups for Amazon Glacier as they have an archive storage format instead of one that allows me to upload bazillions of files :D

---

