---
title: "SUDO Problems - Help!"
date: 2007-06-27
forum: General Help
---

### Post by Cellojazz on 2007-06-27
I'm using Ubuntu Server and after installing NIC Bonding and VMWare-Server - I can't SUDO..

Well I can, kinda.  If I sudo a command, it works, I can sudo apt-get install... but the kicker is I cannot sudo su...
I do, and I don't get an error, but the prompt still says 

adminuser@host:~$

and when I try to add a root password - which is why I'm doing this, it says 
Changing password for adminuser:


(Note adminuser represents the user I installed to administer the server, not the root user)

What happened?

The only action I think that I would have controlled in the process would have been adding the disk group to adminuser

I used the following command:

sudo usermod -G adminuser disk

Did that remove me from the root user group?

Any information that helps in me getting my su command back, and actually being able to login as root would be very helpful.  I need that to be able to change the memory management settings of my vmware server.

---

### Post by McNils on 2007-06-27
```
sudo usermod -G adminuser disk
```
Sets user disk to be in group adminuser... If you didn't swap the arguments when you pasted you shuold be safe. However, the -G argument sets the groups the user should be in and removes all groups not listed. 

To be able to sudo the user must be in group admin. You shuold be able to start the computer in recovery mode and add your adminuser to the admin group.

You can use sudo -i to login as root instead of sudo su.

---

### Post by Cellojazz on 2007-06-27
Well I finally figured out the syntax and did the follwoing

<code> as root<br>
usermod -G adminuser -G root -G disk adminuser
<code>

This at least didn't complain at my syntax.  Still no sudo rights.  After recovering to single user and creating a root password, I at least can login as root.  Otherwise, though I'd like to know how to rescue my system to get sudo back

I also tried manually editing the gshadow and group files previously to fix the group issue and did this

root::adminuser
disk::adminuser

anywhere else I can check to get sudo back to where it was?  D

-- note just figured out that I needed to be in the admin group in /etc/groups

---

