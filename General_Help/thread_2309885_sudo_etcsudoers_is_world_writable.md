---
title: "sudo: /etc/sudoers is world writable"
date: 2016-01-14
forum: General Help
---

### Post by jaanskumar on 2016-01-14
Friends, while using sudo command on installing mysql or any of the programs, I'm getting the following error

And also I tried installing as root user (su -), but still I'm facing the same problem.

Can anyone please help on this,


[B][COLOR=#263238][FONT=Helvetica Neue]root@sysfore1-Veriton-Series:/etc# sudo chmod 777 -R ./[/FONT][/COLOR]
[COLOR=#263238][FONT=Helvetica Neue]sudo: /etc/sudoers is world writable[/FONT][/COLOR]
[COLOR=#263238][FONT=Helvetica Neue]sudo: no valid sudoers sources found, quitting[/FONT][/COLOR]
[COLOR=#263238][FONT=Helvetica Neue]sudo: unable to initialize policy plugin[/FONT][/COLOR][/B]

---

### Post by matt_symes on 2016-01-14
> **jaanskumar said:**
> Friends, while using sudo command on installing mysql or any of the programs, I'm getting the following error

And also I tried installing as root user (su -), but still I'm facing the same problem.

Can anyone please help on this,

```
root@sysfore1-Veriton-Series:/etc# sudo chmod 777 -R ./
sudo: /etc/sudoers is world writable
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin
```

Did you run that *chmod* command on you root directory ? Why are you running *chmod 777* ?

That'll go a great way to destroying any security on your system and is very liable to break your system (as you seem to have succeeded in doing).

You have a world writable sudoers file. I suspect this is due to a *chmod 777* command that went wrong. It's very possible that you have other files that are world writable that should not be.

Reinstall your system.

Once you have completed that then post back and explain what you were trying to achieve with the *chmod* command and we'll try to help you find the correct way to do what you are trying to do.

*sudo chmod 777 ...* is almost never the correct way to achieve whatever it is you are trying to achieve.

Kind regards

---

### Post by furtom on 2016-01-14
This can happen. Usually some badly written software messes with the permissions. I wonder if you installed any propriety drivers lately?

Anyway, it's a simple fix. Try this to change it back:

> pkexec chmod 0440 /etc/sudoers

If that doesn't work for some reason, just use some boot media to get to a root shell and chmod from there.

---

### Post by matt_symes on 2016-01-14
Hi

> **furtom said:**
> This can happen. Usually some badly written software messes with the permissions. I wonder if you installed any propriety drivers lately?

Anyway, it's a simple fix. Try this to change it back:



If that doesn't work for some reason, just use some boot media to get to a root shell and chmod from there.

This is bad advice. 

Sorry furtom but it just is. 

You have no idea what is world writable on the OP's system. (files, sockets, logs, extra installed software, PPAs).

You don't even know if it's a desktop or server system.

The OP is obviously trying to run a *chmod 777* command on their system and has possibly ran one previously.

@OP. _Reinstall your system_

Kind regards

---

### Post by ajgreeny on 2016-01-14
Sorry to say it but I think matt_symes is correct, and with no sudo rights you would only be able to do any of this from recovery mode or a live system.

**DO NOT MESS WITH PERMISSIONS** on an operating system when you are not really sure what you are doing; the **/etc/sudoers** file is one of the most syntax and permissions sensitive files on your whole filesystem so you should not change anything related to that unless you know exactly what you're doing and how to reverse it if something goes wrong.

I suppose that as you are already facing a reinstallation, trying the chmod command suggested can not make matters worse but I'm not even sure exactly which files or folders will have been changed to world-readable by using that ```
sudo chmod 777 -R ./
``` command but I suspect many more than you think will have been changed.

---

### Post by furtom on 2016-01-14
Three things:
1. Perhaps I'm misreading it,  but I didn't think the OP actually chmod his whole system. If he did, of course that was a terrible idea and I stand corrected.  I'm still not sure if he did that, though. We need more info. 

2. If you guys thought my reply was intended as a rebuttal, that is not the case! I think we were writing at the same time. Had I read your reply before writing  my own, it would have been different. 

3. The more I think air about it, the less this makes sense. The OP knew enough to google chmod and su, but still thought 

chmod 777 -R ./ 

Would be a good idea? Dubious...

If the question is legit, I would still like more info before we go reinstalling, but I cam certainly see how you may be right. 

Or this may be just a troll. If so, we fell into it!

Best,

---

### Post by matt_symes on 2016-01-14
Thread moved to **General Help** as this is a support question.

@jaanskumar.

You are new to the forums and have posted your question in the wrong forum. 

I've moved your thread to the correct forum for your query.

Are you new to Linux and Ubuntu ?

And by the way, welcome to the forums :)

---

