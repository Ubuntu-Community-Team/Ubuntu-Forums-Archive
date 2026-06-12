---
title: "Remove vowels of a text file"
date: 2006-07-17
forum: General Help
---

### Post by rob3000 on 2006-07-17
hi,

I want to create a little shell script for exercise which removes all vowels of a textfile.
Are there examples available to realize that?

robi

---

### Post by jmacak on 2006-07-17
Hi

You can easily do this using sed.  If the original file is junk.txt, you can create junk2.txt that doesn't have vowels like this:

cat junk.txt | sed 's/[aeiouy]//g' > junk2.txt

This just cats (prints) the file, pipes into sed, which globally substitutes the characters in the brackets with nothing and the sends the output to junk2.txt.

If junk2.txt exists, it gets overwritten.  

(a second line of the script can replace the original file with the new:

mv junk2.txt junk.txt

)

HTH

cheers

joe in seattle

---

### Post by der_joachim on 2006-07-19
An alternative for sed is tr (only an oldtimer such as myself can understand such a sentence :mrgreen:). 

Try this snippet of code:
```

tr -d [AEIOUaeiou] < foo.txt > bar.txt

```

Happy scripting! 8)

---

### Post by joe343 on 2006-07-19
Hi !

How would you do the same thing but with file names ?

ex: junkfile.txt -> jnkfl.txt

How about processing all the files in a folder/sub-folder ?
Thanks !

---

