---
title: "complexed rename folders?"
date: 2013-12-09
forum: General Help
---

### Post by sohlinux on 2013-12-09
Hello, I have a folder with a 100s of sub-folders so I need to automate this if possible..

example...
brad and sarah in france 00:15:56
brad and sarah at home 00:21:04
pop and gill in the USA 00:56:09
pop and gill at home 00:08:12

I want to end up with the following...

brad and sarah in france 15
brad and sarah at home 21
pop and gill in the USA 56
pop and gill at home 08

so basically the first 2 numbers and the :colon should be removed and the :colon and the last 2 numbers should be removed recursively.

and if possible I would like to keep the first 2 numbers if they are other than 00 , eg 01:25:45 but all colons must be removed or replaced with a dash - so if there were a number starting 01 and the middle numbers were 25 I would end up with 01-25

how can this be done from the command line?

thanks

---

### Post by Lars Noodén on 2013-12-09
You can do this kind of thing with rename:

```
rename -n 's/\d\d:(\d\d):\d\d$/$1/' *
```

The -n stops it from actually making any changes.  Remove it to really rename the files.
However that only works with one folder at a time and you would likely have to combine it with [find](http://manpages.ubuntu.com/manpages/saucy/en/man1/find.1posix.html) to get all the subdirectories.

```

find . -type f -exec rename -n 's/\d\d:(\d\d):\d\d$/$1/' "{}" \;

```

Do make a backup with tar first before renaming, just in case.

---

### Post by sohlinux on 2013-12-09
thanks but it didnt appear to do anything at all, neither did it give any error message, I did remove the -n

I cd in to the folder with the sub folders first then - ```
 find . -type f -exec rename 's/\d\d:(\d\d):\d\d$/$1/' "{}" \;

```


> **Lars Noodén said:**
> You can do this kind of thing with rename:

```
rename -n 's/\d\d:(\d\d):\d\d$/$1/' *
```

The -n stops it from actually making any changes.  Remove it to really rename the files.
However that only works with one folder at a time and you would likely have to combine it with [find](http://manpages.ubuntu.com/manpages/saucy/en/man1/find.1posix.html) to get all the subdirectories.

```

find . -type f -exec rename -n 's/\d\d:(\d\d):\d\d$/$1/' "{}" \;

```

Do make a backup with tar first before renaming, just in case.

---

### Post by Lars Noodén on 2013-12-09
Try it with the -n until you get the output you want.  rename is a perl script so these are perl regular expressions (known outside of perl as PCRE).  So anything you can write as a perl regular expression will work.

---

### Post by Lars Noodén on 2013-12-09
"if possible I would like to keep the first 2 numbers if they are other than 00 , eg 01:25:45 but all colons must be removed or replaced with a dash - so if there were a number starting 01 and the middle numbers were 25 I would end up with 01-25"

I didn't see that the first time around.  That can be done by adding a second search and replace:

```

rename -n 's/00:(\d\d):\d\d$/$1/; s/(\d\d):(\d\d):\d\d$/$1-$2/' ./*

```

---

### Post by sohlinux on 2013-12-09
thanks but I must be missing something very basic here, non of these commands do anything at all?

---

### Post by Lars Noodén on 2013-12-09
I've made four files using the sample names you gave.  Here's what I get with ls and rename:

```

$ ls -1
brad and sarah at home 01:21:04
brad and sarah in france 00:15:56
pop and gill at home 00:08:12
pop and gill in the USA 00:56:09

$ rename -n 's/00:(\d\d):\d\d$/$1/; s/(\d\d):(\d\d):\d\d$/$1-$2/' ./*
./brad and sarah at home 01:21:04 renamed as ./brad and sarah at home 01-21
./brad and sarah in france 00:15:56 renamed as ./brad and sarah in france 15
./pop and gill at home 00:08:12 renamed as ./pop and gill at home 08
./pop and gill in the USA 00:56:09 renamed as ./pop and gill in the USA 56

```

I'm not sure why your output is different.  rename is a regular part of Ubuntu.

---

