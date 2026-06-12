---
title: "Problem with my /home directory"
date: 2007-10-10
forum: General Help
---

### Post by trymbill on 2007-10-10
Hi guys!

I can't seem to be able to open my /home/user directory :-/
This is the output:

```

maggi@hruturinn:~$ cd /home
maggi@hruturinn:/home$ ls
ftp  FTP-shared  maggi  www
maggi@hruturinn:/home$ cd /maggi
-bash: cd: /maggi: No such file or directory

```

I just setup VSFTP and I can see my folder "maggi" and I can create folders in it and everything but I can't seem to be able to do it in Ubuntu it self.  I have to be able to do this so I can put the "www" link from my home directory to the /var/www directory.

Can some one please help me with this?

---

### Post by Scheater5 on 2007-10-10
/maggi indicates the folder with the full pathname "/maggi."  So that command you are using is not trying to go to /home/maggi, but to /maggi.
In the Bash shell, the period indicates "the folder you are now working in."  So if you are in /home, to go to /home/maggi you would use the command ```
cd ./maggi
``` or alternatively the tilde is a shortcut for the current user directory, so merely issue the command ```
cd ~
```

---

### Post by trymbill on 2007-10-10
Thank you for the quick response!  I tried doing that, but it doesn't work.

This is what I tried:

```

maggi@hruturinn:~$ cd /home
maggi@hruturinn:/home$ ls
ftp  FTP-shared  maggi  www
maggi@hruturinn:/home$ cd ./maggi
maggi@hruturinn:~$

```

And also:

```

maggi@hruturinn:~$ cd /home/maggi
maggi@hruturinn:~$

```

And like you said, using ~:

```

maggi@hruturinn:~$ cd ~
maggi@hruturinn:~$

```

It just returns me to the "desktop" directory or the main directory.  I've got no clue on why this is happening :-/

---

### Post by Scheater5 on 2007-10-10
> maggi@hruturinn:~$

Notice the tilde "~"? This is Bash shorthand for the current user's home directory.  You have in fact reached your destination.  Try the command "ls" from there for proof.

---

### Post by trymbill on 2007-10-10
Ah! Thank you for being so patient :)

---

