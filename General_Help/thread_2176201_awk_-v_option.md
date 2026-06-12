---
title: "awk -v option"
date: 2013-09-23
forum: General Help
---

### Post by matthew13 on 2013-09-23
I appear to have a problem using the -v option in awk.

Here is a simple program designed to find the string corresponding to $4 in a file 'symstats.txt' and print to an output file, 'enarray.txt'.

The pattern that needs to be matched comes from the list 'STRUCTLIST' which is printed by a separate awk command as the first part of the program.

For this reason I've attempted to use awk with -v. 

When this is run as an executable, the file enarray.txt is created, but the expected content is not written to it, so it is an empty file.

The first part of the script works as I get the output written to STRUCTLIST when run in terminal window.

Could the problem be the shell I am using? 


This bash script is run on Mac OS X 10.7.4.

```


#!/bin/bash

STRUCTLIST=`awk '{print $6}' fit.out`


for i in $STRUCTLIST; do
  printf $i
  awk -v search=$i '{ 
  if ($4 ~ /search/)
  print $5;
  }' symstats.txt > enarray.txt
done


```

---

### Post by steeldriver on 2013-09-23
With the / ... / regex markers, it interprets /search/ as a literal string, I think - to do a regex match against a string *variable* it's just

```
$4 ~ search
```

Also, you don't need the 'if' since the regex match is a  boolean test on its own, just i.e.

```

awk -v search=$i '$4 ~ search {print $5;}' symstats.txt > enarray.txt

```

should do it

---

### Post by matthew13 on 2013-09-23
Thanks, problem solved :P

---

