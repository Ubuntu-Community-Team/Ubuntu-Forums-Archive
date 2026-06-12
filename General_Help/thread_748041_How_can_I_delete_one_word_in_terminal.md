---
title: "How can I delete one word in terminal?"
date: 2008-04-07
forum: General Help
---

### Post by kjman83 on 2008-04-07
# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

blacklist bcm43xx
blacklist bcm43xx


exit

blacklist bcm43xx


----------------------------------
it's my blacklist file.. I don't know why I wrote exit when I worte exit..
I need to remove the word exit and two blacklist bcm43xx
I know How I can add the word by 'echo blacklist bcm43xx | sudo tee -a /etc/modprobe.d/blacklist

but I don't know How I can remove the words.. please help me.

---

### Post by kesman on 2008-04-07
Open it with some text editor, such as nano like this:
```

sudo nano /path/to/file

```
and edit as you like. Then exit with ctrl+X and answer YES to save the edited file.

---

### Post by loell on 2008-04-07
alt + backspace?

edit-- scratch this ;)

---

### Post by kevdog on 2008-04-07
So do you want to delete duplicates in the file and save only one copy of the duplicates, or do you want to just delete a line that contains an expression.

To remove duplicates (saving the first copy) if they are on consecutive lines:
cat <filename> | sed '$!N; /^\(.*\)\n\1$/!P; D'

To simply remove a certain line that contains a certain expression:
cat <filename> | sed -i "/<regular expression>/d" <filename>

An example is here:
cat local.txt | sed -i "/bcm43xx/d" local.txt

---

