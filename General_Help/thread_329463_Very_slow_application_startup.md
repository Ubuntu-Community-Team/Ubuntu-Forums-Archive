---
title: "Very slow application startup"
date: 2007-01-01
forum: General Help
---

### Post by jigarzon on 2007-01-01
Hi, 

after a few days ago, some application's startup became very slow. For example, opening gnome-terminal takes about 1 minute in some cases. After starting, they work normally, the problem is only within startup of applications.

I have read all the posts in this forum and in gnome's forum related to this issue, but i couldn't resolve the problem. 

As I said, not all applications are starting slow, i think maybe this could be a suggestion of where to find the problem. apt-get, amsn, ooffice, the gimp, and common linux applications (ls, cp, mv, rm, etc) are starting fast (they are the only I found), but all gnome applications, xmms, beryl-manager, mc,  etc are affected by this problem.

I have monitored CPU and Memory usage when starting gnome-terminal. CPU usage is 2% in CPU 1 and 9% in CPU 2, and it does not change significantly, the same happens with RAM.

After a few days everything worked alright, I don't remember exactly what I've done.

I have a Dell Inspiron 6400 laptop Centrino duo 1.88ghz, with 1GB Ram, running ubuntu 6.10.

Thanks in advance!!

---

### Post by Shatrat on 2007-01-01
I can't say I've seen anything quite like this, but maybe you should try launching the offending applications from a terminal so that any error messages are immediately apparent.
Perhaps they are waiting on some resource that isn't available and don't start until it times out or gets freed up.

Good luck.

---

### Post by adamonline on 2007-01-01
[QUOTE=Jigarzon]...opening gnome-terminal takes about 1 minute...[/quote]

[QUOTE=Shatrat]...maybe you should try launching the offending applications from a terminal...[/QUOTE]

Oh irony, sweet irony :D

Regardless, good suggestion...

---

