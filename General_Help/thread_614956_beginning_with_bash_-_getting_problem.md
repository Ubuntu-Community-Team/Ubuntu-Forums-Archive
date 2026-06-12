---
title: "beginning with bash - getting problem"
date: 2007-11-16
forum: General Help
---

### Post by Griffiss on 2007-11-16
I've just started to learn about bash scripting and was following the tutorial [here]("http://linuxcommand.org/writing_shell_scripts.php")

However, I quickly got into difficulties.

I've made a bin folder in my home folder, but this doesn't feature in my PATH (echo $PATH doesn't include it as output), eventhough the following is in my ~/.bash_profile:

```
# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
```

There are a couple of other problems but if I get this one sorted then the rest might be ok.

ps I recently made a new /home partition and not everything transferred automatically from my old home folder - I had to move .bash_profile over afterwards.

Any help much appreciated

---

### Post by mali2297 on 2007-11-16
> **Griffiss said:**
> I've just started to learn about bash scripting and was following the tutorial [here]("http://linuxcommand.org/writing_shell_scripts.php")

However, I quickly got into difficulties.

I've made a bin folder in my home folder, but this doesn't feature in my PATH (echo $PATH doesn't include it as output), eventhough the following is in my ~/.bash_profile:

```
# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
```

There are a couple of other problems but if I get this one sorted then the rest might be ok.

ps I recently made a new /home partition and not everything transferred automatically from my old home folder - I had to move .bash_profile over afterwards.

Any help much appreciated

The file .bash_profile is read at login, so you might need to reboot.

Also, add
```

export PATH

```
at the end of the file.

---

### Post by Griffiss on 2007-11-16
Hi

I rebooted and added

export PATH

to the end of .bash_profile, but my home/bin is still not included. Here is my .bash_profile, in case it helps:

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
    PATH=~/bin:"${PATH}"
fi

export PATH
```

---

### Post by mali2297 on 2007-11-16
You could try some troubleshooting, type the line directly in the terminal:
```

PATH=~/bin:"${PATH}"
echo $PATH

```
Any luck?

If success, try adding the line in the file .bashrc:
```

export PATH=~/bin:"${PATH}"

```
Restart the terminal, and check again
```

echo $PATH

```

> 
I rebooted and added

export PATH

to the end of .bash_profile, but my home/bin is still not included. 


You did add the line *export PATH* before reboot, didn't you?

---

### Post by Griffiss on 2007-11-16
Yes, I made all changes before reboot.

And yes, adding the line to .bashrc worked! thanks

Any idea why this worked rather than making additions to .bash_profile?

---

### Post by mali2297 on 2007-11-16
> **Griffiss said:**
> 
Any idea why this worked rather than making additions to .bash_profile?

If you want to continue troubleshooting, you could add the line
```

touch ~/hello_world

```
to the end of .bash_profile. Reboot and see if you've got an empty file hello_world in your home directory.

If success, then it must be the **if** statement that fails even though the directory ~/bin exists.

If failure, then .bash_profile isn't read at all.

---

### Post by Griffiss on 2007-11-16
no ~/hello_world directory was created.

This means .bash_profile isn't being read at all? Why would that be?

---

### Post by mali2297 on 2007-11-16
> **Griffiss said:**
> no ~/hello_world directory was created.

This means .bash_profile isn't being read at all? Why would that be?

I think the problem is that GDM (the graphical login manager) doesn't read the file. For a discussion:
[http://ubuntuforums.org/showthread.php?t=350855](http://ubuntuforums.org/showthread.php?t=350855)

I would suggest that you use .bashrc instead. That file is read every time you open a terminal.

---

### Post by Griffiss on 2007-11-16
Ok, I'll read that.

Thanks a lot for your help Mali!

---

