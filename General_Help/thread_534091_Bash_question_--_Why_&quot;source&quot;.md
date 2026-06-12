---
title: "Bash question -- Why &quot;source&quot;?"
date: 2007-08-24
forum: General Help
---

### Post by john8791 on 2007-08-24
Can someone explain why an executable script like:

#!/bin/bash
ls -la

works just fine, but one like this:

#!/bin/bash
alias cls='clear'

doesn't work unless the script is run preceded by the word "source" or ". " first?

Thanks!

---

### Post by p_quarles on 2007-08-24
I'm not exactly sure what you mean by "like." Do you mean that this only happens when you try to set an alias with a script? Or are there other commands that require those prefaces as well? 

The best way to make an alias is to add it to the .bashrc file in your home directory.

---

### Post by john8791 on 2007-08-24
Sorry I wasn't very clear.  My aliases work fine at startup in my ~/.bash_aliases file.  My question is just technical curiosity.

If you put an alias command in a script and execute the script manually, the alias does not take.  If you execute the script manually by prefacing it by "source" or ".<space>" it does take.  In contrast, other commands such as "ls", etc "work" when executing the script.  Hope this makes more sense?

---

### Post by p_quarles on 2007-08-24
Yeah, I understand the question now. I don't have an answer, though :)

I wonder if it has something to do with the fact that the "alias" command directly (but temporarily) modifies the active user's profile. In bash, the "." usually refers to the current directory, so it's possible it's requiring this in order to make you specify a user. That's just a wild guess, though.

---

### Post by john8791 on 2007-08-24
Sounds reasonable.  I looked at the "source" man page but it didn't really give me enough info.

Thanks!

---

### Post by daveshields on 2007-08-24
When you run a shell script it is done in a new process. That process inherits the environment in which it is run, but changes made to that environment go away when the process completes.

So, for example, an alias defined within a shell script is only known while the script is running.

On the other hand, 'source' just tells the current shell to read the commands in the specified file and execute them just as though you had typed them in. So aliases defined within the sourced file are still effect when the shell finishes reading the file and returns to your terminal to continue processing. It's all done in the same process.

---

### Post by john8791 on 2007-08-24
> **daveshields said:**
> When you run a shell script it is done in a new process. That process inherits the environment in which it is run, but changes made to that environment go away when the process completes.

So, for example, an alias defined within a shell script is only known while the script is running.

On the other hand, 'source' just tells the current shell to read the commands in the specified file and execute them just as though you had typed them in. So aliases defined within the sourced file are still effect when the shell finishes reading the file and returns to your terminal to continue processing. It's all done in the same process.

Thanks!  Makes perfect sense now. :)

---

### Post by pibble on 2008-04-03
I found the information in this thread helpful, but I'm just wondering:

is there a way to force a script to behave as if you had sourced it when you just do a regular execution?

For instance some of adding a flag to the #!/bin/bash line that tells it to run it in the context of the current shell rather than starting a new one?

thanks
Preston

---

### Post by Rocket2DMn on 2008-04-03
> **pibble said:**
> I found the information in this thread helpful, but I'm just wondering:

is there a way to force a script to behave as if you had sourced it when you just do a regular execution?

For instance some of adding a flag to the #!/bin/bash line that tells it to run it in the context of the current shell rather than starting a new one?

thanks
Preston

I don't believe so, that is why we use "source" to run the script in the current environment.

---

### Post by pibble on 2008-04-04
> **pibble said:**
> is there a way to force a script to behave as if you had sourced it when you just do a regular execution?

For instance some of adding a flag to the #!/bin/bash line that tells it to run it in the context of the current shell rather than starting a new one?

What I ended up doing is creating an alias that sourced my file and accomplished the same effect.

alias myscript=' . /usr/local/bin/src.myscript $@'

---

