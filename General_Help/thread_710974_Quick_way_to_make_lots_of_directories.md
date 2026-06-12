---
title: "Quick way to make lots of directories?"
date: 2008-02-29
forum: General Help
---

### Post by Oen386 on 2008-02-29
I am looking to make a bunch of directories, and sub directories.

I want to do something like /folder 1/subfolder 1/, /folder 1/subfolder2/

Is there any quick way to make 50 or so folders without typing the command everytime.. maybe like a script I can enter?

Thanks.

---

### Post by Mr. C. on 2008-02-29
Sure, but you'll have to help clarify how you want the folder names to be created.

```
mkdir -p 
```

will create all the necessary subdirectories.  Placed inside a loop, you can create anything you want.  For instance:
```

for i in 1 2 3 4 5 6 7 8 9 10 ; do
    mkdir -p dir/level1.$i/level2.$i/level3.$i/level4.$i/level5.$i
done
```

That's 50 right there.  Just change the path components as you see fit, or the for loop list.  You can nested loops for more varieties.

MrC

---

### Post by ghostdog74 on 2008-02-29
```

mkdir folder{1..30}

```
use a for loop if desired to create sub directories. I will leave it to you.

---

### Post by Oen386 on 2008-02-29
Alright..
Well I tried doing like /subfolder 1/, but that did not work properly. Can you tell me the right way to do that?

> for i in 1 2 3 4 5 6 7 8 9 10 ; do
    mkdir -p dir/Episode\ $i
done


Also how do you set it to 50? I realized it did 50 folders, but how is that computed from the above script? Thanks again.

---

### Post by Mr. C. on 2008-02-29
When something "doesn't work properly", show your commands and output.  We can't help solve a problem when there isn't data to analyze.

The code loop you have will create 10 directories.  Unless you need spaces in the directory names, avoid it.  It will trip you up until you learn about proper shell quoting.  Use underscores if you want.

Your script won't create 50 folders; mine did, because I made a series of folder components.  Not how many / path separators in mine vs. yours.

You can replace the iteration list "1 2 3 4 5 6 7 8 9 10" with the enumeration shorthand {1..50}.

```
for i in {1..50} ; do
    mkdir -p dir/Episode\ $i
done
```

Give yourself some debug output to help you see what is going on:


```
for i in {1..50} ; do
    echo Making "dir/Episode $i"
    mkdir -p dir/Episode\ $i
done
```

Or in my script sample case, which I've modified slightly to give you more ways of seeing what's going on:

```
set -x
for i in {10..1} ; do
    mkdir -p dir/level1.$i/level2.$i/level3.$i/level4.$i/level5.$i
done
```

MrC

---

### Post by Oen386 on 2008-02-29
I got it working. Thank you for the examples.

---

