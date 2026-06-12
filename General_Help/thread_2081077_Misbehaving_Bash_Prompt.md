---
title: "Misbehaving Bash Prompt"
date: 2012-11-05
forum: General Help
---

### Post by Randy Schilling on 2012-11-05
I added this command to my .bashrc file to add color to my prompt
and to simplify its path portion  to the lowest level directory,
```
`PS1='\e[1;31m\u@\h:\W\$\e[m ' 
```and my bash prompt comes up as expected.
But occasionally, when I enter a command, part of that command
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

### Post by 28c64 on 2012-11-05
Try this instead.

```

export "PS1='\e[1;31m\u@\h:\W\$\e[m "

```

---

### Post by Randy Schilling on 2012-11-05
Yes, thanks thanks thanks!

---

