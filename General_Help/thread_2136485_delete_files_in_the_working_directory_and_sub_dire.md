---
title: "delete files in the working directory and sub directories?"
date: 2013-04-17
forum: General Help
---

### Post by sohlinux on 2013-04-17
Hello,

How can I delete all files called 001.txt in the working directory and its sub directories from the command line?

I am in /home/tom/test/ I have 40 directories and I want to remove all the files called 001.txt in all 40 directories

thanks

---

### Post by sohlinux on 2013-04-17
sussed it out

find . -type f -name "001.txt" -exec rm -f {} \;

---

### Post by Vaphell on 2013-04-17
find supports *-delete* flag that makes *-exec rm* unnecessary

---

### Post by sisco311 on 2013-04-17
Cool! Almost perfect. :evil:

You should put the -name test before the -file test in order to avoid having to check each file if it's a regular file or not. You only need to check the files with the name `001.txt'. ;)


And `rm' accepts one or more files as an argument, so (in Ubuntu; GNU/find) you could use the `-exec command {} +' form of the -exec action:
```
find ./ -name '001.txt' -type f -exec rm -- {} +
``` 

Please check out [http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

From your OP, is not clear for me if you have multiple levels of subdirectories or not.

If you have a single level of directories, then you could use a glob to match each file:
```

printf '%s\n' ./*/001.txt
```

If not, then, in bash 4 you can use the globstar shell option to match the files recursively in the directory and all subdirectories:
```

printf '%s\n' ./**/001.txt
```

---

### Post by sisco311 on 2013-04-17
> **Vaphell said:**
> GNU/find supports *-delete* flag that makes *-exec rm* unnecessary

fixed :)


@OP
Oh and, rm by default (without the -r, -R or --recursive(GNU)  flag) does not remove directories; so if you want to remove any files (including character/block specials, symbolic links, named pipes...) except directories, then you don't even have to use the -type option of the find command.

---

