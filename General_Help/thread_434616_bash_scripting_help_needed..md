---
title: "bash scripting help needed."
date: 2007-05-06
forum: General Help
---

### Post by nsleiman on 2007-05-06
Hi,

i am trying to write a bash script that unzip's a zip file what is also a zip file..

means i have a file ziped 5000 times :)

here is my not-working code:

```
#!/bin/sh
echo "Starting process.."

LIMIT=5000

for ((a=LIMIT; i<=1; i--))
do
unzip -P "$i" "$i".zip
done
echo "Done Amigo"

```

what should i do ?

---

### Post by gradedcheese on 2007-05-06
what does 'a' have to do with it (look in your 'for' loop ;))  You can also say:

```

for i in `seq 0 5000`; do

```

---

### Post by nsleiman on 2007-05-06
> **gradedcheese said:**
> what does 'a' have to do with it (look in your 'for' loop ;))  You can also say:

```

for i in `seq 0 5000`; do

```

thanx man, another help please:

i have the sequence of the files like this: 5000-4999-4998...1

not from 0 to 5000.

---

### Post by gradedcheese on 2007-05-06
why does the order matter?  You can start at 1 and end at 5000, it's the same result...

---

