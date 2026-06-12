---
title: "Ununtu 14.04 LTS Server (no gui) version (My choice)"
date: 2014-05-12
forum: General Help
---

### Post by microchipmatt on 2014-05-12
I need to activate the root password, for some reason, on 14.04 LTS Server, none of the regular methods I try work, I've tried:

sudo passwd -u root
sudo passwd root
(I then choose my passwd)

Ubuntu does not login....can someone tell me why this does not work in 14.04, and the method to login as the real root account? 

Thanks.

---

### Post by papibe on 2014-05-12
Hi microchipmatt. Welcome to the forum ):P

First of all, this is highly **[COLOR="#FF0000"]not[/COLOR]** recommended. In words of lazyPower at askubuntu (read more about it [here]("http://askubuntu.com/questions/16178/why-is-it-bad-to-login-as-root")):
> It defeats the security model that's been in place for years. Applications are meant to be run with non-administrative security (or as mere mortals) so you have to elevate their privileges to modify the underlying system. For example you wouldn't want that recent crash of Rhythmbox to wipe out your entire /usr directory due to a bug. Or that vulnerability that was just posted in ProFTPD to allow an attacker to gain a ROOT shell.

Its just good practice on any operating system to run your applications on a user level and leave administrative tasks to the root user, and only on a per-need basis.
For the most admin task you can run commands as root by using sudo. For a permanent root prompt you can also use:
```
sudo -i
```
Having said that, you already have taken the steps to enable the root account. Are you trying to login in a graphical desktop, or in text mode?

Regards.


P.S.1.: further reading about security, sudo and the root account: [Root and Sudo]("https://help.ubuntu.com/community/RootSudo").

P.S.2.: to disable again the root account run this:
```
sudo passwd -dl root
```

---

