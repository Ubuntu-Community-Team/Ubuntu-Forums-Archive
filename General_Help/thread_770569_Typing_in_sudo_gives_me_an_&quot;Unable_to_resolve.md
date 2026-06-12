---
title: "Typing in sudo gives me an &quot;Unable to resolve host&quot; error"
date: 2008-04-27
forum: General Help
---

### Post by jjthomas on 2008-04-27
I'm trying to set up my Wifi and I need to edit /etc/network/interfaces per the HOWTO [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)
But every time I type in sudo <any command> I get a "Unable to resolve host" error.

](*,):x

Even sudo ls results in "unable to resolve host ...."

And I searched sudo and all I got were threads about Windows Vista :confused:

Help....

-JJ

---

### Post by ghost_ryder35 on 2008-04-27
just set a password for your root account, since sudo doesnt work you'll have to do it through the gui
go to 
System
Administration
Users and Groups
click on root
then change the password to whatever you like
 
then when you go to the command line again type
```

su -
*password prompt*

```
 
this is a work around though.  I'll google around and see what I can come up with about the sudo problem.  sounds like its trying to search out on the net for an address of "sudo"

---

### Post by Iowan on 2008-04-27
See if anything [here]("http://www.psychocats.net/ubuntu/fixsudo") helps. (Also the last link in my signature)

---

### Post by chrisccoulson on 2008-04-27
I think this is related to [bug 185209]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/185209")

---

### Post by pbpersson on 2008-04-27
> **jjthomas said:**
> I'm trying to set up my Wifi and I need to edit /etc/network/interfaces per the HOWTO [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)
But every time I type in sudo <any command> I get a "Unable to resolve host" error.

](*,):x

Even sudo ls results in "unable to resolve host ...."

And I searched sudo and all I got were threads about Windows Vista :confused:


I would Google the following:

ubuntu "Unable to resolve host"

and find one of the posts where this was resolved.

---

### Post by jjthomas on 2008-04-28
ghost_ryder35: It didn't take me long to go that route. :LOL:
Thanks.

chrisccoulson:  I checked the bug report.  I'm guilty of two things they list in it.  I did chenge my hosts file, old habit and my big problem is I'm trying to get my WiFi working, which is not working as of yet.  So there is no name resolution.  But that should not come into play with sudo.  Will take another look at it when I get home.  Thanks,

-JJ

---

### Post by chrisccoulson on 2008-04-28
> **jjthomas said:**
> chrisccoulson:  I checked the bug report.  I'm guilty of two things they list in it.  I did chenge my hosts file, old habit and my big problem is I'm trying to get my WiFi working, which is not working as of yet.  So there is no name resolution.  But that should not come into play with sudo.  Will take another look at it when I get home.  Thanks,

-JJ

You're right - it *should not* come in to play with sudo, but it does. See [_**bug 32906**_]("https://bugs.edge.launchpad.net/ubuntu/+source/sudo/+bug/32906")

---

