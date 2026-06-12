---
title: "Help with shell scripting"
date: 2008-06-10
forum: General Help
---

### Post by aaunix on 2008-06-10
Hi, need some help with shell scripting
I have a file file1.txt which has following content ( number of lines may change )
/web/sites/v3.0/abc.txt
/web/sites/v4.1.1/abc.txt
/web/sites/def.txt
/web/sites/mnp.txt
/web/sites/upgrade.txt

I need to create a shell script , which will read each line of  file1.txt and if a line has a file with .txt extension and if that file exists in the system then it will print information like
abc.txt file exists in directory /web/sites/v3.0/
if it doesn’t then it will print
abc.txt file doesn’t exists in directory /web/sites/v3.0/

Any help/suggestion is greatly appreciated.
thanks &  regards

---

### Post by mikelygee on 2008-06-10
Something like this may get you started:

#! /bin/sh

for f in $(grep \.txt$ files.txt); do
  if [ -e "$f" ]; then
    echo "$f exists"
  else
    echo "$f MISSING"
  fi
done

---

### Post by nunki on 2008-06-10
Give this a shot

```

#!/bin/sh

if [ $# -ne 1 ]; then
        echo "Usage: `basename $0` <file to read>"
        exit 1
fi
if test ! -f $1;  then
        echo "$1 doesnt exist"
        exit 1
fi
for i in $(cat $1); do
        if echo $i | egrep -i '.+\.txt$' >/dev/null 2>&1 ; then
                if test -f $i; then
                        echo "`basename $i` exists in directory `dirname $i`"
                else
                        echo "`basename $i` doesnt in directory `dirname $i`"
                fi
        fi
done

```

Didnt have time to test it.

---

### Post by aaunix on 2008-06-10
I tested it - AND IT ROCKS :-)
Your help/solution is truly appreciated

---

### Post by aaunix on 2008-06-10
> **mikelygee said:**
> Something like this may get you started:

#! /bin/sh

for f in $(grep \.txt$ files.txt); do
  if [ -e "$f" ]; then
    echo "$f exists"
  else
    echo "$f MISSING"
  fi
done
mikelygee
It not only got me started but put me at the finish line too &#61514;
Solution is to Very helpful. Thanks

---

