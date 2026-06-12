---
title: "Ubuntu - Problem with Users and Groups"
date: 2006-08-14
forum: General Help
---

### Post by henrikfromnorway on 2006-08-14
Hi!

I have Ubuntu installed on my shell/web-server, and I tried to start Users and Groups (in Gnome)

I got this error:
```
ERROR

The configuration could not be loaded

There was an error running the backend script
```

When I press OK, the program terminates.

How can I fix this? I've tried logout-login, but it didn't work.
I also googled, but I didn't find anything good.

I got a hint; 
```
gksu users-admin
``` in termnial

That resulted in this:
```
hc@square:~$ sudo gksu users-admin

(gksu:13466): Gtk-WARNING **: cannot open display:
hc@square:~$
```
I also tried without sudo in front, no difference.


So, any ideas?

---

### Post by brundles on 2006-08-14
Looks like it's trying to access the x-desktop without access.

Try typing:
    xhost +

Before the SUDO command. That will remove all restrictions so anyone (including from the internet if you're not firewalled) can open an X-Window on your desktop.

Remember to type "xhost -" when done to restore security.

---

### Post by henrikfromnorway on 2006-08-15
Found the problem

I had æøå (norwegian characters) in the name. Not nick/username, but real name.

works perfect now :)

---

### Post by Tjakka on 2006-08-23
I noticed that I had installed Ubuntu using a certain hostname. I removed this name from /etc/hosts and left it with just localhost. This appears to have the same effect on functionality. None of the admin tools will get access to the display :-#  (xhost + does not make a difference) If the tool is executed from a console it complains:

[FONT="Courier New"]gksu users-admin
sudo: unable to lookup stillewilly via gethostbyname()[/FONT]

Executed from a root-console it complains:

[FONT="Courier New"]gksu /usr/bin/update-manager

(gksu:23982): Gtk-WARNING **: cannot open display:[/FONT]

For the record....

---

### Post by hans maree on 2006-08-29
I just insalled ubuntu today and I seem have the same problem. How can I set the hostname without reinstalling ubuntu?

my etc/hosts file looks like this:
> 
127.0.0.1	localhost.localdomain	localhost	woonkamer

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


(BTW woonkamer is dutch for 'living room' (the computer name))

can anyone help?

---

