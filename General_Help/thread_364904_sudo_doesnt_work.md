---
title: "sudo doesnt work"
date: 2007-02-18
forum: General Help
---

### Post by Martin01 on 2007-02-18
```
martin@comp:~$ sudo svnadmin dump /usr/local/svn/project > /usr/local/backup/svn/repo.dump
bash: /usr/local/backup/svn/repo.dump: Permission denied
martin@comp:~$

```

When I try to save dump to different (I tried /tmp) directory, it works.
It also works, when I log as root and type exactly same command.

So what is wrong?

I didn't do anything with /etc/sudoers... It all started with strange error "chdir: error retrieving current directory: getcwd: cannot access parent directories:" and strange things do happen since than :confused: 

Do anybody know what could I have done incorrect?
How could happend that root is different form sudo?


Thanks a lot!

---

### Post by taurus on 2007-02-18
```
sudo svnadmin dump /usr/local/svn/project >  sudo /usr/local/backup/svn/repo.dump
```

---

### Post by WW on 2007-02-18
taurus, forgive me, but that doesn't make sense!  The 'svnadmin dump' command writes to stdout; he is just redirecting the output to  /usr/local/backup/svn/repo.dump.   I think your command will either cause an error (because of an extra argument), or write the output to a file called 'sudo' in the local directory.

Martin01: Does the path /usr/local/backup/svn exist?

Edit: Martin01: Nevermind my question.  If the path didn't exist, you would get an error saying 'No such file or directory', not 'Permission denied'.

Edit 2: Martin01, I think this may be 'normal' when redirecting output with sudo. Here is my little experiment:
> $ touch testfile
$ sudo cat testfile > /etc/testfile
bash: /etc/testfile: Permission denied

So, all you Linux gurus, what's up with that?


Edit 3: Here's an answer: [http://www.courtesan.com/pipermail/sudo-users/2000-March/000060.html](http://www.courtesan.com/pipermail/sudo-users/2000-March/000060.html)
What you need to do is something like this:
>  $ sudo sh -c 'svnadmin dump /usr/local/svn/project >  /usr/local/backup/svn/repo.dump'

---

### Post by Martin01 on 2007-02-19
> **WW said:**
> taurus, forgive me, but that doesn't make sense!  The 'svnadmin dump' command writes to stdout; he is just redirecting the output to  /usr/local/backup/svn/repo.dump. 

Sorry Taurus, but WW is right - your code writes the stdout to the 'sudo' file.

> **WW said:**
> Martin01: Does the path /usr/local/backup/svn exist? 

Yes, this directory exists.

Edit 3: Here's an answer: > sudo sh -c 'svnadmin dump /usr/local/svn/project > /usr/local/backup/svn/repo.dump'

Yes, this works! Thank you WW!

But any way, why is one sudo not enough? When I run command as sudo it means that I want also output to be written with "sudo privileges"... or is this normal behaviour?

Why was permisson denied? Who is more that sudo? The directory /usr/local/backup/svn is owned by backup:backup (owner and group I created). Sudo should make it possible to write output everywhere, or not?

> So, all you Linux gurus, what's up with that?
 
Thank you in advance for explanation.

---

### Post by WW on 2007-02-19
This surprised me, too, but in hindsight it makes sense, if you realize that the redirection of the output is handled by your shell, not by the program being run.  Since your shell does not have root privileges, the attempt to write to /usr/* fails.

The "sudo sh -c  'cmd > out'" creates a *shell* with root privileges, and that shell runs the command, so it succeeds.

---

### Post by sdide on 2007-02-19
as ww says.

if you do 
$ touch hello.txt
$ sudo chown root: hello.txt

$ sudo echo "Hello World" > hello.txt

echo is executed with root priviliges, but the redirection ">" is not. Its executed with the priviliges of the shell - 
which is the users. the operation will fail and return  "bash: hello.txt: Permission denied"

if you do 
$ sudo su -
and then
#  echo "Hello World" > hello.txt 
it will work.
Because everything is executed with root priviliges.

---

