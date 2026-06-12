---
title: "bash script help! (recursive)"
date: 2007-04-25
forum: General Help
---

### Post by josh on 2007-04-25
hi all!

i want to make a script that will check the md5sum of all the files and directory in the source directory. 

if it was only files, that would be no problem. but the roadblock is, there are directories. i can "md5sum * check.log" it will just complain that there is a directory and could not proceed checking the contents. to sum it up, how can i recursively use md5sum without downloading any other software and just by using clever scripting techniques? im a batch script newbie :)

---

### Post by stylishpants on 2007-04-25
No script is necessary, it's just a one-liner.

```

find . -type f -exec md5sum  {} \;

```

---

### Post by josh on 2007-04-25
stylishpants, [SIZE="5"]**[COLOR="Red"]YOU ARE A GENIUS![/COLOR]**[/SIZE] 

thank you very much! 

if its not too much to ask, where did you learn how to do this?

---

### Post by stylishpants on 2007-04-26
This stuff is just really fun to learn.  

It constantly amazes me how the UNIX toolchain provides all these simple utilities -- some of which seem kind of silly on their own -- that when put together can perform some amazingly complex and specific tasks.  

You can sit down and read books about this ("Learning The Bash Shell" and "Linux In A Nutshell" are good) but I don't think you can ever learn it all.  There's just too much out there.  I've been a UNIX power user for 10 years now and I learn new stuff all the time.  (Did you know the bash shell can parse regular expressions?  That came up on this forum this morning.  I had no idea!)

Knowing your way around the shell gives you the ability to quickly perform repetitive tasks that would take hours in a gui, it really pays off if you're a heavy computer user.

It's worth learning "find" really well though.  Also learn how to do loops in the shell:
```
find . -type f | while read x; do XXXXX; done
```
Learn to read man pages.  Keep reading these forums, especially command-line questions.

Thanks for the enthusiastic "Thank-You"!

---

### Post by Nergar on 2008-05-07
md5deep is in the repos but your solution is way COOLER!!!

---

