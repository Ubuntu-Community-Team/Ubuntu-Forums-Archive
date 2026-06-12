---
title: "[SOLVED] Unable to lock the administration directory (/var/lib/dpkg/), is another pro"
date: 2007-08-07
forum: General Help
---

### Post by DougieFresh4U on 2007-08-07
How do I unlock as it says this:

[B]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
dougie@DougiesLeanMachine:~$ ps -e | grep -e apt -e adept | grep -v grep
12816 ?        00:09:52 aptitude
dougie@DougiesLeanMachine:~$[/B] 

I do not have any thing open. I did do updates a while ago. Is there some code to use in terminal to shut aptitude down? I don't want to reboot as It might "Break" and I don't want to take that risk today  :)

---

### Post by dreadlord_chris on 2007-08-07
if you're sure that no apt/adept/dpkg processes are running:
```

sudo rm /var/lib/dpkg/lock

```
Should take care of your little problem...

---

### Post by DougieFresh4U on 2007-08-07
> **dreadlord_chris said:**
> if you're sure that no apt/adept/dpkg processes are running:
```

sudo rm /var/lib/dpkg/lock

```
Should take care of your little problem...

Thank you very much. All is good now :)

---

### Post by Neobuntu on 2007-08-14
When all package managers are indeed closed. I suspect a bug or a problem when closing a terminal window that WAS running one of the many package management programs and then abruptly closed (that is a guess). I've run into this, to often for comfort. It is not a newbie encouragement.

 sudo rm /var/lib/dpkg/lock

...did NOT work.

>  sudo killall apt-get

...does work IF apt-get was the manager you were running. Else you may need to issue an...

>  sudo killall aptitude

...or what ever you were running. This worked for me.

This (in context) is all so that one doesn't have to reboot to solve the problem.

I am not certain I have defined the problem absolutely but this works.

---

