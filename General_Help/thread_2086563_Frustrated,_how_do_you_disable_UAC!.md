---
title: "Frustrated, how do you disable UAC?!?"
date: 2012-11-21
forum: General Help
---

### Post by SoulofDeity on 2012-11-21
Using **Ubuntu 12.04 LTS**


What I'm trying to do:

[LIST]
[*]Disable request for authentication when installing or uninstalling programs
[/LIST]
What I'm **NOT** trying to do:

[LIST]
[*]Disable request for password when using sudo. I've already done this.
[/LIST]
What I don't care about:

[LIST]
[*]How 'unsecure' it is because 'someone can install stuff on my pc'. That's why there's a log out feature. If you don't want people installing **** on your account, log out. Not that it matters to me anyway, I'm the only one using my pc.
[*]How I might damage my pc typing the wrong instruction or something. Stupidity is stupidity. You're going to type it in anyway and having to type in a password to do it doesn't make it any safer.
[*]How it makes my computer susceptible to malicious software. Again, if you're stupid enough to run something you don't trust without a password, you'll be stupid enough to run it with one.
[/LIST]


I know I'm being blunt and seemingly rude, but after googling for several hours and listening to people say "I don't recommend doing this, but <insert wrong 'solution' here, usually disabling sudo for a usergroup or password login, which is completely unrelated to the question>", I'm pretty frustrated.   :confused:



I love ubuntu and don't want to look for alternatives, but I'm a very active user and having to type my password in to install or run applications is very irritating. If someone can tell me how to do this, that's be boss :P

---

### Post by drmrgd on 2012-11-21
I don't think you're going to get much help on this, let alone sympathy.  This is the core way the OS works and removing these security features is the equivalent of putting a gun in your mouth and saying nothing bad can happen as long as I never pull the trigger.

---

### Post by philinux on 2012-11-21
See this sticky from the security forum.

[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

---

### Post by SoulofDeity on 2012-11-21
> **drmrgd said:**
> I don't think you're going to get much help on this, let alone sympathy.  This is the core way the OS works and removing these security features is the equivalent of putting a gun in your mouth and saying nothing bad can happen as long as I never pull the trigger.

It's really more like already having the gun in your mouth with the authentication dialog being the words "are you sure you want to pull this trigger?" written in syrup on your forearm.

---

### Post by 2F4U on 2012-11-21
> That's why there's a log out feature. If you don't want people installing **** on your account, log out. 

You are not installing software in your account. You install software in the system so that this software can then be used also by other users.

> ot that it matters to me anyway, I'm the only one using my pc.

Unlike Windows, Linux has been designed as a multi-user system from the beginning. The actions you are referring to are meant to be done by an administrator. In other Linux distributions this would be the root account. If you have a root account, the system won't ask you for confirmation, but, of course, you have to login to that account once. Without a root account there needs to be some security in place that prevents unauthorized people from doing such things.

To be honest, I am enjoying this enhanced security very much, but I understand that others may not be in the same boat.

---

### Post by sgage on 2012-11-21
> **SoulofDeity said:**
> Using **Ubuntu 12.04 LTS**


What I'm trying to do:

[LIST]
[*]Disable request for authentication when installing or uninstalling programs
[/LIST]
What I'm **NOT** trying to do:

[LIST]
[*]Disable request for password when using sudo. I've already done this.
[/LIST]
What I don't care about:

[LIST]
[*]How 'unsecure' it is because 'someone can install stuff on my pc'. That's why there's a log out feature. If you don't want people installing **** on your account, log out. Not that it matters to me anyway, I'm the only one using my pc.
[*]How I might damage my pc typing the wrong instruction or something. Stupidity is stupidity. You're going to type it in anyway and having to type in a password to do it doesn't make it any safer.
[*]How it makes my computer susceptible to malicious software. Again, if you're stupid enough to run something you don't trust without a password, you'll be stupid enough to run it with one.
[/LIST]


I know I'm being blunt and seemingly rude, but after googling for several hours and listening to people say "I don't recommend doing this, but <insert wrong 'solution' here, usually disabling sudo for a usergroup or password login, which is completely unrelated to the question>", I'm pretty frustrated.   :confused:



I love ubuntu and don't want to look for alternatives, but I'm a very active user and having to type my password in to install or run applications is very irritating. If someone can tell me how to do this, that's be boss :P

If you don't care about security and making stupid mistakes, make your password something really, really easy to type. Soon you just won't even notice. If you REALLY don't care, make a root account and operate out of that. Good luck to you - you're gonna need it!  :KS

---

### Post by critin on 2012-11-21
Sure...use a one character password. That's about as easy as as quick as it comes.

Wondering what XP (in the title)  has to do with this question.

---

### Post by jlangvand on 2012-11-21
"sudo passwd root" creates a password for the root account, thus "activating" it. I don`t recommend this, of course :)

There are some setting under /etc/something where you can choose to display root in the login screen. Log in to your desktop as root, and you will never have to type your password after login. And it is like leaving your house without even closing the door behind you.

---

### Post by CharlesA on 2012-11-21
> **SoulofDeity said:**
> I love ubuntu and don't want to look for alternatives, but I'm a very active user and having to type my password in to install or run applications is very irritating. If someone can tell me how to do this, that's be boss :P

What application are you using that requires root access?

Unless you are installing applications every time you use your PC, inputting your password once isn't too bad tbh.

---

### Post by dannyboy79 on 2012-11-21
see post number 8 here: [http://ubuntuforums.org/showthread.php?t=1594986](http://ubuntuforums.org/showthread.php?t=1594986)

PS ANYONE READING THIS PLEASE FULLY UNDERSTAND YOUR SYSTEM IS COMPLETELY INSECURE BY DOING THIS!!!!!

---

### Post by Elfy on 2012-11-21
While you might not be worried about the state of your PC if you go ahead and disable these things - lots of people come here looking for help with their first visit to Linux.

We have to worry about what they might do - hence the forum's position.

Thread Closed.

---

