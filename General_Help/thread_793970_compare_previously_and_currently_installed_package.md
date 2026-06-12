---
title: "compare previously and currently installed packages using diff?"
date: 2008-05-14
forum: General Help
---

### Post by Novus on 2008-05-14
I got 2 lists of installed packages, one from before the upgrade to 64bit and one of the packages currently installed both generated using dpkg -l now how do I get diff (or anything else) to show me what packages I had installed before the upgrade but not installed now?

---

### Post by bingoUV on 2008-05-14
I assume you have these lists in files (say before.txt, and after.txt). Sort both of them (I don't know if dpkg supplies a sorted list)
```

cat before.txt | sort > beforeSorted.txt
cat after.txt | sort > afterSorted.txt

```

Now, use vimdiff to view differences in a nice colour coded way : 
```

vimdiff beforeSorted.txt afterSorted.txt

```

Or, you could diff them and pour the output in a file and then vim would color code it nicely for you
```

diff beforeSorted.txt afterSorted.txt > packages.dif
vim packages.dif

```

In the dif file generated above, grep for starting > to see only the lines available in the second file that are not in first file. Now you can remove the > to get 
```

cat packages.dif | grep '^>' | cut -d" " -f 2-

```

---

### Post by Novus on 2008-05-14
thanx alot for the help bingoUV.. but bcuz of the messed up output from dpkg your solution didn't solve it for me, thou it helped alot on the way.. but this got realy UGLY!

the output is in this format, this is from the old instalation
```

ii  apport                                     0.108.1                                            automatically generate crash reports for debugging
```

this is from the new
```
ii  apport                                     0.108.1                             automatically generate crash reports for debuggi
```

different ammounts of spaces, easely fixed, but, notice the different length of the discription field! this drowe me crazy for hours but finaly I got it the way I want it :)

```
cat newpackages.list | tr -s ' ' > tr_newpackages.list
cat tr_newpackages.list | cut -d" " -f2 > name_newpackages.list
cat tr_newpackages.list | cut -d" " -f4- > desc_newpackages.list
cat desc_newpackages.list | cut -b-45 > cutdesc_newpackages.list
paste -d ' ' name_newpackages.list tabs > tabname_newpackages.list
paste -d ' ' tabname_newpackages.list cutdesc_newpackages.list | sort > Snewpackages.list
cat packages.list | tr -s ' ' > tr_packages.list
cat tr_packages.list | cut -d" " -f2 > name_packages.list
cat tr_packages.list | cut -d" " -f4- > desc_packages.list
cat desc_packages.list | cut -b-45 > cutdesc_packages.list
paste -d ' ' name_packages.list tabs > tabname_packages.list
paste -d ' ' tabname_packages.list cutdesc_packages.list | sort > Spackages.list
diff Spackages.list Snewpackages.list > packages.diff
cat packages.diff | grep '^<' | cut -d" " -f 2- > missing.list
```

yes, Im sure it can be done much smoother but Im a linux noob an Im so tired of this now I don't care how it looks.. I just wanted results :)

"tabs" is a textfile with 4 tabs on each line that goes on for thousends of lines, just to make the final file readable.

---

