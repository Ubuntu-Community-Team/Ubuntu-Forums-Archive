---
title: "Sending a command to a remote Ubuntu box to run a bash script"
date: 2018-01-21
forum: General Help
---

### Post by Pandee on 2018-01-21
Hello!

I need some help finding an app or step to achieve my goal on Ubuntu 14.04

I am trying to send a command to a remote Ubuntu box to run a command in a certain terminal  or via bash (Does that make sense?) 

I know one part I can achieve this with the screen. So I run (Correct me I am wrong)

screen -S mySession[HR][/HR]Then a bash script will send the following 

 

screen -S mySession -X ./command (echo -ne '\015')[HR][/HR]

But before I do that, I need to find a way to execute this script remotely. I know i can use SSH..

But what I'm looking for is a way to execute this with an app (perhaps?) with a certain credentials not relevant to a superuser and at the same time make it so its the only script that can be run. 

Any ideas?

---

### Post by TheFu on 2018-01-22
Use ssh.  It is all possible. Just transfer the ssh-key into the userid you want running the command.  If you only want 1 command to be possible, then setup the config file on the ssh connection (remote side) to only allow 1 command.  This is how github works.  Lots of how-tos exist for it.

Why are you using X11forward?  Is this a GUI application?  If so, then the local machine must have an X11 server that accepts X-events from the remote X/client process.

---

### Post by Pandee on 2018-01-23
Hey TheFu! Thanks for your input.

Could you tell me the keywords so i can google these things? Or link them here so i can learn?

---

### Post by TheFu on 2018-01-23
[http://shop.oreilly.com/product/9780596008956.do](http://shop.oreilly.com/product/9780596008956.do) is one source.
[https://www.amazon.com/SSH-Secure-Shell-Definitive-Guide/dp/0596008953](https://www.amazon.com/SSH-Secure-Shell-Definitive-Guide/dp/0596008953) is another.
and there are always the manpages which are already on your Linux machine.  I learn something new about ssh every time I re-re-read the manpage.
[https://en.wikibooks.org/wiki/OpenSSH](https://en.wikibooks.org/wiki/OpenSSH) is another.

There are thousands of ssh how-to/tips/tricks guides.  Use those in your googles.
```

$ man -k  ssh 
```
will show all the manpages already on your system for all the little parts to ssh. Mine has 206 results.

man ssh
man ssh_config
man sshd_config
are some of the most interesting.

---

### Post by dragonfly41 on 2018-01-23
I know that SSH is the recommended method
But I thought I might add this which I found recently
and works in my development setup ...
[URL="http://https://github.com/krishnasrinivas/wetty"]
https://github.com/krishnasrinivas/wetty[/URL]

This requires node to be installed and also uses SSH.

The twist is that the shell appears in the local browser.

---

### Post by TheFu on 2018-01-23
Yep. There are 20 other web-server front-ends to a shell.  Just because something is possible, that doesn't make it a good idea for 99.999% of the situations.

Unix/Linux is really flexible.  There are usually 50-500 different ways to solve any problem.  Most of those methods are bad choices for performance, complexity, security reasons.  I like to use my "smell test" for solutions and ask - "does this smell funny?" Everyone has different smell sensitivity.  

Think about all the parts, how each part connects for the solution, and what other, external things are required for each part to work.  How does each of those things "smell?"  Good, tight, secure?  Excellent.  Or perhaps they smell like a garbage bin outside a restaurant after a very hot day?

And never forget that new is the enemy of stable/secure.  Only time can provide any assurance that something is secure.

And back to the OPs question - I googled "ssh allow 1 command" and got lots of results.
[https://access.redhat.com/solutions/65822](https://access.redhat.com/solutions/65822) - this is about restricted shells inside a chroot environment. Good layer of security to start.
[https://research.kudelskisecurity.com/2013/05/14/restrict-ssh-logins-to-a-single-command/](https://research.kudelskisecurity.com/2013/05/14/restrict-ssh-logins-to-a-single-command/) is about allowing 1 command for ssh connections. This is handy for allowing a backup server to "pull" backups.  "push" backups are a security failure, since every client system has access to the backup server(s) that way. If the backup server "pulls" from each client, then only 1 server has that access. But all it can run is "backup pull software" on each remote system. 

The same idea can be used to allow 1 command to be run or to create a secured-by-ssh "jump" server between different networks.

But I might be completely missing the OPs real question.

---

### Post by dragonfly41 on 2018-01-23
Solid advice, TheFu.
What are your thoughts on using Ansible?

**[COLOR=#b22222][Later edit][/COLOR]**

I have learned from here that a &#8220;single command&#8221; can be restricted by using ~/.ssh/authorized_keys file ...

[https://serverfault.com/questions/407497/how-do-i-configure-sshd-to-permit-a-single-command-without-giving-full-login-ac](https://serverfault.com/questions/407497/how-do-i-configure-sshd-to-permit-a-single-command-without-giving-full-login-ac)

---

### Post by TheFu on 2018-01-23
> **dragonfly41 said:**
> Solid advice, TheFu.
What are your thoughts on using Ansible?

**[COLOR=#b22222][Later edit][/COLOR]**

I have learned from here that a “single command” can be restricted by using ~/.ssh/authorized_keys file ...

[https://serverfault.com/questions/407497/how-do-i-configure-sshd-to-permit-a-single-command-without-giving-full-login-ac](https://serverfault.com/questions/407497/how-do-i-configure-sshd-to-permit-a-single-command-without-giving-full-login-ac)

Be careful with stackexchange family of websites answers.  Actually, being careful with answers from anyone is a good idea. Google isn't always a good thing for answers, especially when someone is really new.  Often, the answers are for a version that has a different method than what you are running today. Since 2012, networking has drastically changed in Linux.  Prior to 2012, we'd used the same methods since the beginning - they worked, but were less than friendly for new people.  

The same applies to how systems startup. Since 15.10, that has been completely changed.  For about 5 years prior, Ubuntu used Upstart and before that all Linux systems used "init".  Some systems (mostly unpopular) still use init for startup management.

The same applies to 17.10 and later for how the underlying GUI works.  17.10 swapped out X11 for Wayland.  X11 has been used for 30+ yrs in the Unix world and since 1992 for Linux. It is well understood, but definitely had some security and performance problems that most people didn't need.  X11 is part of my daily workflow. I cannot do my job with Wayland, period.  Lots of programs haven't been modified to work with Wayland - things like screen capture and any sort of remote GUI stuff is broke.  Those things will be fixed, but it will take time.  X11 used to crash daily in the early 1990s and that was after 10 yrs of development.  I'm hopeful Wayland will be better, faster, and support network-based GUI stuff that I need.

I use ansible. Don't see how that is relevant to this question.  Best to open a new question.

---

### Post by Pandee on 2018-01-25
Thanks for the input guys! I'm going through each one carefully.

---

### Post by TheFu on 2018-01-26
14.04 support ends in about a year, so really it is time to move (or start fresh) on 16.04.

---

