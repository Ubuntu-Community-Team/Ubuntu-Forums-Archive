---
title: "ls -d and symbolic links"
date: 2014-10-18
forum: General Help
---

### Post by SteelCore on 2014-10-18
In the manual page for **ls**, the -d (--directory) option is described as 
```
-d, --directory
        list directory entries instead of contents, and do not dereference symbolic links
```
Can someone please explain what does "**_dereference_** symbolic links" mean. 
Thank you for your help.

---

### Post by O9aIevckc0 on 2014-10-18
it appears this means that if it comes across a symbolic link, it examines the file that the link points to

if i interpreted the information here correctly

[https://www.gnu.org/software/findutils/manual/html_node/find_html/Symbolic-Links.html](https://www.gnu.org/software/findutils/manual/html_node/find_html/Symbolic-Links.html)

---

### Post by matt_symes on 2014-10-18
Hi

> **abpabp said:**
> it appears this means that if it comes across a symbolic link, it examines the file that the link points to

if i interpreted the information here correctly

[https://www.gnu.org/software/findutils/manual/html_node/find_html/Symbolic-Links.html](https://www.gnu.org/software/findutils/manual/html_node/find_html/Symbolic-Links.html)

Kind of means the exact opposite.

```
ls -d
```

 It doesn't follow the symlink the directory points to.

Compare it to

```
ls -H
```

This will dereference the symlink.

Here's an example using the zsh. 

Test is a symlink to a folder (storage/test/) that contains the file, test_file.

```
matthew-laptop:/home/matthew:5 % ls -l Test 
lrwxrwxrwx 1 matthew matthew 12 Oct 19 00:38 Test -> storage/test/
matthew-laptop:/home/matthew:5 % ls -d Test
Test@
matthew-laptop:/home/matthew:5 % ls Test 
Test@
matthew-laptop:/home/matthew:5 % ls -H Test
test_file
matthew-laptop:/home/matthew:5 % 
```

I should point out that different shells use different aliases for the ls command.

```
matthew-laptop:/home/matthew:5 % alias ls
ls='ls -F --color=auto'
matthew-laptop:/home/matthew:5 % bash
matthew@matthew-laptop:~$ alias ls
alias ls='ls --color=auto'
matthew@matthew-laptop:~$ 
```

So I'll run the same commands in bash and let you spot the difference.

```

matthew@matthew-laptop:~$ ls -l Test
lrwxrwxrwx 1 matthew matthew 12 Oct 19 00:38 Test -> storage/test
matthew@matthew-laptop:~$ ls -d Test
Test
matthew@matthew-laptop:~$ ls Test
test_file
matthew@matthew-laptop:~$ ls -H Test
test_file
matthew@matthew-laptop:~$ 

```

Hopefully i have made that a bit clearer and not muddied the waters.



Kind regard

---

### Post by SteelCore on 2014-10-20
So 'dereference' basically means list whatever file or directory the symbolic link points to.
In your examples you seem to have used two types of shells. In the first, **ls** did not dereference the symbolic link (Test@ is the link itself) but when you switched to bash **ls** derefernced the symbolic link and showed the file (test_file) that it pointed to.

Thank you for your clarification.

---

### Post by matt_symes on 2014-10-20
Hi

> **SteelCore said:**
> So 'dereference' basically means list whatever file or directory the symbolic link points to.


Yes. Pretty much.

> 
In your examples you seem to have used two types of shells. In the first, **ls** did not dereference the symbolic link (Test@ is the link itself) but when you switched to bash **ls** derefernced the symbolic link and showed the file (test_file) that it pointed to.

Thank you for your clarification.

To be totally clear, it is not the shell that makes the difference but the alias the shell uses for ls.

I can make the Bash shell behave the same way as the Zsh shell by changing its alias for ls. That is the point i was trying to make.

Here's an example to make Bash behave like Zsh when using the ls command.

```
matthew@matthew-laptop:~$ alias ls
alias ls='ls --color=auto'
matthew@matthew-laptop:~$ unalias ls
matthew@matthew-laptop:~$ alias ls='ls -F --color=auto'
matthew@matthew-laptop:~$ ls -l Test
lrwxrwxrwx 1 matthew matthew 12 Oct 19 00:38 Test -> storage/test/
matthew@matthew-laptop:~$ ls -d Test
Test@
matthew@matthew-laptop:~$ ls Test
Test@
matthew@matthew-laptop:~$ ls -H Test
test_file
matthew@matthew-laptop:~$
```

Kind regards

---

### Post by SteelCore on 2014-10-25
Thank you again for the detailed explanation.

---

