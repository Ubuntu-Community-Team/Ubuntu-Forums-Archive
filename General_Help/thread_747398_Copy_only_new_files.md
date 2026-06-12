---
title: "Copy only new files"
date: 2008-04-06
forum: General Help
---

### Post by Nonno Bassotto on 2008-04-06
I need to copy files between two folders, say from A to B, and I need to copy a file only if it doesn't already exist in B. How can I do it?

I'm sure I already read a thread about this, but I'm not able to find it anymore. The solution was to use cp together with the command yes in a pipe, but I'm not sure how to put it all together.

Please note that I don't need a synchronization program; I just  want to copy files that are not already there.

---

### Post by bodhi.zazen on 2008-04-06
you can use find or rsync

find : [http://www.hccfl.edu/pollock/Unix/FindCmd.htm](http://www.hccfl.edu/pollock/Unix/FindCmd.htm)

rsync: [http://ubuntuforums.org/showthread.php?&t=187894](http://ubuntuforums.org/showthread.php?&t=187894)

---

### Post by ajgreeny on 2008-04-06
Or if you must have a graphical interface use grsync, just a front end to rsync.

---

### Post by prshah on 2008-04-06
> **Nonno Bassotto said:**
> I need to copy files between two folders, say from A to B, and I Please note that I don't need a synchronization program; I just  want to copy files that are not already there.

Here's half a solution: ```

ls -b A > dir1
ls -b B > dir2
diff dir1 dir2 | grep "<" | cut -c 3- > filestocopy

```

At this point, the file "filestocopy" will contain a list of files in "A" that are not in "B". How to make use of this list is beyond me.

Note that ```
for name in `diff dir1 dir2 | grep "<" | cut -c 3-` ; do cp A/$name B/ ; done
``` will work fine as long as the filename DONT contain spaces. You can safely test what it does with ```
for name in `diff dir1 dir2 | grep "<" | cut -c 3-` ; do echo $name  ; done
```

---

### Post by bodhi.zazen on 2008-04-06
I think I mis read the original post.

Lets assume 2 directories, A and B :

```
for i in `ls A`; do
if [[ -e B/"$i" ]]
then :
else cp A/"$i" B
fi
done
``` 

I advise you use the full path for your directories A and B

---

### Post by mali2297 on 2008-04-06
How about this?
```

yes n | cp -i /path/to/A/* /path/to/B

```

---

### Post by prshah on 2008-04-06
> **bodhi.zazen said:**
> 
[code]for i in `ls A`; do


The problem with for is that it will breakup filenames which have spaces in them, even if you use ls -b to "escape" the spaces.

Eg, a file such as "this is a test" will be returned as 

1st iteration
this
2nd:
is
3rd
a
4th
test

and not "this\ is\ a\ test"

So obviously, since the whole filename is not given, the copy will fail.

---

### Post by chunchengch on 2008-04-06
[COLOR="Red"]$ cp -r -u -v /A /B
[/COLOR]

that is all!

---

### Post by unutbu on 2008-04-07
Following up on prshah's solution:

```
ls -b A > dir1
ls -b B > dir2
diff dir1 dir2 | grep "<" | cut -c 3- > filestocopy
cd A
xargs  cp -t B < filestocopy 
```

(I'm assuming A,B and filestocopy are given as absolute paths).

chunchengch's solution is succinct, but is not exactly what the OP asked for. The -u flag will copy any file in A which is newer than the same-named file in B. The OP only wants missing files to be copied.

---

### Post by prshah on 2008-04-07
> **unutbu said:**
> 
```
cd A
xargs  cp -t B < filestocopy 
```


Maybe ```
xargs  cp -t [color=red]../[/color]B < filestocopy 
``` ?

Considering that for me the whole point of ubuntuforums is to learn, I consider the time well spent on this thread. Cheers to all.

---

### Post by Nonno Bassotto on 2008-04-07
First, thank you all. I think this is what I was thinking about

> **mali2297 said:**
> How about this?
```

yes n | cp -i /path/to/A/* /path/to/B

```

and this is another thing I will try.

> **chunchengch said:**
> [COLOR="Red"]$ cp -r -u -v /A /B
[/COLOR]

that is all!

---

### Post by bodhi.zazen on 2008-04-07
```
rsync -t A B
```

also works. Very similar to the cp command.

---

