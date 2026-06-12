---
title: "Modifying the Command Prompt"
date: 2007-06-11
forum: General Help
---

### Post by SnakeByte29 on 2007-06-11
Whenever I start up the terminal, my current directory appears before the prompt (reminiscent of DOS). Is there a way to change this (from "user@PCname:directory" to "username@PCname")?

---

### Post by drs305 on 2007-06-11
```

PS1="\u@\H:"

```

I use a colon at the end but you can omit it or put in another character or symbol. The format is saved in ~/.bashrc  

here is a link to various options:
[http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html](http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html)

---

### Post by FryerFox on 2007-06-11
There is a file called .bashrc in your home direcory that is executed whenever you start a shell. The variable, PS1 contains your prompt.

Try checking out [this]("http://www.pantz.org/scripting/shell/colorterm.shtml") site for information on how to customize your prompt.

To make the prompt be user@pcname, change PS1 to
> PS1="\u@\H > "

---

### Post by SnakeByte29 on 2007-06-11
Thanks, that worked. :)

---

