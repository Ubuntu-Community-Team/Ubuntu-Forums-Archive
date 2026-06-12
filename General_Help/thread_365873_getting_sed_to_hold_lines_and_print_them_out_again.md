---
title: "getting sed to hold lines and print them out again"
date: 2007-02-20
forum: General Help
---

### Post by inonzi_prowler on 2007-02-20
hello all.

so i have this text file, a section of which looks like this:

> 
KH6:1:1
                                4691814
                                4691814
                                4691814
                                4691814
                                4691814
KT3:1:1
                                4691815
                                4691815
                                4691815
                                4691816
                                4691816
                                4691816


i would very very much like for it to look like this:

> 
KH6:1:1                               
KH6:1:1                        4691814
KH6:1:1                        4691814
KH6:1:1                        4691814
KH6:1:1                        4691814
KH6:1:1                        4691814
KT3:1:1                               
KT3:1:1                        4691815
KT3:1:1                        4691815
KT3:1:1                        4691815
KT3:1:1                        4691816
KT3:1:1                        4691816
KT3:1:1                        4691816


reading around i guess i need to get it to hold the line in the buffer when it finds a ":" (the common bit of text in the left column) and print at the start of each line until it finds another ":".

is that right guys? i am very new to sed and am struggling.

many thanks in advance for any help.

---

### Post by jasutton on 2007-02-20
Here's a bash script that will do what I think  you want it to do:

```
#!/bin/bash

lines=`cat test.txt`

for line in $lines; do
  echo $line | grep ":" > /dev/null
  if [ $? -eq 0 ]; then
    curPrefix="$line"
    echo "$line"
  else
    echo "$curPrefix $line"
  fi
done
```

test.txt is, of course, your input data.  You can use stdout redirection to save the result to a file.  :)

---

### Post by inonzi_prowler on 2007-02-20
> **jasutton said:**
> Here's a bash script that will do what I think  you want it to do:

```
#!/bin/bash

lines=`cat test.txt`

for line in $lines; do
  echo $line | grep ":" > /dev/null
  if [ $? -eq 0 ]; then
    curPrefix="$line"
    echo "$line"
  else
    echo "$curPrefix $line"
  fi
done
```

test.txt is, of course, your input data.  You can use stdout redirection to save the result to a file.  :)


it looks like it worked. however, i do not fully understand how you did it. thanks very much and i will look at what you did some more and try to understand.

souce file is 1million plus lines though so i guess this will take a while?

---

