---
title: "How can I create aliases that can be run without sudo?"
date: 2020-06-03
forum: General Help
---

### Post by peb-cak on 2020-06-03
Hi,

I would like to make some aliases for command lines that are normally run with sudo. I would like to be able to run them without having to type my password all the time. I have been searching the internet and I have found mentions of editing /etc/sudoers and so on. I thought I better come here and ask for help than doing som faulty things damaging my system.

I appreciate much your help and advice,

---

### Post by HermanAB on 2020-06-03
Read up on SUID Root.

---

### Post by TheFu on 2020-06-03
There are lots of opinions on this and many security topics. 

I wouldn't ever make any script suid-root.  Interpreters often have methods to pass commands through stdin or environment variables, so someone could take advantage of that with a script.  A properly written C program can be secure enough for setuid, if any external commands it calls are carefully considered and hard-coded. Never trust the PATH. NEVER TRUST THE PATH.

To have specific programs, run by a specific userid, without a password prompt by sudo, there are examples in the sudoers beautiful manpage.  The sudoers manpage is one of the most complete, easiest to understand manpages out there.  It is possible to limit the options allowed for commands too.

```
Host_Alias      CDROM = orion, perseus, hercules
pete             CDROM = NOPASSWD: /sbin/umount /CDROM,/sbin/mount -o nosuid\,nodev /dev/cd0a /CDROM
```

That would allow userid 'pete', to **mount** and **umount** the cdrom on hosts orion, perseus, hercules - without any password.

Additionally, most uses online are about running as root, but sudoers can allow userids to run specific commands as other userids too, with or without passwords, with options limited or not.  For many users, making a little shell script that has the exact command(s) they can run makes the admin's life easier.  In a prior job, I setup some printing sudoer files that were placed on over 150 servers to control printing to over 6,000 printers.  Rather than have queue management setup for every userid and each specific printer, we did 1 user and the 15 different models of printers.  Today, I'd do it differently, but at the time, it was the best, available, option to feed into the different queues at hundreds of offices.

---

### Post by peb-cak on 2020-06-04
Thank you HermanAB and TheFu for your replies!

> **TheFu said:**
> 

To have specific programs, run by a specific userid, without a password prompt by sudo, there are examples in the sudoers beautiful manpage.  The sudoers manpage is one of the most complete, easiest to understand manpages out there.  It is possible to limit the options allowed for commands too.

```
Host_Alias      CDROM = orion, perseus, hercules
pete             CDROM = NOPASSWD: /sbin/umount /CDROM,/sbin/mount -o nosuid\,nodev /dev/cd0a /CDROM
```


That would allow userid 'pete', to **mount** and **umount** the cdrom on hosts orion, perseus, hercules - without any password.


Additionally, most uses online are about running as root, but sudoers can allow userids to run specific commands as other userids too, with or without passwords, with options limited or not.  For many users, making a little shell script that has the exact command(s) they can run makes the admin's life easier..


I think what you are suggesting, TheFu, is more aligned with what I had in mind. I will look into the man page for sudoers and see if I can work it out by myself. Otherwise I would appreciate to get some more help if I run to some obstacles. 

Just some more questions, is it possible to define aliases systemwide? Is it in /etc/bash.bashrc that they should be defined? If so where in that file I put them?

Thanks again!

---

### Post by HermanAB on 2020-06-04
Some things in Linux/BSD are set to be super secure for servers and untrained users and don't make much sense on intelligent user machines.  On my personal and company engineering machines, we set all the network utilities to SUID Root.  That allows the user to easily configure the ethernet ports and is very helpful.

This also means that any network configuration script can then call those utilities without any ado.

---

### Post by TheFu on 2020-06-04
> **peb-cak said:**
>  Just some more questions, is it possible to define aliases systemwide? Is it in /etc/bash.bashrc that they should be defined? If so where in that file I put them?

There are things that can be done and there are things that shouldn't be done.  Unix system philosophy is about allowing as much power to the end-users as possible, without risking security.  It is up to the admin team to decide what makes sense for their users and security risk management.

aliases are a specific type of solution. There is no default built-in way that an admin can change 1 file and all users magically have those changes immediately or even at next login.  You can setup a template that all new users get with aliases, if you like. I'd consider this bad form, since configuring my initialization files for my likes and dislikes is one of the first things I do.  That is very personal.  Another person probably wouldn't want some of my aliases and those aliases can break existing scripts if run from an interactive prompt, but won't work with used in scripts invoked via cron.

Usually, when I want to make a command available for everyone on a system, I'll make a little script and drop it into /usr/local/bin/ .  This is almost always in the PATH for everyone, but only admins can modify those files. Much safer.  But if it is a script and needs some sudo capability, I'd want to limit who can run it to only the group of users which the sudoers specifically allow the commands necessary with the necessary options to be allowed.

---

### Post by peb-cak on 2020-06-04
> **TheFu said:**
> 
Usually, when I want to make a command available for everyone on a system, I'll make a little script and drop it into /usr/local/bin/ .  This is almost always in the PATH for everyone, but only admins can modify those files. Much safer.  But if it is a script and needs some sudo capability, I'd want to limit who can run it to only the group of users which the sudoers specifically allow the commands necessary with the necessary options to be allowed.

Thanks again for your reply and the explanation!
 
I have to admit that, even though I have used Linux on and off for some time, most of its inner working is still opaque to me. I might be asking obvious and perhaps sometimes silly questions, so I hope you all will bear with me. Now I understand much better after your explanation what the proper course of action should for doing what I had in mind. 

Thanks again!

---

### Post by ActionParsnip on 2020-06-05
The sudoers file is universal. You can make groups of commands and groups of users then give the users access to run ONLY those commands using sudo. The rest will be denied. Sudo can be very granular, down to specific commands. Your first user can run any command with sudo but you can allow trusted users to run certain commands using sudo (Like allowing web devs to restart their services and such). Very handy in delegating some control.

---

