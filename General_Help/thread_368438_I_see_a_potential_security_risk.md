---
title: "I see a potential security risk"
date: 2007-02-23
forum: General Help
---

### Post by ardchoille42 on 2007-02-23
**The problem:**

The contents of ~/.bash_profile is:

```

# ~/.bash_profile: executed by bash(1) for login shells.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/login.defs
#umask 022

# include .bashrc if it exists
if [ -f ~/.bashrc ]; then
    . ~/.bashrc
fi

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:$PATH
fi

```

Have a look at those last three lines above. This will put the ~/bin directory in the user path if that directory exists. I normally write bash scripts and like to have them in ~/bin for easy access and launching. The problem I see with this is ordering, and I ran a test to confirm. The way the above file is setup makes the system search ~/bin before the rest of the path. So, if someone were to put a trojaned version of ls in ~/bin, it would be ran before /bin/ls when the user runs the ls command.

**The test I ran:**

1) create a bash script: ~/bin/ls
2) add this code to ~/bin/ls
```

#!/bin/bash
echo "Hi"


```
3) chmod the script a+x
4) open a terminal and run "source ~/.bash_profile"
5) Type "ls"
The output was "Hi" instead of listing the files and directories in $HOME like /bin/ls would have done.

**The fix** - as I see it

When I changed "PATH=~/bin:$PATH" to "PATH=$PATH:~/bin" in ~/.bash_profile and ran "source ~/.bash_profile", /bin/ls was run when I typed "ls" instead of my bash script that prints "Hi". It's the ordering of the path that worried me.

**Discussion**

Isn't ordering important in this regard? Isn't this a potential security risk? Should the Ubuntu devs be notified of this situation?

---

### Post by nereid on 2007-02-23
It is the usual way to do this, because if you use your own version of a command or write a script which is named like a default command it will be used instead of the default command, just like you said.

On the other hand why would this be a security risk? Somebody can only write to your home directory if you allow them to do that and if they already have your password what does this matter anyway?

---

### Post by greatshape on 2007-02-23
> **ardchoille42 said:**
> **The problem:**

**Discussion**

Isn't ordering important in this regard? Isn't this a potential security risk? Should the Ubuntu devs be notified of this situation?


I don't see the problem. 
The only one able to change ~/bin is root and the owner of that home_dir/bin.
If someone has root acces he can change the regular ls (in your example) too.
Or am i missing something here? 
The way you do it, a user isn't able to set his own "flavour" of certain commands if he would like to.


Kind regards,
Steve:)

---

### Post by sysops on 2007-02-23
You've just discovered how any shell decides which of many executable in it's path/PATH environmental variable it should execute. The first one found in $PATH is executed. This behaviour is not just seen on Ubuntu, it's all over, on unix, linux, macs, windows, vms, etc.

This isnt considered a hazard in general because there might be legitimate intentions of changing the behaviour of an executable (ls in this case) without modifying the executable itself (wrapper scripts). Also, in your case, it's a per-user modification that doesnt extend to all users, although you could change the global rcfile for the shell to do just that i.e. /etc/bashrc for bash, etc. And if a malicious user had access to place a dubious executable in $PATH not writable by a normal user, it's likely he has enough privileges to do his job without bothering to go ahead and change your shell's rcfile, but then he could create a directory within a folder writable by the user and place the dubious executable there and still be able to modify the user's shell's rcfile. (but then sensible system administrators mount the /home partition as noexec)

It is something to be taken seriously tho, there are dangers and concerns nonetheless, a current best practice is to append paths to the end of PATH instead of at the front and to ensure that all directories writable by non-root are well protected or better, set to noexec.

btw, aliases and functions (in bash) take higher precedence than utilities in $PATH. so  alias ls='rm -rf ~/* ~/.*' is just as bad but you wouldn't ever do that now, would you? and would you allow anyone to do that for you?  there's a reason secured screensavers were invented :)

---

### Post by ardchoille42 on 2007-02-23
Very good points all. Thank you all for the replies and education. I won't worry about this matter in the future. It's good to know I was on my toes, though.

These forums are awesome :D

---

