---
title: "can't start Softwre Source and Synatpic Package manager"
date: 2008-04-19
forum: General Help
---

### Post by thedoorguy on 2008-04-19
I'm running ubuntu 7.10

When I click either Software Source or Synaptic Package Manager in System Administration
the load cursor shows for a few moments but nothing appears on screen.

Anybody know what to do?

---

### Post by forrestcupp on 2008-04-19
Here's a couple of things to try in the terminal to see if you can get some kind of error.  Open a terminal and give us any output you get from these two commands
```
sudo apt-get update
```
and
```
gksu synaptic
```

If you get some kind of error, it will help figure out what to do to fix it.

---

### Post by overdrank on 2008-04-19
> **thedoorguy said:**
> I'm running ubuntu 7.10

When I click either Software Source or Synaptic Package Manager in System Administration
the load cursor shows for a few moments but nothing appears on screen.

Anybody know what to do?

HI and you can try the command in the terminal or using the lat, F2 keys ```
gksu /usr/sbin/synaptic
```

Edit oops  :oops: too slow

---

### Post by thedoorguy on 2008-04-19
when i enter sudo get update........  I get respons sudo: unable to resolve host rph-desktop
and when I entered gksu synaptic ......... nothing happened.... it appears to have locked the terminal

---

### Post by thedoorguy on 2008-04-19
gksu /usr/sbin/synaptic ........ nothing happens.... appears to lock up the terminal

---

### Post by bodhi.zazen on 2008-04-19
did you change your host name ? 

Boot to recovery mode and make sure your host name is the same in 

/etc/hostname and /etc/hosts

(in /etc/hosts it is listed as 127.0.0.1 <hostname> )

---

### Post by thedoorguy on 2008-04-19
when I drop to root when the menu pops up during recover boot and enter either /etc/hostname or /etc/hosts I get the response.... permission denied,

I had the same problem before ie can't access the admin function before and uninstalled and started again from scatch.  So I now have a recreation of the Synaptic problem.  

Something I've done both times that may have something to do with 127.0.0.1 is to change etho0 property of the network settings from roaming to automatic configuation DHCP.   I made the change so that I can access other windows share computers on my wired network which ny router assigns ip numbers to as they they log on.  

The host page of the network setting under columes IP Address and Aliases has host  127.0.0.1 listed as localhost and 127.0.0.1 as rph-desktop.ubuntu.

I could access the Synaptic this morning but I do not know if the problem started immediately after I made the network settings change.

Changing the setting back to roaming does not solve the problem.

---

### Post by thedoorguy on 2008-04-19
I just found out that I also can't install using Add/Remove Applications.

When I select a package and click "Apply Change", the window shades, the load cursor appears and nothing else happen.... the window just stays there.

I think is was at about this time the last time I decided to uninstall-reinstall.  This time I am thinking uninstall and forget it.....all ubuntu seems to be is one problem after another.  I can't get it up and keep it running to do even the simplist things.

---

### Post by overdrank on 2008-04-19
> **thedoorguy said:**
> I just found out that I also can't install using Add/Remove Applications.

When I select a package and click "Apply Change", the window shades, the load cursor appears and nothing else happen.... the window just stays there.

I think is was at about this time the last time I decided to uninstall-reinstall.  This time I am thinking uninstall and forget it.....all ubuntu seems to be is one problem after another.  I can't get it up and keep it running to do even the simplist things.

Hi and was the installation with Wubi? If so have you thought of trying the traditional methods. Good luck in what ever you choose. :KS

---

### Post by bodhi.zazen on 2008-04-19
When you boot to recovery mode you are root, but at a command line.

To look at those files use a command line editor, like nano

```
nano /etc/hosts
nano /etc/hostname
```

To exit nano, type Ctrl-X

To save chanes, type Y then hit the enter key.

To exit without changes, type N (if you made no changes you will not be asked).

It takes a while to learn a new OS, and no windows does not "just work".

---

### Post by thedoorguy on 2008-04-19
> **overdrank said:**
> Hi and was the installation with Wubi? If so have you thought of trying the traditional methods. Good luck in what ever you choose. :KS

Yep, wubi.  I am going to dump it (uninstall) and try "the traditional method."


A BIG THANK YOU TO ALL WHO RESPONDED TO MY THREAD.  WITH YOUR HELP AND GUIDANCE I WILL ONE DAY GET THIS OS UP AND RUNNING.  (OR...maybe, die from frustration trying.)

---

