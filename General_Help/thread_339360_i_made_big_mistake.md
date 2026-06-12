---
title: "i made big mistake"
date: 2007-01-15
forum: General Help
---

### Post by bahrain on 2007-01-15
because i'm new to ubuntu, i thoght that if i change ( home/myname ) to ( root ) in users and groups i will be like "root", but now i can't login after restarted my computer!!!

what can i do?  :(

---

### Post by taurus on 2007-01-15
Boot into recovery mode from GRUB menu and paste the output of these two commands here.

```
cat /etc/hostname
cat /etc/hosts
```

---

### Post by bahrain on 2007-01-15
> cat /etc/hostname
jaffar-desktop
> cat /etc/hosts
127.0.0.1 localhost
127.0.1.1 jaffar-desktop

---

### Post by taurus on 2007-01-15
What's your login name then?  Assuming it's **bahrain**, run (from the recovery mode)

```
chown -R **bahrain**:**bahrain** /home/root
ls -la /home
```
Paste the output of the last command here!

---

### Post by jocko on 2007-01-15
> **bahrain said:**
> because i'm new to ubuntu, i thoght that if i change ( home/myname ) to ( root ) in users and groups i will be like "root", but now i can't login after restarted my computer!!!

what can i do?  :(

I'm not sure exactly what you mean. Do you mean that you changed owner and permission of the /home/[COLOR=Red]username[/COLOR] folder so that it now belongs to root?

In that case this would help (change "[COLOR=Red]username[/COLOR]" to whatever login you have):
```
sudo chown -R [COLOR=Red]username[/COLOR]:[COLOR=Red]username[/COLOR] /home/username/
```

---

### Post by bahrain on 2007-01-15
no, my login name is jaffar

---

### Post by bahrain on 2007-01-15
> **jocko said:**
> I'm not sure exactly what you mean. Do you mean that you changed owner and permission of the /home/username folder so that it now belongs to root?
no i change this directory to "/root" like what it is in root user

---

### Post by taurus on 2007-01-15
Then use jaffar!  ](*,) 

```

chown -R **jaffar**:**jaffar** /home/root
ls -la /home

```

---

### Post by taurus on 2007-01-15
What's the output of this command then?

```
ls -la /home
```

---

### Post by phossal on 2007-01-15
> **taurus said:**
> Then use jaffar!  ](*,) 

Are you sure you've understood his question?

[edit] Some questions really shouldn't be answered. Everyone (who deserves it) should have to go through the painful process of losing all their hard work and data, and having to completely reinstall their OS, before the mods jump in to rescue them. Those experiences teach a person foresight and prudence, if they're capable of learning it. :p

---

### Post by jocko on 2007-01-15
> **bahrain said:**
> no i change this directory to "/root" like what it is in root user

So you **renamed** your /home/jaffar/ directory to /home/root?
Or did you **move** /home/jaffar to /root?

---

### Post by bahrain on 2007-01-15
> **jocko said:**
> So you **renamed** your /home/jaffar/ directory to /home/root?
i renamed it to "/root"only, and i did that from "users and groups"

---

### Post by Denn1s on 2007-01-15
can u log in as root and change it back?

---

### Post by bahrain on 2007-01-15
> **Denn1s said:**
> can u log in as root and change it back?
i don't know what is this user's password !!

tried my password but nothig happened

---

### Post by phossal on 2007-01-15
You can reinstall Ubuntu in about 20 minutes. You'll have learned a good lesson, and hopefully some prudence. The 20 minutes you spend reinstalling is just 20 minutes. The 20 minutes you spend here is 20 minutes wasted multiplied by everyone who posted. lol

---

### Post by jocko on 2007-01-15
> **bahrain said:**
> i renamed it to "/root"only, and i did that from "users and groups"

Ok. **Now** I understand what you did. You changed so that your login (jaffar) uses /root as home folder? (**VERY** bad idea)
That means you can not login using the standard login, since you do not have write permissions to the /root folder.
And root login is normally disabled in ubuntu so you can not simply login as root and revert what you did.

I hope someone can help you sort it out from a command line (you can still boot in recovery mode to get a command line with root permission).

---

### Post by Denn1s on 2007-01-15
and wath about creating a new sesion for you using the recovery mode?

---

### Post by bahrain on 2007-01-15
> **Denn1s said:**
> and wath about creating a new sesion for you using the recovery mode?
how?

before that, how can i change "/root/ to "/home/jaffar/"using the recovery mode?

---

### Post by bahrain on 2007-01-15
> **jocko said:**
> Ok. **Now** I understand what you did. You changed so that your login (jaffar) uses /root as home folder? (**VERY** bad idea)
That means you can not login using the standard login, since you do not have write permissions to the /root folder.
And root login is normally disabled in ubuntu so you can not simply login as root and revert what you did.

I hope someone can help you sort it out from a command line (you can still boot in recovery mode to get a command line with root permission).
yes that it is

---

### Post by bahrain on 2007-01-15
> **phossal said:**
> You can reinstall Ubuntu in about 20 minutes. You'll have learned a good lesson, and hopefully some prudence. The 20 minutes you spend reinstalling is just 20 minutes. The 20 minutes you spend here is 20 minutes wasted multiplied by everyone who posted. lol
what is about a slow machine?!!

---

### Post by Lord Illidan on 2007-01-15
I'd advise you to reinstall. An advanced user could probably sort out the problem with some help, but given that you are not one of them (no offense intended, we all were newbies one day), it might be better to start from scratch.

---

### Post by jocko on 2007-01-15
I think I have figured out a way it can be done (I have not tested it, but it can not screw up your computer any more than it already is...).

To boot into recovery mode:
Reboot.
Press ESC when you see "Press ESC to enter the boot menu" (or something similar, I don't remember exactly).
In the boot menu, use the up/down keys to select a line that ends in "(recovery mode)". hit enter.

When boot finishes you will have a command line with root permissions.
Type the following command:
```
usermod -d /home/jaffar jaffar
```

This should change it back to the way it was, I hope.

---

### Post by bahrain on 2007-01-15
> **jocko said:**
> I think I have figured out a way it can be done (I have not tested it, but it can not screw up your computer any more than it already is...).

To boot into recovery mode:
Reboot.
Press ESC when you see "Press ESC to enter the boot menu" (or something similar, I don't remember exactly).
In the boot menu, use the up/down keys to select a line that ends in "(recovery mode)". hit enter.

When boot finishes you will have a command line with root permissions.
Type the following command:
```
usermod -d /home/jaffar jaffar
```

This should change it back to the way it was, I hope.
woooooooow

thanks

i did it :mrgreen:

---

### Post by MeduZa on 2007-01-15
remember, root users can't login on xorg by default

---

### Post by bahrain on 2007-01-15
root@jaffar-desktop:/home/jaffar# ./RealPlayer10GOLD.bin
bash: ./RealPlayer10GOLD.bin: Permission denied
root@jaffar-desktop:/home/jaffar# 


q2: how can i install real player?

---

