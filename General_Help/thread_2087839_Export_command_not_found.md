---
title: "Export: command not found"
date: 2012-11-24
forum: General Help
---

### Post by TestUb on 2012-11-24
Hello.

This may seem like a dumb question, but I've been looking for an answer and I couldn't find a specific one. So, whenever I open the terminal, I get this:

```
´export: command not found
```What should I do to solve this?

---

### Post by steeldriver on 2012-11-24
Hello and welcome

That sounds like a typo in either your ~/.bashrc or possibly ~/.profile file - open 'em up (text editor or 'less' them on the command line) and have a look

---

### Post by gnusci on 2012-11-24
What is the output of your SHELL environment variable?

$ echo $SHELL

---

### Post by TestUb on 2012-11-24
> **gnusci said:**
> What is the output of your SHELL environment variable?

$ echo $SHELL
/bin/bash

---

### Post by llamabr on 2012-11-24
Strange.

Don't just paste the output.  Also copy/paste the entire thing, including what you type, and what is the output.  It's difficult to troubleshoot by only seeing the second part.

---

### Post by TestUb on 2012-11-25
> **llamabr said:**
> Strange.

Don't just paste the output.  Also copy/paste the entire thing, including what you type, and what is the output.  It's difficult to troubleshoot by only seeing the second part.
´export: command not found
bradley@ubuntu:~$ echo $SHELL
/bin/bash
bradley@ubuntu:~$

---

### Post by Habitual on 2012-11-25
```
grep export .bashrc -n
```
One of the hits should have the '[COLOR=Red]**´**[/COLOR]' symbol in the line.

---

### Post by llamabr on 2012-11-25
why are you typing that little ´ symbol?

---

### Post by oldos2er on 2012-11-25
> **TestUb said:**
> What should I do to solve this?

Can you post your .bashrc?

---

### Post by TestUb on 2012-11-25
> **oldos2er said:**
> Can you post your .bashrc?
```
# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi
´export PATH=/home/bradley/.cabal/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games´
```Maybe is there something wrong here?

---

### Post by TestUb on 2012-11-25
> **Habitual said:**
> ```
grep export .bashrc -n
```One of the hits should have the '[COLOR=Red]**´**[/COLOR]' symbol in the line.
This is what I got:

```
bradley@ubuntu:~$ grep export .bashrc -n
108:´export PATH=/home/bradley/.cabal/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games´

```

---

### Post by nothingspecial on 2012-11-25
It's the little tick thing just before export that is causing the problem. You need to edit your .bashrc and remove it.

---

### Post by oldos2er on 2012-11-25
Pretty sure the backtick "´" needs to be deleted from the end of that line too.

---

### Post by TestUb on 2012-11-25
So, do I just remove the "´" at the begging and at the end and then save it?

---

### Post by Habitual on 2012-11-26
> **TestUb said:**
> So, do I just remove the "´" at the begging and at the end and then save it?

Sort of,
```
vi +108 .bashrc
```remove [COLOR=Red]**`**[/COLOR] at beginning **and the end of **
**[COLOR=Red]'[/COLOR]**export PATH=/home/bradley/.cabal/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games[COLOR=Red][B]'
[COLOR=Black]
[/COLOR][/B][COLOR=Black]All that line needs to read is
[/COLOR][/COLOR]```
export  PATH=/home/bradley/.cabal/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/game
```

re-run terminal to see if error is gone.

---

### Post by rnerwein on 2012-11-26
> **TestUb said:**
> ```
# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi
´export PATH=/home/bradley/.cabal/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games´
```Maybe is there something wrong here?

the backtick in my terminal looks "[COLOR=Red] `[/COLOR] " and that looks different.
with [COLOR=Blue]'[/COLOR] export bla=blu [COLOR=Blue]'[/COLOR]
i get the same error ( in german)
export bla=blu: Befehl nicht gefunden.

---

### Post by Habitual on 2012-11-26
> **rnerwein said:**
> the backtick in my terminal looks "[COLOR=Red] `[/COLOR] " and that looks different.
with [COLOR=Blue]'[/COLOR] export bla=blu [COLOR=Blue]'[/COLOR]
i get the same error ( in german)
export bla=blu: Befehl nicht gefunden.

Bradley:
[COLOR=Red][COLOR=Black]All that line needs to read is
[/COLOR][/COLOR]```
export PATH=/home/bradley/.cabal/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/game
```Do NOT use ' or ` for this command anywhere in it's string|line.

Just ```
vi +108 .bashrc
``` press DD to delete the line, press O, or o (o or O, not zero) to open a new line and insert this snippet.
```
export  PATH=/home/bradley/.cabal/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/game
```save, exit, or exit with save and re-bash.

---

### Post by Habitual on 2012-11-26
> **TestUb said:**
> So, do I just remove the "´" at the begging and at the end and then save it?

yes.
Remove ticks at front and end of line 108.

---

### Post by TestUb on 2012-11-27
Thanks for the help. It is now SOLVED!

---

### Post by Habitual on 2012-11-28
Glad it worked out!

---

