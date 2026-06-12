---
title: "bash variable substitution"
date: 2007-02-04
forum: General Help
---

### Post by bamba on 2007-02-04
Hi,

i have the following problem. 
I want to work with variables in the cd command:
e.g.
$ export MUS=/mm/mp3/mus
then I want to extend the variable with the TAB
$ cd $MUS
The result is 
$ cd \$MUS
I want the following result 
$cd /mm/mp3/mus/
I know this feature from other unix and linux systems

i have already enabled the lines in the files /etc/bash.bashrc and ~/.bashrc:
# enable bash completion in interactive shells
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

Thanks

---

