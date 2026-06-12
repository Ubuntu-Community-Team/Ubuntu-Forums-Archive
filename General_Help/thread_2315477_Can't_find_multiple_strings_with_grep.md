---
title: "Can't find multiple strings with grep"
date: 2016-02-29
forum: General Help
---

### Post by peter1897 on 2016-02-29
I have a text file that has lines like these:
```

1. Redirect chroot sftp user to specific directory.
2. Chroot can be created only with root permissions.
```

If i search for the words **chroot** and **root** it shows only the first line:
```
max@ubuntu:~$ grep chroot test | grep root
Redirect chroot sftp user to specific directory.
```

If i add the parameter -w to match the exact words it doesn't find anything:
```
max@ubuntu:~$ grep chroot test | grep root -w
max@ubuntu:~$
```

Why it doesn't find the second line of the file?

---

### Post by howefield on 2016-02-29
You only have one instance of the word "chroot" so.... you might want to add the -i switch which will ignore case.

---

### Post by vasa1 on 2016-02-29
What about trying```
grep -E "chroot|root"
``````
05:29 PM ~/Desktop/ztemp $ grep -E "chroot|root" temppp
1. Redirect chroot sftp user to specific directory.
2. Chroot can be created only with root permissions.
05:29 PM ~/Desktop/ztemp $ 


```

---

### Post by peter1897 on 2016-02-29
@howefield 
I added the -i parameter and now it is working:
```
max@ubuntu:~$ grep -i chroot test | grep root -i
Redirect chroot sftp user to specific directory.
Chroot can be created only with root permissions.
```

But is it possible to add only once the parameter -i at the end of the command and to make it work for both grep commands in the line?

Also, this command highlights only the 'root' matches but doesn't highlight 'chroot' matches. Why is that? 

@vasa1 
I want to use command that finds multiple strings in one line and using **grep -E "chroot|root"** will show lines that have only 'root' or 'chroot' in them.

---

### Post by vasa1 on 2016-02-29
Okay, I don't understand what's going on here. Why the pipe?

Also root is a subset of chroot which adds to my confusion.

---

### Post by peter1897 on 2016-02-29
> **vasa1 said:**
> Okay, I don't understand what's going on here. Why the pipe?

Also root is a subset of chroot which adds to my confusion.


As i said i want to search only for lines that contains all words.
This is the test file, it has 4 lines:
```
max@ubuntu:~$ cat test -n
     1  Redirect chroot sftp user to specific directory.
     2  Chroot can be created only with root permissions.
     3  root
     4  chroot
```


If i use *grep -E "chroot|root"*  it will show all lines:
```
max@ubuntu:~$ grep -E "chroot|root" test
Redirect chroot sftp user to specific directory.
Chroot can be created only with root permissions.
root
chroot
```

---

### Post by vasa1 on 2016-02-29
Maybe this: [http://stackoverflow.com/questions/6480687/grep-for-2-words-existing-on-the-same-line](http://stackoverflow.com/questions/6480687/grep-for-2-words-existing-on-the-same-line) with -w for whole words?

For the file "max":
```
This is string1 followed by string2
This is string2 followed by string1
This line has no numbered string
This is string1 by itself
This is string2 by itself
This is substring1 followed by substring2
This is substring2 followed by substring1

```

```
$ grep -E -w 'string1.*string2|string2.*string1' max
This is string1 followed by string2
This is string2 followed by string1
$ grep -E 'string1.*string2|string2.*string1' max
This is string1 followed by string2
This is string2 followed by string1
This is substring1 followed by substring2
This is substring2 followed by substring1

```You may be interested in [this answer]("http://stackoverflow.com/a/6482230") which some comments regarding the use of pipes.

---

### Post by peter1897 on 2016-03-01
@vasa1 Thanks, that is useful information! 
Any idea why when i use pipe it highlights only the last string in the command? For example, if i search: *grep word1 file.txt | grep word2 | grep word3* it will highlight only the word3 matches.

---

### Post by steeldriver on 2016-03-01
By default, the alias for grep only colors output when it's going direct to a terminal (not a pipe), using the `--color=auto` setting

```

$ alias grep
alias grep='grep --color=auto'

```

You should be able to alter that by adding `--color=always` to the piped greps

```

grep --color=always -iw chroot test | grep -iw root

```

---

### Post by peter1897 on 2016-03-01
@steeldriver Thanks, it's working! I also changed the alias from 'grep --color=auto' to 'grep --color=always'

---

