---
title: "Substituting 2 number in a list"
date: 2015-04-28
forum: General Help
---

### Post by CkDGTAT on 2015-04-28
Hi,

I have a file composed of 

```
(n1,n2,n3,n4)
(n5,n6,n7,n8)
(n9,n10,n11,n12)
...
```

And I want to have

```
(n2,n1,n4,n3)
(n6,n5,n8,n7)
(n10,n9,n12,n11)
...
```

Thank you

---

### Post by Lars Noodén on 2015-04-28
That can be done easily with [awk](http://manpages.ubuntu.com/manpages/trusty/en/man1/awk.1posix.html)

```

awk 'BEGIN{ FS="[(),]"; OFS=","} {tt=$2; $2=$3; $3=tt; tt=$4;$4=$5;$5=tt; sub(/^,/, "(" ); sub(/,$/,")"); print }' *yourfile*

```

The BEGIN clause sets the field separator to a pattern of a comma or parentheses.  The output field separator is a plain comma.

Then the main script swaps the second and third fields using the variable tt as a temporary holder.  Same for the fourth and fifth fields.  Then before printing, any leading or trailing commas are replaced with the appropriate parenthesis.

---

### Post by Topsiho on 2015-04-28
Hi,

First, I think this is a question for Development and Programming.

Second, what programming language do you use?

In Python you could open this file for reading, read each line, (until there are no more lines), and add it's contents in a list, let's call it:  lijst.
After that you could code: lijst  = (lijst[1], lijst[0], lijst[3], lijst[2])

and add this line to your new file. The swapping of numbers that you want is done for each line in the file.

Topsiho

---

### Post by Holger_Gehrke on 2015-04-28
Why a long 'awk' when a short substitution in 'sed' will do ?
```

sed 's/^(\([^,]*\),\([^,]*\),\([^,]*\),\([^)]*\)/(\2,\1,\4,\3/' listfilename

```
or in awk but without the variable:
```

awk 'BEGIN {FS="[(),]"} {print "(" $3 "," $2 "," $5 "," $4 ")"}' liste

```

And I don't think that anything that can be done with one command belongs in Development and Programming ...

---

### Post by Topsiho on 2015-04-28
> **Holger_Gehrke said:**
>  And I don't think that anything that can be done with one command belongs in Development and Programming ...

You are right. I did not think of using sed or awk (unknown territory for me, there is still a lot to learn), only of how to solve this with Python, which is a programming language.

Topsiho.

---

