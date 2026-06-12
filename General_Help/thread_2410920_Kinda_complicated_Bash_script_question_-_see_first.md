---
title: "Kinda complicated Bash script question - see first post"
date: 2019-01-22
forum: General Help
---

### Post by raphaell2 on 2019-01-22
Hi, I hope this is the right forum for bash scripting questions. Now here's my problem:

I have a bunch of files that I keep in one version in Directory A and in a slightly different version in Directory B.

I want to cross-check the files in Directory A and Directory B to see which version is newer. Then I want to copy all the files in Directory A that are *newer* than their versions in Directory B into a *third, *empty, Directory *C *- that is, *not*, at least not at first, into Directory B. 

My eventual goal is to perform various operations on the versions of the files in Directory C later in the script, then copy the modified versions from Directory C into Directory B using cp -u , and finally empty Directory C so that it is clean for the next time I run the script. 

Is there any way of doing this in a bash script?

---

### Post by sisco311 on 2019-01-22
Do the file versions from A and B share the same name? 

What do you mean by newer? atime, ctime or mtime?

There are many ways to do this a bash script. Where did you get stuck?

---

### Post by Holger_Gehrke on 2019-01-22
Assuming the files whose date you want to compare have the same names it should be as simple as
```

cd DirA
for file in * ; do 
  if [[ -f DirB/$file ]] && [[ $file -nt DirB/$file ]] ; then 
    cp $file DirC ;
  fi;
done

```

Warning: that's of the top of my head and untested. I only looked up the '-nt' (newer than, comparison of mtime) operator in the conditional expression (I knew there was something like it but didn't remember exactly ...)

Holger

---

### Post by raphaell2 on 2019-01-22
> **Holger_Gehrke said:**
> Assuming the files whose date you want to compare have the same names

Yes they do! Thank you very much!

> 
 it should be as simple as
```

cd DirA
for file in * ; do 
  if [[ -f DirB/$file ]] && [[ $file -nt DirB/$file ]] ; then 
    cp $file DirC ;
  fi;
done

```

Warning: that's of the top of my head and untested. I only looked up the '-nt' (newer than, comparison of mtime) operator in the conditional expression (I knew there was something like it but didn't remember exactly ...)

Holger

Neat! Thank you!




One workaround that I have come up with before reading your post (although it's probably an old trick that I just hadn't heard about) is to create a little file randomfile.txt, and then add these lines to the very end of the script:

```

rm randomfile.txt
echo 'randomtext' > randomfile.txt

```

That way, I always have a file that was last modified the last time I ran the script, which is very useful for my purposes.

---

### Post by raphaell2 on 2019-01-22
> **raphaell2 said:**
> 
One workaround that I have come up with before reading your post (although it's probably an old trick that I just hadn't heard about) is to create a little file randomfile.txt, and then add these lines to the very end of the script:

```

rm randomfile.txt
echo 'randomtext' > randomfile.txt

```

That way, I always have a file that was last modified the last time I ran the script, which is very useful for my purposes.

*slaps forehead* Of course it's easier to use touch for that file. What was I thinking...

---

