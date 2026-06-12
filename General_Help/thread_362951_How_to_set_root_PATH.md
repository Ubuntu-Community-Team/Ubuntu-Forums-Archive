---
title: "How to set root PATH"
date: 2007-02-16
forum: General Help
---

### Post by sessionip on 2007-02-16
I need to add /usr/local/mysql/bin/ to the root PATH 

i log on my Ubuntu 6.10 by using a regular user, and then "sudo -s" , i enter root password and log in as root.

how do i add that directory to my root PATH ??

Regards

---

### Post by n00bish on 2007-02-16
If you're using bash, it should be like this:
```

export PATH=$PATH:"/usr/local/mysql/bin"

```

Which basically means "export into the shell variable PATH the value stored in $PATH plus a colon and the path you want".  The format of a path is as so:

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

so when you append :/usr/local/mysql/bin/ it will just add the new path to the old one in the correct format.

---

### Post by sessionip on 2007-02-16
sorry,
i forgot to tell that i need this executed automatically every time i login as root.
In Debian there is a file called /etc/profile which does the trick, but i can´t seem to find a similar configuration file to do that in Ubuntu.

Regards

---

### Post by n00bish on 2007-02-16
> **sessionip said:**
> sorry,
i forgot to tell that i need this executed automatically every time i login as root.
In Debian there is a file called /etc/profile which does the trick, but i can´t seem to find a similar configuration file to do that in Ubuntu.

Regards
IIRC, a path that you export should "stick" until you remove it manually.  You should check on that first.  If that doesn't work, make a file called ".profile" in your home directory and put the command in there.  I strongly recommend you do not do this until you are *sure* your path is not keeping the new addition, or else you may end up with a path like this:
```

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/usr/local/mysql/bin:/usr/local/mysql/bin:/usr/local/mysql/bin:/usr/local/mysql/bin:/usr/local/mysql/bin:/usr/local/mysql/bin

```

---

### Post by sessionip on 2007-02-16
This is my .profile file under /root/ but it still does not work, if i type echo $PATH it returns 
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

cat .profile 
# ~/.profile: executed by Bourne-compatible login shells.

if [ "$BASH" ]; then
    if [ -f ~/.bashrc ]; then
        . ~/.bashrc
    fi
fi

export PATH="$PATH:/usr/local/mysql/bin"

mesg n

---

### Post by sessionip on 2007-02-19
any ideas?
i must be something very easy...

Thanx

---

### Post by sdide on 2007-02-19
From "man bash"

 > When bash is invoked as an interactive login shell, or as a non-interactive shell with the --login option, it first reads
       and executes commands from the file  /etc/profile,  if  that  file  exists.   After  reading  that  file,  it  looks  for
       ~/.bash_profile,  ~/.bash_login,  and  ~/.profile, in that order, and reads and executes commands from the first one that
       exists and is readable. 

So if  ~/.bash_profile exists, it will not invoke ~/.profile (unless .profile ofcouse is executed in ~/.bash_profile)

So I would add the 
export PATH=${PATH}:/usr/local/mysql/bin 
to the ~/.bash_profile

---

### Post by sessionip on 2007-02-19
I did it, 
I was able to set the root PATH by editing the /etc/bash.bashrc file. add the following to the end of the file:

```
export PATH="$PATH:/usr/local/mysql/bin"
```

---

