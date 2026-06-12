---
title: "Run command on Ubuntu server from windows computer"
date: 2014-06-05
forum: General Help
---

### Post by Cool_Javelin on 2014-06-05
Hi:

I would like to run a command on my Linux box from a batch file on my WinXP machine.

Specifically, I want to be able to IM my windows desktop from my iPhone, then run a command on my Linux box.

Currently:
On Linux, I have a crontab that runs each minute, checks for the existence of a file in the home directory, then parses that file and does something.
On Windows, I have a batch file that checks my IM logs, and if proper conditions are met, creates a file on the Linux server.

I would rather just be able to send a command directly to the Linux box for execution without bothering with intermediate files and parsers and such.

I have SSH installed, and can PUTTY in from windows, I don't know if that helps.

Is there some apt-get package I can install that will help with this, or can Ubuntu handle directly?

Ubuntu machine = Ubuntu server 12.04.2 LTS (headless and no GUI)
Windows machine = WinXP (SP3)

Any ideas?

Thanks, Mark.

---

### Post by Cool_Javelin on 2014-06-05
OK, never mind, I found the answer.

I can run a command on the windows machine called plink (installed with putty on windows.)

It runs a command on the Linux machine.

I am happy.

Mark.

---

