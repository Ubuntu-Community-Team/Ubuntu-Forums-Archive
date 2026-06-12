---
title: "How do I save my alias' and my scripts?"
date: 2007-02-27
forum: General Help
---

### Post by jincast90 on 2007-02-27
Hello. I have to questions which I hope you can answer.

1. Is it possible to "save" an alias. What I mean is that each time I close a terminal window all my alias' will disapeer, so I have to write in the alias again each time I have had my terminal closed.

2. I have a folder containing some scripts. This folder is located at: /home/myname/scripts How do I get this folder to intigrate into the command line. For example: If I have a script called "script1" in located at /home/myname/scripts I would normally cd to that directory, and then do a ./script1 to launch it. What I want to do is to be able to type script1 anytime and anywhere from the terminal and It will use this script.

---

### Post by taurus on 2007-02-27
1.  You put your aliases in ~/.bashrc.

```
gksudo gedit ~/.bashrc
```

2.  And while you are editing your ~/.bashrc to include your aliases, you also need to add these two lines in there for that new path.

```
PATH=$PATH:/home/**myname**/scripts
export PATH
```

---

### Post by jincast90 on 2007-02-27
Thank you. I will give it a try.

---

### Post by jincast90 on 2007-02-27
The answer for the 1. worked out perfect. But the second did not. I did indeed type what taurus said. Do I need to call scripts something special to be recognized by the shell, or does anyone else know what I might be doing wrong?

---

### Post by taurus on 2007-02-27
Is your login name myname?  Did you replace myname in /home/myname/scripts with the actual name that you log in with?

---

### Post by WW on 2007-02-27
There is no need to use gksudo to edit .bashrc.  The command
> gedit ~/.bashrc
works just fine.

---

### Post by RedSquirrel on 2007-02-27
Can you tell us the output of:

```
 whoami
```and

```
echo $PATH
```
And with regard to aliases, if you have a lot of them, I would recommend that you put them in a separate file, called ".bash_aliases". That way, you dont' have to go through your .bashrc file when you want to add or remove aliases.

The .bash_aliases file needs to be included from .bashrc

Before you make changes to .bashrc, it's not a bad idea to make a backup copy:

```
cp ~/.bashrc ~/.bashrc.bak
```

In your .bashrc, you should have a section like this:

```
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```If those last three lines have a '#' in front of them, delete the #.

After that, run this command in a terminal:

```
source .bashrc
```

to apply the changes to the terminal you're currently using.

---

