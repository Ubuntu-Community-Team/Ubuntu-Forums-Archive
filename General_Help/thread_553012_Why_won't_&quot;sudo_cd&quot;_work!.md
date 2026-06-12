---
title: "Why won't &quot;sudo cd&quot; work?!"
date: 2007-09-17
forum: General Help
---

### Post by t0p on 2007-09-17
I was trying to move some music files from my cellphone to my pc using ubuntu rather than booting up XP.  I had to do it as root, and both the phone card and the music files have spaces in their names.  Of course, I could just initiate 2 nautilus sessions with gksudo and do a simple click n drop in gnome... but that didn't immediately occur to me... :neutral:

*Anyway...* I decided to do it on the command line.  I remembered about using \ to get bash to ignore spaces in file and directory names, and... Well look...

```
martinx@x-box:/media$ ls
cdrom  cdrom0  floppy  floppy0  PHONE  PHONE CARD  windows
martinx@x-box:/media$ file PHONE\ CARD
PHONE CARD: directory
martinx@x-box:/media$ cd PHONE\ CARD
bash: cd: PHONE CARD: Permission denied
martinx@x-box:/media$ sudo cd PHONE\ CARD
password:
sudo: cd: command not found
martinx@x-box:/media$ 
```

You can see that bash could identify PHONE CARD as a directory okay, right?  Wouldn't let me cd to it, permission problem.  So I try "sudo cd" - and it doesn't know what I'm on about!

Am I overlooking something glaringly obvious?  (If I am, please don't make the flames too hot!)

---

### Post by raul_ on 2007-09-17
What about 

"sudo su" and then

"cd whatever/you/want"

?

---

### Post by t0p on 2007-09-17
> What about

"sudo su" and then

"cd whatever/you/want"

?

Well yeah, I guess that'd work (I haven't actually tried it, cos I'm currently using the cellphone in question as a modem, and switching from *phone mode* to *file transfer mode* is a serious PITA).  Yeah, AFAICT your "sudo su" suggestion would work... but I figured "sudo cd..." would work too...

Now that I've actually given the matter a modicum of thought, I've figured out a few ways to achieve what I wanted to achieve (and what I *did* achieve, with a simple GUI click n drag.  What I want to know is:  [I]why[I] didn't the "sudo cd..." command work?  Is sudo not meant to work with cd and certain kinds of directories?  Is it a bug?  Am I stupid?

It's not important or anything... I'm just nosey^N^N^N^N^Ninquisitive.

---

### Post by AusIV4 on 2007-09-17
I think the reason sudo cd doesn't work is that if it did, an unprivileged user would end up in a privileged directory, then they couldn't do anything once they got there. If you have to use sudo for every command you use, you might as well sudo su and shorten each command.

---

### Post by mxg01 on 2007-09-17
'sudo cd' won't work because the cd command is built into the shell. So you are saying become root and then run this command. You become root and then the command after sudo is searched for but there is no cd command to find. 

I suppose you could use the 'sudo su' and then try your commands.

---

### Post by yota on 2007-09-17
> **t0p said:**
> 
Am I overlooking something glaringly obvious?  (If I am, please don't make the flames too hot!)

Ahem... there's indeed something that's getting overlooked:

cd is not a program (try to find it on the filesystem!), it's a bash builtin command.
So if you say 'sudo cd' sudo tries to launch the cd program (which doesn't exists) with elevated privileges and what you get is exactly "sudo: cd: command not found"

Most of the times big and obvious things are able to hide themselves better than small ones ;-)

---

### Post by t0p on 2007-09-17
Thanks for the explanations, folks.  Yeah, cd being a bash built-in command rather than a program - it all becomes clear once someone's pointed the glaringly obvious to me </humble>

What I felt most embarrassed about though, was the fact that I'd dropped to the command line *after* I'd given it a (wrong) go in the GUI.  It was only after I'd ground my teeth for a while, reading "sudo: cd: command not found" that it dawned on me I could use 2 gksudos and click and drop.

These little struggles are instructive though.  Because I've had cause to think about the problem, I've sussed out a few different ways to achieve my aim - to transfer the files from my phone to my pc.  In ubuntu.

I don't need to use the software Sony Ericsson supplied with the phone anymore.  That software ran on Windows.  That's one less reason to have XP on my hard drive.

---

