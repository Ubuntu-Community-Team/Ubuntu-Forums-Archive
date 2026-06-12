---
title: "How to change the command prompt message?"
date: 2008-07-05
forum: General Help
---

### Post by george9233 on 2008-07-05
I would really like to change the prompt message of the terminal to something like:
```

12:43 /some/directory $

```is there a way to do it?

Or is there a way to change the default prompt message to anything you want?

Thanks.

---

### Post by pyrofreek_9 on 2008-07-05
You can change the prompt to just about anything you want!
Check out the how-to [here]("http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html") for details.
I think you'd be looking for something like:
PS1='\A \w \$ '
in your ~/.bashrc file (if you have one already) or in the one he mentions in the how-to :)

---

### Post by brian_p on 2008-07-05
> **george9233 said:**
> I would really like to change the prompt message of the terminal to something like:
```

12:43 /some/directory $

```is there a way to do it?

Or is there a way to change the default prompt message to anything you want?

Thanks.

The PROMPTING section in man bash is basically what you want. Googling 'bash prompt change' should bring up tons of information.

---

### Post by lswb on 2008-07-05
I can't tell you the exact commands to get the prompt you want, but take a look at the .bashrc file in your home directory to see where the prompt is set. If the 12:43 refers to the time of day, some variation of the "date" command could do it.

---

### Post by george9233 on 2008-07-05
> **pyrofreek_9 said:**
> You can change the prompt to just about anything you want!
Check out the how-to [here]("http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html") for details.
I think you'd be looking for something like:
PS1='\A \w \$ '
in your ~/.bashrc file (if you have one already) or in the one he mentions in the how-to :)
Thanks for your useful link. Now I know how to do it.

And I did check out the man page of bash, it's also very helpful.

---

