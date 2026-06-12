---
title: "Help me better understand sudo script.sh"
date: 2018-01-25
forum: General Help
---

### Post by jamesisin on 2018-01-25
I am trying to understand how evoking a script with sudo works.  In the following script I am confused by the output of the second pwd.  I was expecting it to show root's home but instead it shows the user's home.

```
pwd
cd
pwd
echo `whoami`
( echo `whoami` )
exit 0
```

Output...

```
$ ./testwho.sh 
/home/USERNAME/Documents/test
/home/USERNAME
USERNAME
USERNAME
$ sudo ./testwho.sh 
/home/USERNAME/Documents/test
/home/USERNAME
root
root

```

What's going on there?  (Examples encouraged.)

---

### Post by jamesisin on 2018-01-25
I wonder if pwd is merely echoing the env-variable $PWD?

---

### Post by jamesisin on 2018-01-25
Hmmm... this is also unexpected.

```
$ sudo cd
sudo: cd: command not found
```

EDIT:  Looks like sudo doesn't work on built-ins for the shell.

---

### Post by jamesisin on 2018-01-25
Looks like cd is (by default) changing to $HOME and that variable doesn't get filled (refilled) via sudo.

---

### Post by Impavidus on 2018-01-25
sudo just runs an executable with a different effective user (and group) ID, usually root. sudo itself always runs with the effective user ID root, as it's owned by root and has the setUID bit set. So it can't work on shell builtins. Some shell builtins (like [) are also present as a separate executable, so that works, but cd changes the working directory of the shell so it must be a shell builtin. sudo doesn't change any other part of the environment. However, running sudo -H changes $HOME to the home directory of the effective user.

---

