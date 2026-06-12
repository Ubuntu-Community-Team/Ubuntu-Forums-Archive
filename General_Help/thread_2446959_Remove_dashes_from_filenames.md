---
title: "Remove dashes from filenames"
date: 2020-07-10
forum: General Help
---

### Post by raleigh3 on 2020-07-10
This removes spaces in filenames.

How can I also remove dashes - ?

```
rename "s/ //g" *
```

---

### Post by ActionParsnip on 2020-07-10
Make a test file with touch and you can play

Possibly
```

touch ~/dashtest.txt
rename "s/\-//g" ~/dashtest.txt

```

I'm not at my system so can't test personally but it's a dummy file (a test) so no harm is done. If it's OK then move to prime time (be sure your data is backed up too just in case)

---

### Post by sisco311 on 2020-07-10
The rename command used by Ubuntu is based on perl, so check out: [https://perldoc.perl.org/perlre.html](https://perldoc.perl.org/perlre.html)

```
rename -n 's/[ -]//g' ./*.txt
```
should do the trick. 

The -n or -nono flag means *No action*. Check out the man page for details.

---

