---
title: "no color in console/ edgy"
date: 2006-11-25
forum: General Help
---

### Post by dalem on 2006-11-25
I have color in xterm and gterm so I know my bashrc file is colorizing the terminals correctly. But when I'm in the console, I only have black, white and grey colors, the grey being what would normally be colorized.

I worked with the guys on IRC in #bash and we tried all sorts of different commands and could get the console to output color in red, but were unable to get it co colorize for ls -l --color.

I tried removing gdm. The first time I input ls -l --color, the console displayed the colors correctly. Then when I boot Xwindows with the startx command and then returned to tty1 and killed X with CTL-C I was back to black white and grey in the console.

This is driving me nuts, can someone point me in the right direction? Thanks

---

### Post by po0f on 2006-11-25
dalem,

Post the output of:
```
$ **cat ~/.bash_profile**
```

---

### Post by dalem on 2006-11-26
> **po0f said:**
> dalem,

Post the output of:
```
$ **cat ~/.bash_profile**
```
dale@ubuntu:~$ $ *cat ~/.bash_profile*
bash: $: command not found

---

### Post by po0f on 2006-11-26
dalem,

The dollar sign represents your terminal prompt (*dale@ubuntu:~$* in your case) and isn't part of the command.  The command was in bold.  Also, where did the asterisks come from?

---

### Post by dalem on 2006-11-26
> **po0f said:**
> dalem,

Post the output of:
```
$ **cat ~/.bash_profile**
```
~$ *cat ~/.bash_profile*
bash: *cat: command not found

---

### Post by tomcheng76 on 2006-11-26
JUST TYPE
cat ~/.bash_profile

---

