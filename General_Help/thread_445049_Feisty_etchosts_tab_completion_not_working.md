---
title: "Feisty: /etc/hosts tab completion not working"
date: 2007-05-15
forum: General Help
---

### Post by smitjel on 2007-05-15
I just installed Feisty and I'm trying to ssh to some remote servers I have listed in my /etc/hosts file.  It's like my user can't see this file and I can't use tab completion when entering "ssh root@myserver".  I can't tab complete "myserver"...root user is fine though.  I checked the perms on /etc/hosts and it's 644.  What do I need to do to get my user to see /etc/hosts?  Is it a bash profile thing or something?  Thanks for any help.

---

### Post by wormser on 2007-05-17
It sounds like a path problem.  Each user has a path to programs it can execute.  To find out what is in your path:

```
echo $PATH
```

Check that command with root and your user to see the differences.  You then can use the **which** command to find the path of the program.  I forgot how to set your path.  

To set your path:

For just one user, you can put it in ~/.bash_profile

```
export PATH=$PATH:<NEW DIRECTORY TO ADD>
```

There is more about it on this [post]("http://ubuntuforums.org/showthread.php?t=429127&highlight=path").  I am still a little confused about it myself.  Try that and see if it works.

---

### Post by fanatik on 2007-05-17
doesn't bash completion for ssh use the known_hosts file rather than the /etc/hosts?

---

### Post by smitjel on 2007-05-17
> **wormser said:**
> It sounds like a path problem.  Each user has a path to programs it can execute.  To find out what is in your path:

```
echo $PATH
```

Check that command with root and your user to see the differences.  You then can use the **which** command to find the path of the program.  I forgot how to set your path.  

To set your path:

For just one user, you can put it in ~/.bash_profile

```
export PATH=$PATH:<NEW DIRECTORY TO ADD>
```

There is more about it on this [post]("http://ubuntuforums.org/showthread.php?t=429127&highlight=path").  I am still a little confused about it myself.  Try that and see if it works.

root's $PATH doesn't say anything about /etc/hosts so I'm not so sure that editting my $PATH will fix it.  I think it has more to do with .bashrc or .profile or something like that.  But why would root's work but not mine?  I've never seen this before...this worked on Dapper and Edgy.

---

