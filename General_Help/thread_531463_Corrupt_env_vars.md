---
title: "Corrupt env vars"
date: 2007-08-21
forum: General Help
---

### Post by ecomber on 2007-08-21
WhenI issue the 

set

command, I get a list of my env vars, but at the end of this there is appended what appears to be (an apache ?) script ...

e.g. the file changes ...

SHELLOPTS=braceexpand:emacs:hashall:histexpand:interactive-comments:monitor
SHLVL=1
TERM=vt102
UID=1000
USER=ec
_=less
bash205='3.2.13(1)-release'
bash205b='3.2.13(1)-release'
bash3='3.2.13(1)-release'
_a2dismod ()
{
    local cur;
    COMPREPLY=();
    cur=${COMP_WORDS[COMP_CWORD]};
    _apache2_modsites mods-enabled
}
_a2dissite ()
{
    local cur;
    COMPREPLY=();
    cur=${COMP_WORDS[COMP_CWORD]};
    _apache2_modsites sites-enabled


... and so it goes.

I am trying to find wheer this gest added to my env vars but I'm afraid I can't.

Ant ideas??

Eddie.

---

### Post by manimal on 2007-08-21
If you are using bash as your shell, there are several files to check:

~/.bashrc
~/.bash_profile
/etc/bash.bashrc

(the '~' here means your home directory, so on the command line, you can just type "gedit ~/.bashrc")

---

### Post by ecomber on 2007-08-21
Thanks. Only the first and last of those files exist, ane neither are the culprit.

It looks like part of an Apache script that has been appended.

I've just seen that the env vars are OK under the sh shell, so it appears to be a bash shell issue, though I can't find where it's creeping in..

Eddie.

---

### Post by manimal on 2007-08-22
In my ~/.bashrc file, I have the line:

```
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
```

Does this line exist for you?  Is so, it means that the contents of this file are effectively being included in your bashrc file. So, check this file for your apache environment variables.  Also, the file   /etc/bash_completion uses files in the directory /etc/bash_completion.d so check this directory also.

---

### Post by ecomber on 2007-08-22
> **manimal said:**
> In my ~/.bashrc file, I have the line:

```
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
```

Does this line exist for you?  Is so, it means that the contents of this file are effectively being included in your bashrc file. So, check this file for your apache environment variables.  Also, the file   /etc/bash_completion uses files in the directory /etc/bash_completion.d so check this directory also.

Well, you spotted it. The file apache2.2-common was in /etc/bash_completion.d containing the script of which some appears in the 'set' command.

I deleted the file apache2.2-common, but even after reboot and creating a new user, the junk in the top message still appears in the new users account after issuing the 'set' command.

I'm at a bit of a loss and as it's causing problems (files with names form the script appearing in my user directory) I may be looking at a full install.

Eddie.

---

### Post by manimal on 2007-08-22
I removed the file "apache2.2-common" in "/etc/bash_completion.d" and it got rid of the environment variables for me.  Are you sure you deleted the file as root (or using "sudo")?  Of course, you could always just remove the "apache2.2-common" package with synaptic.

---

### Post by ecomber on 2007-08-23
Yes I removed it as root (it wouldn't allow me to without sudo).

In any case it's gone now.

 I need the apache package though. I'm sure the solution is there somewhere so I'll keep looking.

Eddie.

> **manimal said:**
> I removed the file "apache2.2-common" in "/etc/bash_completion.d" and it got rid of the environment variables for me.  Are you sure you deleted the file as root (or using "sudo")?  Of course, you could always just remove the "apache2.2-common" package with synaptic.

---

