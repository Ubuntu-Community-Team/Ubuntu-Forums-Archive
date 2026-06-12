---
title: "[SOLVED] In Terminal: how to display fifth row from inpu file"
date: 2008-03-13
forum: General Help
---

### Post by abcuser on 2008-03-13
Hi,
I would like to display fifth row from input file. Input file looks something like this:
```

aaa xxx
bbb xxx
ccc xxx
ddd xxx
eee xxx
fff xxx
ggg xxx

```
So output should be line at "eee xxx".

I don't know what is the contents of fifth row, I would just like to get data in fifth row from input file.
So far I have written the following:
```

nl input_file | gawk '$1==5 {print $2, $3, $4, $5, $6}'

```
The problem with gawk is that I never know how much columns are in input file. Is there any way to tell gawk to display from second column to end of line?

Thanks,
Abcuser

---

### Post by abcuser on 2008-03-13
Hi,
I have solved the problem.
```

nl input_file | gawk '$1==5' | cut -f 2-

```
Thanks,
Abcuser

---

