---
title: "Best way to search for files and folders?"
date: 2015-07-08
forum: General Help
---

### Post by peter1897 on 2015-07-08
I am looking for a search command that can produce all available data for specified search word. So far i now about this search commands: whereis, which, find, locate, but none of them seems to be able to produce comprehensive results. For example, if i search for **mysql** none of the commands list the location /var/lib/mysql/ where is the mysql data. 

What command or method i can use to implement comprehensive search?

---

### Post by steeldriver on 2015-07-08
The `locate` command should find it unless (i) it has been added more recently than the database was last updated or (ii) you have modified the updatedb.conf, for example to exclude /var . In the former case, you can force an update using
```

sudo updatedb

```

The `find` command should work provided you start it from high enough in the directory tree and don't exclude directory matches e.g.

```

find / -name 'mysql'

```


```

$ find / -name 'mysql' 2>/dev/null
/var/log/mysql
**/var/lib/mysql**
/usr/share/mysql
/usr/share/bash-completion/completions/mysql
/usr/share/maven-repo/mysql
/usr/lib/mysql
/usr/lib/perl5/auto/DBD/mysql
/usr/lib/perl5/DBD/mysql
/usr/bin/mysql
/etc/mysql
/etc/apparmor.d/abstractions/mysql
/etc/init.d/mysql

```

---

### Post by peter1897 on 2015-07-08
Thanks. Using **find** from the root directory worked well. Also, after updating updatedb the **locate** command found the directory /var/lib/mysql.

---

### Post by ajgreeny on 2015-07-08
By default locate will use the database of the total filesystem, but you can limit the output by piping to grep with, for example, command ```
locate **searchterm** | grep /home/$USER
```just to find the searchterm in your home.

It is possible to limit the updatedb database but I can't now remember how, and I think it more flexible just to pipe the output, as there is then no need to update to a full database afterwards.

---

### Post by OldGrampa on 2015-08-02
Regarding:  find / -name 'mysql'
I tried it, and then compared it with KFind.
KFind found many more.

I'm not familiar with   find,
I want it to search all my hard drives,
and all hidden files,
meaning all the files in the entire computer.

Is there some additional options I should use with  find.
Tx for any comments.

---

### Post by nerdtron on 2015-08-02
The find command when used to search on / will search all files in all hard drives (as long as the drives are mounted of course)
You can try to find all file/folder with the name mysql on it using the following command, I used -iname instead of -name so because iname is not case sensitive.
The below command will also search hidden files/directories.
```
 find / -iname "*mysql*" 
```

 If you want to search purely hidden files, the start the keyword with a dot (.) since all hidden files/folders have names starting with a dot.
```
 find / -name ".*mysql*" 
```

more practical examples of find command: [http://www.tecmint.com/35-practical-examples-of-linux-find-command/](http://www.tecmint.com/35-practical-examples-of-linux-find-command/)

---

### Post by OldGrampa on 2015-12-07
Thank you nerdtron:

Using 
find / -iname "*kfindrc*"
helped me find an additional file in /root/,
that Kfind missed.

---