### Post by mpop on 2007-01-02
Same problem here. Nautilus and gnome-terminal and Gaim and Eye of Gnome are delayed (usually 20s of "inactivity" before the application starts to launch), while Firefox and The Gimp and others are perfectly fine. There seems to be more evidence of delayed application startup here :
[http://www.ubuntuforums.org/showthread.php?t=296443](http://www.ubuntuforums.org/showthread.php?t=296443)

Sadly, there was no real answer. Someone suggested turning off IPv6, but I can't see how the *Internet Protocol* could delay applications which just don't use the network at all (or do they?)...

Well, maybe I'll try that anyway.

---

### Post by 2CV67 on 2007-01-02
See last post here - it sounds like same problem to me.

[http://www.ubuntuforums.org/showthread.php?t=323151](http://www.ubuntuforums.org/showthread.php?t=323151)

Don't ask me for explanation though...

---

### Post by jigarzon on 2007-01-02
> **Shatrat said:**
> I can't say I've seen anything quite like this, but maybe you should try launching the offending applications from a terminal so that any error messages are immediately apparent.
Perhaps they are waiting on some resource that isn't available and don't start until it times out or gets freed up.

Good luck.
Thanks for the advice, but I already tried that (as I said, the problem happens even in console applications like mc, not only gnome apps).

I've done an strace of my "offending applications", I will post the ouput after reading the solution from 2CV67 (and after i go back to home)

Thanks for your responses!!

---

### Post by mpop on 2007-01-03
jigarzon > just in case you didn't notice, it really seems to be a networking problem. Fixing your /etc/hosts config file (and if necessary your /etc/hostname config file) should do the trick. See this thread:
[http://www.ubuntuforums.org/showthread.php?t=296625](http://www.ubuntuforums.org/showthread.php?t=296625)

It seems that your /etc/hosts should have at least one line with :
```
127.0.0.1 <your-hostname> localhost
```
or
```
127.0.0.1 localhost <your-hostname>
```
Don't know if the order is important.

---

### Post by crapapelada on 2007-03-06
Removing all entries related to IPv6 from the hosts file solved the problem in my case.
I am testing the various methods suggested in the forum to disable IPv6 to get rid of it once for all.
I move from a network to another on a daily basis; everything seems to be related to DNS configuration and IPv6, even if it sounds strange.
Everytime I changed the active network profile the problem appeared again and pissed me off until I edited the hosts file.
Hope that disabling IPv6 it will be gone.

---

### Post by rjikzy on 2007-03-17
I have a several problems, but this not network problems. Applications  (like mc, not lan-dependency) starting is very slow.... Help! :confused: :confused: :confused:

---

### Post by Catfish81 on 2007-03-18
I am also having slow app start up problems. The gnome panel now fails to load fully. It sits there blank for about a minute then disappears and my desktop loads. Starting up most applications take about half to a full minute - sometimes even more.

I have Ubuntu 6.10 and i did all the latest updates. I only just started using Ubuntu so this isn't really fun.

I've edited my /etc/hosts file, commenting out all the ipv6 lines and editing the 127.0.0.1 entries.

My hosts file now says:
127.0.0.1       localhost       delta
(all other lines are commented out)

EDIT: I have now also disabled ipv6 (added an /etc/modprobe.d/bad_list file) and this doesn't fix the problem. I don't think this has disabled ipv6 because "ip a | grep inet6" still shows results.

Here's an overview of the problems I have:
- After login (username and password) it takes about a minute before my desktop is loaded.
- The gnome-panel half loads and then disappears. Having made a desktop icon to launch the panel, it will start rather quickly, but my launcher icons and system tray apps take a while to load up.
- amsn will not load on startup as specified in the sessions manager
- loading of pretty much any program takes a long time before the app actually appears on screen.
- i get "starting application name" on the taskbar for a little while, then that disappears, the hard drive light stays on solid until the app appears on screen.
- once the app appears on screen, it functions normally.

I've checked for free memory issues, swap usage etc and none of that is a problem. I barely use half of the available RAM and no swap.

---

### Post by gp2x on 2007-03-27
You disable ipv6 by editing 

/etc/modprobe.d/aliases

and changing

alias net-pf-10 ipv6

to 

alias net-pf-10 off

---

### Post by fledder on 2007-04-10
> **gp2x said:**
> You disable ipv6 by editing 

/etc/modprobe.d/aliases

and changing

alias net-pf-10 ipv6

to 

alias net-pf-10 off

That solved my problem right away, awesome! Before: 30 sec delay on application launch, after: no delay :) 

Thanks!

---

### Post by playmodrill on 2007-08-10
any other ideas please?

i use dapper, i turned off IPv6 but that doesn't work. i checked all the related threads and tried every solution, now my /etc/hosts file contains only 127.0.0.1 localhost <hostname> but gnome is slow with every application.

i think my problem is because i had to switch several times between a static IP configuration at my uni and a DHCP at home, now i want to fix at least with DHCP... any suggestion is welcome, i don't really know what to do.

thanks

---

### Post by zasf on 2007-08-15
> **mpop said:**
> jigarzon > just in case you didn't notice, it really seems to be a networking problem. Fixing your /etc/hosts config file (and if necessary your /etc/hostname config file) should do the trick. See this thread:
[http://www.ubuntuforums.org/showthread.php?t=296625](http://www.ubuntuforums.org/showthread.php?t=296625)

It seems that your /etc/hosts should have at least one line with :
```
127.0.0.1 <your-hostname> localhost
```
or
```
127.0.0.1 localhost <your-hostname>
```
Don't know if the order is important.

it fixed it!!!

**before**
```
matteo@z2:~$ cat /etc/hosts.backup
127.0.0.1 localhost
127.0.1.1 z2.zcasa

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```
**after**
```

matteo@z2:~$ cat /etc/hosts
127.0.0.1 localhost z2
127.0.1.1 z2.zcasa

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

@playmodrill: /etc/hosts is modified by the network setup app, make sure that when you change between networks the file is changed right, now I use feisty or gutsy, but I remember I had such problems with dapper

---

### Post by playmodrill on 2007-08-28
Thanks Matteo,

i always did that, but my laptop loads gnome normally (ie within a reasonable time) randomly, let's say one time it's OK against 5 times not working correctly. I'm wondering if it's not due to another problem, but the symptoms are quite the same everyone described in this post.

As an extreme measure, I think I'll go for a complete format and installation of Feisty. I'll stick with only one kind of network and if even that doesn't work, well it'll be clear it's another issue.

---

### Post by zasf on 2007-08-29
> **playmodrill said:**
> i always did that, but my laptop loads gnome normally (ie within a reasonable time) randomly, let's say one time it's OK against 5 times not working correctly. I'm wondering if it's not due to another problem, but the symptoms are quite the same everyone described in this post.

I also had such problem, sometimes it worked, sometimes it didn't. I didn't check /etc/hosts every single time, so I'm not sure, but *maybe* network-manager didn't configure that file in a right manner for every different network connection.

> **playmodrill said:**
> As an extreme measure, I think I'll go for a complete format and installation of Feisty. I'll stick with only one kind of network and if even that doesn't work, well it'll be clear it's another issue.

If you have time, a clean feisty install won't hurt for sure :)

Matteo

---

