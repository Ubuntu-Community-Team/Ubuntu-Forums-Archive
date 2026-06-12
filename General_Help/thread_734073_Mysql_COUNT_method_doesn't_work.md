---
title: "Mysql COUNT method doesn't work"
date: 2008-03-24
forum: General Help
---

### Post by protenniser on 2008-03-24
Hi all,

I have installed mysql and mysql query browser from repositories, however I cannot use COUNT method in mysql.
For example: a simple count method like this;
SELECT COUNT(*) FROM Students where students is a predefined table gives an error that says that mysql.count function is not defined.

I have a homework assignment and for that assignment I have to use COUNT method to write some queries, so all help is appreciated, what might be the problem?

Thanks in advance...

---

### Post by very_japi on 2008-03-24
Depending of how much in a hurry you are, you could do the following hard-solving solutions:

1.- Uninstall MySQL (completely, sudo apt-get purge mysql-server)

2.- Delete all configuration files at /etc/MySQL and all binaries at /bin and /usr/local/mysql (i think that's where they are located)

3.- reinstall MySQL and try again.

If that doesnt work and you are bitting your nails, you could try booting into the live CD and installing MySQL in there. Or re-intall ubuntu altoghether (wouldnt recomend that of course)

---

### Post by protenniser on 2008-03-24
Hi, thanks for the reply...
However why shouldn't it work? It is quite weird. I have also tried to install mysql on my virtual windows (on vmware) and on windows COUNT method doesn't work again, and gives the same error: mysql.COUNT function doesn't exists.
However I can see the COUNT method in the method lists and mysql browser recognizes that method (I think so since it is bold).
Uninstalling and reinstalling Ubuntu is quite expensive however I might give a try to your 1st suggestion.
Any other help, the homework is due to Wednesday night!

---

### Post by very_japi on 2008-03-24
Are you running the command as root? The user ight not have acces to certain methods, like count. That miht be possible.

I just copy-pasted the SQL statement in your first post and it worked, so nothign wrong with it.



If all fails, and before you trash your antire system in desperation you could try compiling mysql from source code

apt-get source mysql
cd mysql.c (or somethign like that)
./configure
make
make install

It might take a while, cuz mysql s a big big application, but ... if all fails.

---

### Post by protenniser on 2008-03-27
Hi all,

I am sorry that I bothered you all but we have (my friend) solved the problem. The problem was I was writing the query like this:
..... COUNT (*)
where as weird but mysql doesn't like the blank space between COUNT and (*) so when writing like this:
...... COUNT(*) the problem is solved. Sorry again...

---

