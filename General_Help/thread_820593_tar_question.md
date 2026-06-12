---
title: "tar question"
date: 2008-06-06
forum: General Help
---

### Post by chantegreil on 2008-06-06
Hi,

I'm trying to use the unix 'tar' command and have it omit a specific folder.  I can't find an answer to my question in the man pages or with a Google search, so here goes ...

I'm in folder x, and it contains:
a
a/a
a/a/asdf.txt
a/asdf.txt
a/b
a/b/a
a/b/a/asdf.txt
a/b/a/a
a/b/a/a/asdf.txt
a/b/asdf.txt

I want to tar everything except a/a (and everything under a/a).

How can I do this?

Here's what I tried already:
tar -cvf a.tar --exclude "a/a" --no-ignore-case --no-wildcards a
a/
a/asdf.txt
a/b/
a/b/a/
a/b/a/asdf.txt
a/b/asdf.txt

In this case, it also filtered a/b/a/a which is not what I want.

I tried the --no-recursion option, but then it doesn't descend into any folders.
I tried the 'exclude-list', but this behaves the same as above.

I know I can solve my issue by 'inclusively' listing all the folders I want, like ...

tar -cvf a.tar a/b a/asdf.txt

... but this could get extremely painful if the directory hierarchy were less simple.

There must be a better way.  Any ideas?

Thanks,

Phil

ps: I'm new to posting ... sorry if this is the wrong place for this question

---

### Post by geirha on 2008-06-06
In this case, instead of specifying a, you can specify ./a (which is the same), but then you can filter on the first a/a only:
```
tar -cvf a.tar --exclude "./a/a" ./a
```

---

### Post by chantegreil on 2008-06-06
Hi, and thanks for the quick response.

What about if somewhere in the hierarchy there is a path like:

.../my_folder./a/a/more_important_folders/...

Maybe too obscure to worry about?

---

### Post by geirha on 2008-06-06
It will not match actually. ```
$ mkdir -p a/b./a/a 
$ touch a/b./a/a/asdf.txt
$ tar -cvf a.tar --exclude "./a/a" ./a
[...cut...]
./a/b./a/a/
./a/b./a/a/asdf.txt

```

The pattern must match full path components. --exclude="sdf.txt" will not work either, but --exclude "?sdf.txt" and --exclude="asdf.txt" will match the asdf.txt files.

You might find it easier to just include the right directories though, like ```
tar -cvf a.tar a/asdf.txt a/b/
```

---

### Post by chantegreil on 2008-06-06
Wonderful! Thank you _very_ much :)

---

