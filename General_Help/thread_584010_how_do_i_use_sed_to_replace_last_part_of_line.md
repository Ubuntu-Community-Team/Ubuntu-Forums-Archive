---
title: "how do i use sed to replace last part of line"
date: 2007-10-20
forum: General Help
---

### Post by lavinog on 2007-10-20
I have a file that needs to be modified by a script.
in the file there is a line that has

```
someadjustmentfactor=0.27000
```

I am trying to find a way to use sed to change the factor
Right now i am using:
```
sed 's/someadjustmentfactor=0.27000/someadjustmentfactor=0.29500/' < file >file 
```

I can't seem to figure out how to get sed to replace everything after the = with the new number

I guess I could use cut but i feel that there is a way to do it solely with sed.

---

### Post by bapoumba on 2008-12-20
Moved to general Help as requested by OP, and Buu..uuump !

---

### Post by dagnabit dang doohickey on 2008-12-20
```
sed 's/^\(someadjustmentfactor=\)[0-9/.]*/\10.29500/'
```

---

### Post by andrew.46 on 2008-12-20
Hi,

A slightly different approach:

```
echo 'someadjustmentfactor=0.27000' |\
sed 's/.\{7\}$/0.29500/'
```

Just copy these lines and paste into your terminal to test the result. I love sed!!! If you are a little new to sed the only odd syntax would perhaps be:

```
's/.\{7\}$/
```

 This simply matches the last 7 characters in the line and allows the subsequent substitution with the number of your choice.
  Andrew

---

