---
title: "understanding awk command"
date: 2007-11-15
forum: General Help
---

### Post by carverj on 2007-11-15
Hi all,
         with the command $grep ^”r ” trace.tr | $awk ‘$5~/tcp/ || $5~/ack/ {RB += $6} END {print RB}‘
I understand what grep is doing. I don't understand what the awk command is doing here.
Could someone explain briefly?
Thanks in advance

---

### Post by carverj on 2007-11-15
> $grep ^”r ” trace.tr | $awk ‘$5~/tcp/ || $5~/ack/ {RB += $6} END {print RB}‘

a regular expression to extract all the tcp or ack values(size), place them in a variable and add the next columns values to it then print sum perhaps!!?

---

### Post by nick_h on 2007-11-16
Yes.  Type:
```
man awk
```
for details.

The awk language consists of patterns and actions.  Each line in a file is split into fields and then these fields can be matched with patterns and then actions executed.

The first pattern is **$5~/tcp/ || $5~/ack/** which is true when field 5 matches the regular exprssion /tcp/ or /ack/ (contains tcp or ack).  In this case the action **{RB += $6}** is executed which adds the contents of field 6 to the variable RB. (RB is initialised to 0 when first accessed).

The second pattern is **END** which matches the end of the file.  The corresponding action simply prints the value of RB.

---

