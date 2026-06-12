---
title: "Using su with the -c option"
date: 2007-02-26
forum: General Help
---

### Post by ocgstyles on 2007-02-26
Hi All,

I have Ubuntu 6.06 installed on one of my desktops.  I seem to be having some trouble with the **su** command from the bash shell.  I'll use the following command for this example:

su - dbadmin -c 'db2start'

This should switch user to "dbadmin", and invoke the "db2start" command.  It completely fails on Ubuntu, but works without a problem on SuSE (and on AIX).  

For some reason, even though I am sourcing in "dbadmin"'s profile when using the "-", since I am also using "-c" it *doesn't* source in the profile.  This is evident in that, "dbadmin"'s profile alters the PATH variable so "db2start" could be found.

I also tried just echo'ing an environment variable instead, which also fails:

su - dbadmin -c 'echo $INSTHOME'

Any idea why Ubuntu doesn't get this "right"?

- Keith

---

### Post by aysiu on 2007-02-26
Ubuntu doesn't default to allowing root logins. It uses *sudo* instead.

Read more here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by highneko on 2007-02-26
# Maybe this will work?
sudo su - dbadmin -c 'db2start'

---

### Post by ocgstyles on 2007-02-27
> **aysiu said:**
> Ubuntu doesn't default to allowing root logins. It uses *sudo* instead.

Read more here:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I read the article, but not sure how its going to help me.  I tried this instead:

```
sudo -u dbadmin echo $HOME
```

It outputs the home directory for the user who ran the command, not the home directory for dbadmin.

I see that the -i option may be what I am looking for so I tried:

```
sudo -u dbadmin -i echo $HOME
```

but I get an error:

```
/bin/echo: /bin/echo: cannot execute binary file
```

Am I just using the command incorrectly?

- Keith

---

### Post by rjfioravanti on 2007-02-27
try this

su dbadmin -c echo $HOME

---

### Post by ocgstyles on 2007-02-27
> **rjfioravanti said:**
> try this

su dbadmin -c echo $HOME

Close!  :)  You need to quote echo $home as 'echo $HOME' so the current shell doesn't expand it.  So the result is:

```
su dbadmin -c 'echo $HOME'
```

This worked perfectly!  Thanks!

---

### Post by ocgstyles on 2007-02-27
> **ocgstyles said:**
> Close!  :)  You need to quote echo $home as 'echo $HOME' so the current shell doesn't expand it.  So the result is:

```
su dbadmin -c 'echo $HOME'
```

This worked perfectly!  Thanks!

Well, almost perfectly.  I do notice that the profile (.bashrc) is not sourced in.  I got around it by sourcing in what I needed before I ran the command.  For example:

```
su <user> -c '. <profile file> ; <command>'
```

hmph...

---

