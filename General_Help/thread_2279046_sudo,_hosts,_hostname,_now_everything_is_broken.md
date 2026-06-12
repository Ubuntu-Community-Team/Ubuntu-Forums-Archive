---
title: "sudo, hosts, hostname, now everything is broken"
date: 2015-05-20
forum: General Help
---

### Post by OhLongCat on 2015-05-20
I ran an ARM version of Ubuntu-Mate under Raspberry Pi 2. It worked well until I tried to sudo. It said "sudo: unable to resolve host pi-ubuntu-mate". I googled and found out that I had to change /etc/hosts and /etc/hostname.  [br]1[/br] In my /etc/hosts is [br]1[/br] pi-ubuntu-mate [br]1[/br]  In my /etc/hostname was [br]1[/br]127.0.0.1 localhost[br]1[/br]127.0.1.1 pi-ubuntu-mate.HOME [br]1[/br] I changed pi-ubuntu-mate.HOME to simply pi-ubuntu-mate and rebooted. But after that xserver started but there were no panel and no icons on the desktop. I terminated xserver, and with sudo nano /etc/hostname changed everything back and rebooted again. But alas it was the same. Important to mention if I login under a guest account everything is OK. [br]1[/br] I might just rewrite the image to the SD card and start over, but I'd like to know what I broke and never do it again. What else can I do?

---

### Post by Bashing-om on 2015-05-20
OhLongCat; Hello;

Mind you I have no experience with the Raspberry Pi ; However, extrapolating from a standard install ->
the 'name' in /etc/hosts must match exactly to that in /etc/hostname.

Also we need to verify that "you" own your /home.
What returns:
```

ls -al /home
ls -al /home<'you'>

```
example:
```

sysop@1404mini:~$ ls -al /home/sysop/
total 4612
drwxr-xr-x 29 sysop sysop    4096 May 20 11:46 .
drwxr-xr-x  4 root  root     4096 May 19  2013 ..
drwx------  2 sysop sysop    4096 Sep 13  2014 #133454 • Fedora Project Pastebin_files
-rw-r-----  1 sysop sysop   11389 Sep 13  2014 #133454 • Fedora Project Pastebin.html
drwx------  2 sysop sysop    4096 May  7  2014 .aptitude
-rw-------  1 sysop sysop   40051 May 19 23:14 .bash_history
-rw-r--r--  1 sysop sysop     309 Jul  8  2013 .bash_logout
-rw-r--r--  1 sysop sysop     220 May 19  2013 .bash_logout~
-rw-r--r--  1 sysop sysop     220 Jul  8  2013 .bash_logout-orig
-rw-rw-r--  1 sysop sysop    2154 Mar 20 17:44 bash'n
<snip>
-rw-------  1 sysop sysop    1956 May 20 11:46 .ICEauthority
<snip>
-rw-------  1 sysop sysop     209 Feb  4 15:15 .Xauthority
<snip>

```

[INDENT][INDENT]security
[INDENT][INDENT][INDENT]who has access
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by OhLongCat on 2015-05-20
It is probably not important what I'm running. Just said for information. I did ls -al /home/pi, it gave something like yours. ls -al /home gave me three lines with root, root, pi.

---

### Post by bab1 on 2015-05-20
> **OhLongCat said:**
> [br]1[/br] In my /etc/hosts is [br]1[/br] pi-ubuntu-mate [br]1[/br]  In my /etc/hostname was [br]1[/br]127.0.0.1 localhost[br]1[/br]127.0.1.1 pi-ubuntu-mate.HOME [br]1[/br] 

The above is backwards.  The /etc/hostname file should only hold the hostname```
 pi-ubuntu-mate
```

The /etc/hosts file should have the mapping of IP Address to hostname```

127.0.0.1 localhost
127.0.1.1 pi-ubuntu-mate pi-ubuntu-mate.HOME
```

The last line above maps both the hostname and it's alias to the IP address of 127.0.1.1

---

### Post by OhLongCat on 2015-05-20
> **bab1 said:**
> The above is backwards. Yes, you're right, my mistake in the original post. > **bab1 said:**
> The /etc/hosts file should have the mapping of IP Address to hostname Just did. No effect. I'll probably give up. :(

---

### Post by nerdtron on 2015-05-20
And have you tried to reboot after you changed the hostname?

---

### Post by OhLongCat on 2015-05-22
> **nerdtron said:**
> And have you tried to reboot after you changed the hostname? You're kidding. Obviously I rebooted. It seems something's wrong with xserver.

---

