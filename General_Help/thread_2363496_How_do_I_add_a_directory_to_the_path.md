---
title: "How do I add a directory to the path?"
date: 2017-06-10
forum: General Help
---

### Post by nzdreamer55 on 2017-06-10
Hi everyone,

I am pretty green with linux but know that I need to add a directory to my path so I can execute a script from any other place.  In windows I know how to do this, but not in linux OS.

Could someone point me to a tutorial on how to do this?  Also if i add a directory will all the sub-directories also be included?

Thanks

---

### Post by Bashing-om on 2017-06-10
nzdreamer55; Hello; I can take a stab at this  -

> 
 so I can execute a script from any other place. 


That functionality already exists . in your home directory is the directory bin. Place your executables here and the system will find them .

Now to answer the question ; Let's say the bin directory did not exist, and you create the directory - to add it to the path one would run terminal command:
```

 echo 'PATH="$HOME/bin:$PATH"' >> "$HOME/.bashrc" 

```

such that when the .bashrc file is parsed the directory is added to the path .

to see what is presently set for the PATH :
```

echo $PATH

```
 and you see that the PATH "/home/<your_user_name>/bin:" is already set .

[INDENT][INDENT]we make it what it is
[/INDENT][/INDENT]

---

### Post by efflandt on 2017-06-11
Actually things are normally inserted in your PATH in ~/.profile (a hidden file in your home directory). That is an example of how "bin" directory in your home directory is inserted to run your own scripts, etc. there, before looking in the rest of your $PATH. If hidden files (beginning with dot) are not shown when you open the file manager (nautilus) you can display them with Ctrl+H.

But note that your ~/.profile is only looked at when you log in. So if you add something to that file, the new $PATH would not take effect until the first time you log out of X and log back in (or restart your computer). You separate each path with colon (:) and include :$PATH at the end to include rest of existing path.

---

### Post by nzdreamer55 on 2017-06-11
Thank you both for the help.  I was able to add the folder that I needed to my path!  Problem solved :-)

---

