---
title: "Help with BASH script to compare two files"
date: 2007-12-05
forum: General Help
---

### Post by jasont.t on 2007-12-05
Hi,
 I want to create a simple BASH script to test the difference between two files and if they differ export the lines that are different to another text file; then the plan is to send the contents to an e-mail account. If there is no difference then no action is performed.

I’m not sure how to achieve this. I have been able to use the ‘diff’ command to successfully test but not sure where to go from here.  E.G “diff –I –b –B –q file1.txt file2.txt”

Can someone please provide some suggestion?

Thanks

---

### Post by jasont.t on 2007-12-05
I've worked out the answer, here it is;

```
diff -i -b -B -q file1.txt file2.txt
if [ ! $? -eq 0 ]; then
echo "**** File has changed*****" 
diff -i -b -B file1.txt file2.txt >> /tmp/diff.txt
else
echo "same"
```

---

### Post by kevdog on 2007-12-05
Does this work on binary files?

---

### Post by zadig on 2007-12-05
You may also want to use CVS for a better control.

---

### Post by jasont.t on 2007-12-06
> **kevdog said:**
> Does this work on binary files?

I don't think so. I think you might be better off using the "cmp" command.

---

