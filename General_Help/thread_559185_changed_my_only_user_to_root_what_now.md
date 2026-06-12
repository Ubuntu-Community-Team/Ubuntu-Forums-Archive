---
title: "changed my only user to root what now"
date: 2007-09-24
forum: General Help
---

### Post by jrmink on 2007-09-24
I cannot access any administrative apps I an error saying that I cannot run administrative apps 

while under root.  The only problem is I have no other users that are not root because I renamed 

myself root hoping to be able to always log in as root.  Any suggestions?

jrmink

---

### Post by jrmink on 2007-09-24
This is extremely important as I have work to do I cant be going and reinstalling ubuntu time after time because of these errors.

Help anyone?

---

### Post by Adramelech on 2007-09-24
you are not root, you should rename your user back.
to run administrative apps use the sudo command.

example:

sudo command-to-run-as-root

---

### Post by 3rdalbum on 2007-09-24
Reinstall Ubuntu.

It would probably be possible for an expert to repair the damage, but I don't think anyone would be able to talk you through it on the forums.

Logging in as root is a seriously bad idea, and it is *never* necessary. To get root permissions, you can preface your command with "sudo" for terminal programs or "gksudo" for graphical programs. For instance, if the command you want to run is "rm /var/apt/cache/*", you would type:

```
sudo rm /var/apt/cache/*
```

Or to bring up a root file browser:

```
gksudo nautilus
```

Alternatively, you can become root within the bounds of one terminal window:

```
sudo su
```

I hope this helps.

EDIT: If you can't waste time reinstalling Ubuntu whenever you fiddle around with the internals of your system, then either save your fiddling for a non-production machine, or try installing Ubuntu within a virtual machine program such as Virtualbox.

---

### Post by Adramelech on 2007-09-24
he is not root, I mean, he renamed his administrative user to root, but i think the user is still a sudoer so can be able to fix the problem with a renaming and using the sudo command

---

### Post by jrmink on 2007-09-24
Yea what the guy above me said

I renamed my username from jrmink to root so now I cant access things because it says im under root

But when I log in regularly im still using jrmink and then my password to login...

and no I dont have time to be reinstalling, i think there is a way around this I have to fix it somehow

Edit--

I also notice when I run groups in the terminal jrmink is a group and there are two users named jrmink...

---

### Post by Adramelech on 2007-09-24
what admin commands are you trying to run? please paste the error messages

---

### Post by jrmink on 2007-09-25
Any!  I cant run users and groups it says something about root access denied and how I cant run administrative programs while im under root.

Users and groups is the main program I need to run so that I can fix this.

Like I said before my username was jrmink then I changed it to root and now I messed it up.

It also seems I have two jrmink accounts somehow.

I need a solution one that involves a way to make a new user or something.

jrmink

---

### Post by jrmink on 2007-09-26
Resolved.

If this happens to anyone I would recommend you reinstall ubuntu, which is what I did.

---

### Post by muralpennies on 2007-09-26
jrmink, what command did you run or GUI did you use to rename your userid to "root"?  I'm not very familiar with Windows or MacIntosh, but is this something (renaming a userid to gain higher privileges) that's commonly done in those operating systems?

---

