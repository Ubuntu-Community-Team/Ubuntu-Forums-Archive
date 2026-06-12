---
title: "Misbehaving Bash Prompt"
date: 2012-11-06
forum: General Help
---

### Post by Randy Schilling on 2012-11-06
I added this command to my root  .bashrc file to add color to my prompt
and to simplify its path portion  to the lowest level directory,
```
export PS1="\e[1;31m\u@\h:\W\$\e[m " 
```
and my bash prompt comes up ending with $ when I expected #.
Also, occasionally, when I enter a command, part of that command
becomes part of my prompt!
If the following is a prompt and command,
```
prompt$ command
```then my prompt might come back as
```
prompt$ com
```What's causing this strange behavior? 
Please let me know if you need to see more of my .bashrc file.

Thanks for your help and grateful for this forum, Randy

---

### Post by 2F4U on 2012-11-06
It may be a copy/paste problem, but as far as I know, the double quotes should be replaced by single quotes. This site has a nice overview of how to design bash prompts:

[https://wiki.archlinux.org/index.php/Color_Bash_Prompt#Basic_prompts](https://wiki.archlinux.org/index.php/Color_Bash_Prompt#Basic_prompts)

---

### Post by codemaniac on 2012-11-06
The below section might be informative for you in /etc/profile
```

if [ "$PS1" ]; then
  if [ "$BASH" ] && [ "$BASH" != "/bin/sh" ]; then
    # The file bash.bashrc already sets the default PS1.
    # PS1='\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
      . /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi
```

---

### Post by Randy Schilling on 2012-11-06
Thanks, both of you.

---

