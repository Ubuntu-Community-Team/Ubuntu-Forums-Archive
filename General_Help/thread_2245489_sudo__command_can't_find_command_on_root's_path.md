---
title: "sudo  command can't find command on root's path"
date: 2014-09-24
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2014-09-24
lxterminal history says it all:
```
me@m:~$ echo $PATH
/first:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/usr/share/fslint/fslint:/last
me@m:~$ sudo echo $PATH
/first:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/usr/share/fslint/fslint:/last
me@m:~$ ls /last/exists
/last/exists
me@m:~$ sudo ls /last/exists
/last/exists
me@m:~$ stat -c %a /last/exists
755
me@m:~$ sudo stat -c %a /last/exists
755
me@m:~$ stat -c %U /last/exists
me
me@m:~$ sudo stat -c %U /last/exists
me
me@m:~$ # In light of the above, why the following?
me@m:~$ exists
me@m:~$ sudo exists
sudo: exists: command not found
me@m:~$ 
```
The executable is clearly in the path for both me and root. Me has no problem. Root can't find it. ???? Have I finally lost my mind?

---

### Post by ajgreeny on 2014-09-24
What is "exists"?

If it is a script it must be executable to run in that manner, I think, so what does ```
ls -l /full/path/to/exists
``` tell us.

---

### Post by Lars Noodén on 2014-09-24
Sudoers can set a variable, secure_path.  If the secure_path is set, its value will be used for the $PATH instead.  So look at the beginning of /etc/sudoers and add what you need there.  See the manual page for sudoers for details.  

Better, use full paths for programs instead of relying on $PATH if you are writing a script.

---

### Post by Dreamer Fithp Apprentice on 2014-09-24
Thanks, AJ.
> **ajgreeny said:**
> What is "exists"?A bash script.
> **ajgreeny said:**
> what does ```
ls -l /full/path/to/exists
``` tell us.```
me@m:~$ ls -l /last/exists
-rwxr-xr-x 1 me me 4141 Sep 17 04:15 /last/exists
me@m:~$ 
```Mea culpa. I should have used the -l option above.

> **Lars Noodén said:**
> Sudoers can set a variable, secure_path.  If  the secure_path is set, its value will be used for the $PATH instead.   So look at the beginning of /etc/sudoers and add what you need there .   . . Better, use full paths for programs instead of relying on $PATH if you  are writing a script.That's it. I confirmed it by adding that  dir to the secure_path statement in sudoers. I may undo that and do it  one of the other ways instead, but that experiment made it clear to me.  Thanks a bunch.

I had the delusion the the secure_path was effectively added to PATH  rather that substituted for it. But I can see why that might not be a  good idea. I suppose it might be as important to keep some software out  of root's path as it is to keep other software out of a user's.

Thanks, guys. Y'all are quick.

---

### Post by steeldriver on 2014-09-24
... also fyi

```

sudo echo $PATH

```

doesn't tell you what you think it does since the shell expands $PATH before calling sudo - you'd needto do something like

```

sudo sh -c 'echo $PATH'

```

---

### Post by btindie on 2014-09-24
> **Dreamer Fithp Apprentice said:**
> 
```
me@m:~$ sudo echo $PATH
/first:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/usr/share/fslint/fslint:/last
```
The above won't be doing what you think it does. The shell first expands $PATH before sudo sees it to give
```
me@m:~$ sudo echo /first:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/usr/share/fslint/fslint:/last
```

The result you're looking for is actually produced by running
```
sudo sh -c 'echo $PATH'
```
Due to the single quotes the shell doesn't expand $PATH.

---

### Post by Dreamer Fithp Apprentice on 2014-09-27
Steeldriver, btindie:

Thanks for these insights. You guys rock. :)

---

