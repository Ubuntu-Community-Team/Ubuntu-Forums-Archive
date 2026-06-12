---
title: "How to log on as superuser"
date: 2008-05-04
forum: General Help
---

### Post by labtek on 2008-05-04
Hello to the group and good day.

I'm presently exploring Ubuntu 8.04 on my bench computer.

I need to have "superuser" privileges to perform some functions in Konsole. I presume this is otherwise known as "root".

I feel that I should know how to do this but can't remember how. Rather than spend lots of time searching the forums, perhaps someone can enlighten me on this.

Many thanks.

---

### Post by tvtech on 2008-05-04
just use sudo in console and you'll be prompted for your password, or... open a root console  applications>system tools>root terminal

an addendum on ubuntu and root.  Although many linux distro's allow direct and relatively easy access to root this can pose some problems.  one as in windows root access can be dangerous changing the wrong thing can cripple your system. make sure you know what your doing before accessing it.  two.  ubuntu doesn't natively allow root priveledge access it allows user level access and grants those users based on their profiles super user access for limited amounts of time using the gksu or sudo commands, at which point you are prompted to enter your user password.  as long as you haven't changed your user permissions, you'll have full root access from the user profile you created when you installed by entering your password when prompted.  also being logged in as root opens you up to a number of vulnerabilities in the linux os security model.  This is one of the reasons windows xp and ealier had so many security holes becuase 99% of the time users are logged in as super user.   so leasing a brief root with the sudo or gksu commands at prompt or from the application starter, and then shutting down root access after that use is finished keeps your system much safer, as long as no one else knows your password.  it also makes server side attacks on linux systems much more difficult.  and also makes creating "bots"  that self install programs much harder to create as well.  this is one of the reasons mac osx is so hard to crack since it is now a BSD variant.  although mac leaves some unusual security holes that ubuntu does not.

---

### Post by Luke771 on 2008-05-04
Do you really want to login as root?
You shouldn't do that, it's a major security risk and there's no need to do it anyway.

Using sudo before a command line will run that line as root, and if you want to have write access by default on directories that are outside of your regular user's home dir, all you have to do is to change ownership of that directory and everything in it, making your user the owner instead of root. (DON'T do that on system directories. Use sudo intead)
The command line to do that is:
```

sudo chown <your-user> /path/to/directory -R
```

If you need a GUI file browser with super user access, run:

```

sudo nautilus
```

If you run KDE (Kubuntu) the line is:

```
sudo konqueror
```

Remember NOT to access the internet through Konqueror while in super user mode.
As an alternative, you may add a panel button or menu item that runs your file browser as root:
Right click on your panel > add custom launcher, name it something like 'root's file browser' and in the 'command line' field type:
```

gksu nautilus
```

Adding gksu before the command line in any button on menu iten will prompt you for password and  launch the app as root.
This is useful for some application that are launched as regular user but can't do anything or their changes aren't permanent because they're not running as root (examples: nvidia-settings and gparted)

OK, looks like now you have all you need to do whatever you may have to do without actually logging in as root.
You _still_ want to login as super user?
Alright then, but if mess it up, don't say that I didn't warn you: YOU SHOULD NOT do this:

-go to Main menu > system > administration > login window
-In the Login Window interface, click the second tab from the right: 'Security'
- check the checkbox marked 'allow _local_ administrator login'
(DON'T check 'allow _remote_ system administrator login'!!! Not even at gunpoint!)
- close Login Window
- open a terminal
- use this command line
```

sudo passwd root <root password>
```
- confirm password
- exit.

Now you should be able to login with username root and password <your root password>.
Once again: DON'T!
It's stupid and unnecessary.

---

### Post by ghost_ryder35 on 2008-05-04
> **labtek said:**
> Hello to the group and good day.
 
I'm presently exploring Ubuntu 8.04 on my bench computer.
 
I need to have "superuser" privileges to perform some functions in Konsole. I presume this is otherwise known as "root".
 
I feel that I should know how to do this but can't remember how. Rather than spend lots of time searching the forums, perhaps someone can enlighten me on this.
 
Many thanks.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by labtek on 2008-05-04
Hello again to the group.

Many thanks to those who posted replies. It's greatly appreciated. One of the many strengths of Linux is the forums.

Sudo worked fine- I used it before the command line that I was trying to run. It asked for my user password and it all went smoothly from there on. The command was executed perfectly.

Also good information on "running as root"- that was a bonus.

Have a great day one and all.

---

