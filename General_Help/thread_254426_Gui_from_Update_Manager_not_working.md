---
title: "Gui from Update Manager not working"
date: 2006-09-09
forum: General Help
---

### Post by jandi on 2006-09-09
Hi,

The gui for the update in manager in Ubuntu ceased to work. It just refuses to start, no error messages. I started having problems non stop after upgrading to Dapper.  I suspect something is messed up with permissions or sudoers, or something, but i have no idea where to start looking ](*,)

---

### Post by mssever on 2006-09-10
Open up a terminal and type
```
sudo update-manager
``` You should get some error messages in the terminal. Immediately after you get your prompt back (before you type any other command), type
```
echo $?
``` This will give you update-manager's exit status (which may or may not be helpful).

BTW: Great avatar!

---

### Post by jandi on 2006-09-10
Thanks!
Haha, this is odd.
From the command line I am able to start the update manager no problem.  I just get a warning before it starts:
/usr/lib/python2.4/site-packages/apt/__init__.py:17:FutureWarning: apt API not stable yet
warnings.warn(*apt API not stable yet*, FutureWarning).

But I can still not start it from the menu.  And actually, I'm unable to start the network manager, and even synaptic directly from the menu.

---

### Post by mssever on 2006-09-10
I get that same warning. Given that it's called a "FutureWarning," I'm guessing that everybody does, too.

Have you tried logging out and back in? It appears that something's messed up with your panels. Restarting them might fix them.

---

### Post by MattToner on 2006-09-10
i get the same thing, i just use terminal to update now

sudo aptitude update then sudo aptitude upgrade instead of update manager.

---

### Post by jandi on 2006-09-10
Restarted the computer a couple of times, and still get the same issue.

This is weird.

I guess I´ll have to resort to the terminal to update now.

---

### Post by jISh on 2006-09-10
Same problem, but I found the update manager slow and useless anyways and simply do a daily check with apt-get.

---

### Post by PriceChild on 2006-09-10
Could you try:```
gksudo update-manager
```please?

---

