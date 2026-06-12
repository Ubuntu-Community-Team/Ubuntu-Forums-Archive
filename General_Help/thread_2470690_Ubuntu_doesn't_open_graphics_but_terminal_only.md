---
title: "Ubuntu doesn't open graphics but terminal only"
date: 2022-01-08
forum: General Help
---

### Post by kamdaou on 2022-01-08
Hello everyone,

I am facing a common problem but I am unable to solve it.
I was working on my computer yesterday and I wanted to delay its shutdown process, because it was working at this time. So I used shutdown command to delay it. But, at the first time, I used it with a short timer and instead of cancelling before typing another command, I typed again the command with another timer. It is just the uncommon thing that I did yesterday. But, waking up this morning to open it, I find that the graphic cannot be openned. I searched some same problems in some forums and it seems like I have to install nvidia, or configure it. But I realized also that my computer doesn't use nvidia, after typing a command that I saw in those forum. Any idea of how I can solve this problem please ?

---

### Post by KBar on 2022-01-08
Hello and welcome to ubuntuforums!

First of all, what version of Ubuntu are you using?

Secondly, could you please post the relevant parts of *~/.bash_history* or at least recall and tell us the exact commands you typed in?

If the graphical interface cannot be accessed at all, switch to a virtual terminal by a way of pressing these three keys in combination: _Ctrl_+_Alt_+_F1_. From there, you can read the contents of that file with:```
less ~/.bash_history
```Find the command that you ran and post it here. By default, _Ctrl_+_Alt_+_F7_ should let you get back to the graphical interface.

**Please, read and educate yourself before executing commands in the shell.**

---

### Post by kamdaou on 2022-01-08
Hello. Thank you.
I am using Ubuntu 18.04
I typed the command but it seems like commands I typed in the morning are not listed.
Anyway, kindly find in attachment a picture of the result.

---

### Post by KBar on 2022-01-08
There are some **autoremove** operations in there. Could you post the last entries in */var/log/apt/history.log* and */var/log/dpkg.log*?

I don't think uninstalling *python* should break the system, though I'm not particularly familiar with it.

---

### Post by Apanta on 2022-01-09
I had the same problem on ubuntu 18.04-gnome. I solved it by enabling auto login. Through supergrubdisk I started ubuntu18.04 and then enabled automatic login.

---

### Post by kamdaou on 2022-01-10
Hello, sorry for giving you information late. I thought I subscribe for email but not.
Oka, I attached these information.

---

### Post by KBar on 2022-01-10
You already showed us the bash command line history. 

There are some **autoremove** operations in there. Could you post the last entries in */var/log/apt/history.log* and */var/log/dpkg.log*?

---

### Post by kamdaou on 2022-01-10
It's attached right now I think.

---

### Post by kamdaou on 2022-01-10
Can you please give me a link that can help me to do it ?

---

