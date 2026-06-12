---
title: "BASH How to cut some text out of other text (see inside)"
date: 2007-10-22
forum: General Help
---

### Post by Walter_Crankite on 2007-10-22
Hello, 


If for instance you got outputs (retrieved from awk '{print $3}') like this:

ABX_thing1
ABX_thing2
...


How do you cut off ABX_ and just display the other text.
What I mean is like the opposite of "more", leaving similar things away ?


thx
Walter

---

### Post by squaregoldfish on 2007-10-22
Are your text lines always going to start with ABX_?

If so, you can pipe the output of the previous command through sed. For example:

awk '{print $3}' |sed -e s/^ABX_//

In this case, sed will run through each line of output, and if it finds ABX_ at the start of the line (that's what the ^ means), it will remove it.

If you want to remove anything before the first underbar, you can use the following:

awk '{print $3}' |sed -e s/^[^_]*_//


Read up on sed and regular expressions. If you intend to do lots of shell scripting, you will learn to love them both.

Steve.

---

### Post by kast on 2007-10-22
Well if its going to be a fixed number of Text/# then using the **cut** command would also work.

**cut -c1-4** # would cut the first four characters

squaregoldfish is right with sed, it is more robust and maybe a better fit depending on what your looking to do.

---

### Post by ayoli on 2007-10-22
or pipe (with |) the awk output in this:
```
cut -d _ -f 2
```

---

### Post by Walter_Crankite on 2007-10-24
Cutting off the first four characters is the most easy way.


~$ df -h | grep /mnt/BU_Home | awk '{print $6}'

/mnt/BU_Home

~$ df -h | grep /mnt/BU_Home | awk '{print $6}' | cut -c6-20

BU_Home


But it has to be cut -c1-4 normally??
What went wrong?


Thx a lot for the info.
cheers

Walter

---

