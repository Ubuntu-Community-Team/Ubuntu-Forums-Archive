---
title: "command not found?"
date: 2013-01-06
forum: General Help
---

### Post by seacher on 2013-01-06
I copied a file from my jump drive into the file directory with the path 'usr/share/Surge-View'.

When I use the command line to invoke the GUI I get the message 'Surge command not found'

Anyone have any similar problems before or know a possible solution?

---

### Post by dcstar on 2013-01-06
> **seacher said:**
> I copied a file from my jump drive into the file directory with the path '**usr/share**/Surge-View'.

When I use the command line to invoke the GUI I get the message 'Surge command not found'

Anyone have any similar problems before or know a possible solution?

You do not put binaries in /usr/share. Put them in /usr/local/bin or somewhere more appropriate.

---

### Post by seacher on 2013-01-07
I tried that method but now I cannot even get to the file and get the message:

'bash: cd: /usr/local/bin/Surge-View: Permission denied'

I need some help.

---

### Post by steeldriver on 2013-01-07
it's a bit difficult to guess exactly what you're trying to do - but here's a good introduction to working with files and directories at the command line

[https://help.ubuntu.com/community/UsingTheTerminal#File_.26_Directory_Commands](https://help.ubuntu.com/community/UsingTheTerminal#File_.26_Directory_Commands)

---

### Post by ivotkl on 2013-01-07
Have you tried with sudo before the command you're trying to execute?

---

### Post by 3rdalbum on 2013-01-07
> **seacher said:**
> I tried that method but now I cannot even get to the file and get the message:

'bash: cd: /usr/local/bin/Surge-View: Permission denied'

I need some help.

Have you set the execute flag?

```
sudo chmod +x /usr/local/bin/Surge-View
```

---

### Post by Impavidus on 2013-01-07
> **ivotkl said:**
> Have you tried with sudo before the command you're trying to execute?
I wouldn't execute anything except the simplest tools and maintenance commands with sudo, certainly not something manually installed that you haven't written yourself. You give the program the right to destroy your system. (But I don't know, there may even be a saveguard against that with sudo simply refusing to execute those commands as root.)

Make sure everyone has the right to execute your command. Check with **ls -l** There should be an x in the last column for access flags. For details: **man chmod** and **man ls**.

---

### Post by oldos2er on 2013-01-07
> **seacher said:**
> I copied a file from my jump drive into the file directory with the path 'usr/share/Surge-View'.


What is "Surge-View' and from where may one obtain it?

---

### Post by seacher on 2013-01-07
Yes, I tried sudo and it simply states 'cd: command not found'

I will try to set permissions now.

Surge-View is a program that allows me to interface with the Wireless Sensor Network from Memsic.  So if you want a Surge-View you probably need to get in touch with Memsic:)

---

### Post by rnerwein on 2013-01-07
> **seacher said:**
> Yes, I tried sudo and it simply states 'cd: command not found'

I will try to set permissions now.

Surge-View is a program that allows me to interface with the Wireless Sensor Network from Memsic.  So if you want a Surge-View you probably need to get in touch with Memsic:)
hi
"cd" isn't a command it's a shell build in.
but some more questions:
is Surge-View a directory --> post the output of ls -lda
if Surge-View is a directory post the output of the executable inside.
i guess the x-bit is missing
cheers

---

### Post by seacher on 2013-01-07
This is more involved than I believe it should be.

Is there a simpler way to install a program from a CD-ROM onto a laptop without a CD drive?

---

### Post by oldos2er on 2013-01-07
I see this is the third thread you've started with essentially the same issue. In the future please keep one question to one thread.

Is Surge-View Windows software?

---

### Post by seacher on 2013-01-07
So I need to keep one task per thread or post a new thread with each issue I encounter through the task?  

Surge-View is licensed by Sun Microsystems, Inc.

I have been fairly thrown into using the command line in Linux, until 5 months ago I didn't even know Ubuntu existed.  

Is there a better way to do what I am doing with Ubuntu?

---

### Post by jerome1232 on 2013-01-07
We can't know unless you give us more info.

Is this a Linux executable you're trying to install? Did it come with any setup instructions? Is this a Windows executable?

Can you post results from the requested commands?

```
ll /usr/local/bin/Surge-View
```

---

### Post by seacher on 2013-01-07
I have instructions for set-up but they are for Windows systems only.

The results I get from the command 'cd /usr/local/bin/Surge-View' when I enter it into the command line is:
'bash: cd: /usr/local/bin/Surge-View: Permission denied'

---

### Post by jerome1232 on 2013-01-07
I meant the one I posted above, in the "code" box.

---

### Post by seacher on 2013-01-07
I get the message '11 command not found'

---

### Post by seacher on 2013-01-07
And because I can't tell if those are el's or ones the other command says 
'ls: cannot open directory /usr/local/bin/Surge-View: Permission denied'

---

### Post by oldos2er on 2013-01-07
> **seacher said:**
> So I need to keep one task per thread or post a new thread with each issue I encounter through the task?

Let's just keep it all in this thread for now.  

> **seacher said:**
> Surge-View is licensed by Sun Microsystems, Inc.

Ok, but we need to know whether the software you're trying to install and run is meant for Windows, or Linux. I asked because usually when beginners talk about trying to run a program from a CD, it's Windows software (which won't run natively on Linux).

> **seacher said:**
> Is there a better way to do what I am doing with Ubuntu?

Possibly; we don't have enough information yet to determine that.

Btw, it's easiest to copy and paste commands given in "code:" boxes, fewer mistakes that way.

---

### Post by seacher on 2013-01-07
Thanks oldos2er.

I will keep my post confined to this digital box.

How would I go about finding if the program is meant for Windows or Linux?

---

### Post by dodo3773 on 2013-01-08
> **seacher said:**
> I get the message '11 command not found'

That's because jerome1232 was asking you for the output from the "ll" command not the "11" command (the latter doesn't exist that I know of). 

Also, I agree that you may be making too hard work of something that is probably simpler. I cannot think of any reason you could not execute this application from your home folder for starters.

---

### Post by Cheesemill on 2013-01-08
If this is the software that you're trying to install then it's written for Windows, not Linux. You are trying to run it on an OS is wasn't designed for working on.
My advice would be to install it on a Windows machine instead.

[http://www.willow.co.uk/html/software.html](http://www.willow.co.uk/html/software.html)

---

### Post by oldos2er on 2013-01-08
> **seacher said:**
> How would I go about finding if the program is meant for Windows or Linux?

Where did you get the CD from? Is anything printed on it? Can you look at the CD contents with a graphical file manager? 

Which version of Ubuntu are you using?

---

### Post by piratebill on 2013-01-08
> **seacher said:**
> How would I go about finding if the program is meant for Windows or Linux?

Does the file extension end in .exe or .msi?

---

