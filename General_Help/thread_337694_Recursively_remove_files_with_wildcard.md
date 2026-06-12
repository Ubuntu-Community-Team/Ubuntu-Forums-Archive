---
title: "Recursively remove files with wildcard"
date: 2007-01-13
forum: General Help
---

### Post by oroboro on 2007-01-13
I've been searching for a way to do this extremely simple task but cannot seem to find one. What I want to do is remove all the files of a certain type (.class) recursively.
I tried this:
```
rm -rv *.class
```
But it doesn't work (because Linux takes care of wildcards rather than the program?)

I know that I can use a for loop to do it, but is there no simpler way?

---

### Post by Ramses de Norre on 2007-01-13
That command should work.. I use wildcards like that all the time.
Are you sure you're in the right directory etc? Does rm output something?

---

### Post by souki on 2007-01-13
**rm -r** is for deleting directories recursively, this is not what you want to do

instead, you can use find, something like that (replace the path and the pattern) :

first check :
> find /path_to_search -type f -name "*the_patern*"and then, delete :
> find /path_to_search -type f -name "*the_patern*" -exec rm {} \;NB: the '\' and the ';' are important

---

### Post by souki on 2007-01-13
sorry, double post

---

### Post by oroboro on 2007-01-13
That worked, thanks a lot.

> **Ramses de Norre said:**
> That command should work.. I use wildcards like that all the time.
Are you sure you're in the right directory etc? Does rm output something?
Yes I am sure that I was in the same directory. It says that it cannot find the specified file. If you can get it to somehow work, could you post how you did it?

---

### Post by souki on 2007-01-13
for your security, I have to tell you,

I'm sure that rm -r works only on directories
if you don't believe me, check the manual

or try this proof :

> touch blah.class
mkdir sub1
touch sub1/blah.class
rm -r *.class
ls sub1/
it will only remove the first blah.class, because it's the only one matching the patern
that's it, the pattern cannot be recursive
all you can do is

> rm *.class */*.class */*/*.class  ... ans so onnow, if you have a directory named "sub.class", rm -rf *.class will remove the directory and all the files inside (recursively)

please, always use the "find" method I mention earlier, it is safe

---

### Post by Hossie on 2007-01-13
There is an easy explanation for that: All wildcards get expanded by the *shell* _before_ it gets passed to the program. Programs never see wildcards. So the shell expands *.class to 1.class 2.class in the current directory, and then passes these arguments to the program. So you just pass 2 "class" files to rm, and it just deletes that.

---

### Post by Ramses de Norre on 2007-01-13
```
ramses@icarus:~$ mkdir test
ramses@icarus:~$ cd test/
ramses@icarus:~/test$ touch 1.class
ramses@icarus:~/test$ touch 2.class
ramses@icarus:~/test$ touch foo.class
ramses@icarus:~/test$ touch test
ramses@icarus:~/test$ ls
1.class  2.class  foo.class  test
ramses@icarus:~/test$ rm *.class
ramses@icarus:~/test$ ls
test
ramses@icarus:~/test$ 

```

Is it this kind of thing you were trying to do?

---

### Post by souki on 2007-01-13
I don't think so, he's pretty clear with what he wants to do
"remove all *.class files recursively"

---

### Post by sstucke on 2007-09-03
I wrote  a howto for deleting files recursively (you may even preview which files will be deleted):
[http://en.tuxero.com/2007/09/how-to-delete-useless-windows-files-in.html]("http://en.tuxero.com/2007/09/how-to-delete-useless-windows-files-in.html")
Cheers!

---

### Post by steven0451 on 2007-11-27
> **sstucke said:**
> I wrote  a howto for deleting files recursively (you may even preview which files will be deleted):
[http://en.tuxero.com/2007/09/how-to-delete-useless-windows-files-in.html]("http://en.tuxero.com/2007/09/how-to-delete-useless-windows-files-in.html")
Cheers!

That was the best, it was **exactly** what I was trying to do. Thank you!

*Sorry if this post bumped the thread, I just had to say thanks.* :)

---

### Post by bodhi.zazen on 2007-11-27
> **steven0451 said:**
> That was the best, it was **exactly** what I was trying to do. Thank you!

*Sorry if this post bumped the thread, I just had to say thanks.* :)

Nice link, but, FYI, this is exactly what souki advised earlier in the thread :)

---

