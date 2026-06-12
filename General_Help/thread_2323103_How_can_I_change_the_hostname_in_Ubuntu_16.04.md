---
title: "How can I change the hostname in Ubuntu 16.04?"
date: 2016-05-02
forum: General Help
---

### Post by kate8 on 2016-05-02
Hi, I hope this hasn't been already been asked a 1000 times, but I can't work out how to change the hostname in Ubuntu 16.04. I'm not sure if it is the hostname I mean - I mean the name that appears in the terminal, i.e., 0000@1111 - I want to change the "0000" part. Tried sudo gedit /etc/hostname and sudo gedit /etc/hosts, hostname is registered as the one I want, but I've still got the "0000" name in the terminal. 

Tried sudo nano, nothing works there either. And yes I've rebooted. Gksudo doesn't work. 

Been googling around for over a week, already asked in several places, still can't find any solution that works. As I said, the host name is registered as the one I want, but it just doesn't show up in the terminal or directories. Am I able to change the name of the directory without deleting/moving all the files in it, or should I just scrap it and create a whole new account get my desired my desired name that way? It is kinda important, and I did not choose the existing name.

It's weird, every solution I've found or been told is really simple, but simply doesn't work for me. I must be doing something wrong, but I just can't work out what.

---

### Post by him610 on 2016-05-02
Unless I am mistaken the *0000* is your user name. 

You can create a new user account then transfer all of your files from the 0000 account to your newly created account.

---

### Post by kate8 on 2016-05-05
I have changed the username, that's the one I log in with etc. So changing the username will just change the login name, and the change won't extend to the name that appears in the terminal? 

Well, I guess I'll just have to create a new account, but it seems kinda flawed that it's not possible to actually change the username.

---

### Post by DuckHook on 2016-05-05
Welcome to the forums, kate8.

Below is a link to the process for changing your username properly. The problem with just creating another account is that, by default, your second identity does not have root elevation (sudo) privileges. If you then somehow delete your first account, you will end up locking yourself out of your system for any administrative tasks (like updates - yikes!). There are ways out of such a pickle, but they involve using a LiveUSB, etc and it's best to avoid such troubled waters.

[Here]("http://askubuntu.com/questions/558669/renaming-user-name") is the link to the proper way to change user name so that you retain your default opening identity (userid: 1000) and root elevation privileges. As you can see, it's a rather involved process for someone new to Linux/Ubuntu. If you get a step wrong, you may end up not being able to log in. If you have just installed your system, I would actually recommend that you simply reinstall, but this time choosing the name you want. It may take a bit longer, but is conceptually much easier.

---

### Post by Dennis N on 2016-05-05
> **kate8 said:**
> I have changed the username, that's the one I log in with etc. So changing the username will just change the login name, and the change won't extend to the name that appears in the terminal? 


To change hostname (name of your computer), two edits have to be made:

1) edit **[FONT=Courier New]/etc/hostname[/FONT]**
2) edit **[FONT=Courier New]/etc/hosts[/FONT]**

In each file, change the current hostname to the new choice and save. After making both changes, restart.

---

### Post by matt_symes on 2016-05-05
Hi

This command can be used to set the hostname.

```
hostname
```

Kind regards

---

### Post by DuckHook on 2016-05-05
> **Dennis N said:**
> To change hostname...

> **matt_symes said:**
> This command can be used to set the hostname...
I suspect OP is actually trying to change username and is using the term "hostname" when what she really means is "username". I'm assuming this from her stated desire to "change the 0000 part".

---

### Post by matt_symes on 2016-05-05
Hi

> **DuckHook said:**
> I suspect OP is actually trying to change username and is using the term "hostname" when what she really means is "username". I'm assuming this from her stated desire to "change the 0000 part".

If that's the case then i must stop speed reading posts :)

In any case, this can be used to change the user name

```
sudo usermod -l <new_name> <old_name>
```

That's a small L above.

From man usermod:

> -l, --login NEW_LOGIN
           The name of the user will be changed from LOGIN to NEW_LOGIN. Nothing else is changed. In particular, the user's home
           directory or mail spool should probably be renamed manually to reflect the new login name.


Kind regards

---

