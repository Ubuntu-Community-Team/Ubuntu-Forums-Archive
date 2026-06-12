---
title: "[SOLVED] su and sudo problem, can't patch kernel"
date: 2008-06-24
forum: General Help
---

### Post by Titan8990 on 2008-06-24
Yesterday I did the update in which patches the kernel. This did not work out well for me as GRUB was wailing to launch the OS after that giving me an "file not found" error when selected either of the three kernel versions listed in grub.

So I restore from a back up and most things seemed to go smoothly except now I am forced to log in as root because I can not get root privleges as a user. 

Whenever I try to look at the users and groups GUI it never opens. It hangs for a minute and then quits itself. But this is the major issue I am having:

```
jordan@einstein:~$ sudo fdisk -l
sudo: must be setuid root
```

```
jordan@einstein:~$ su
Password: 
su: Authentication failure
Sorry.
```

I know that my password is correct because I can log in root. 

The setuid sounds like a permissions issue but I have checked files that I know what permissions they should have and the retained the correct permissions as they should have.

This issue is also preventing me from attempting to update again as the update manager does nothing.

Thank you for any insight that you all can provide.

Edit: After some further testing it looks like any GUI that requires an admistrative password will not work at all.

---

### Post by cariboo on 2008-06-24
You shouldn't need a gui on a server as it is just wastes ram and cpu cycles. There are no gui sever administration tools in Ubuntu. Open up a terminal and type:

```
man adduser
```

If you scroll down a bit you will see a section Add a normal user. 

Jim

---

### Post by Titan8990 on 2008-06-25
That is not an issue at the momment. This server is not live yet so I have been using GUIs for things such as wireshark. I am aware of how to do most eveything from the BASH shell.

My #1 issue is not being able to sudo or su commands. This forces me to log on as root which I do not like doing for security reasons.

I found a article on how to repair sudo but I had no luck with it.

Also, this does not answer the question of why the kernel patch that is sitting update manager breaks my OS.

I appreciate the try.

---

### Post by cariboo on 2008-06-25
I know this is a problem with the desktop edition but I don't know if it is also an issue with the server edition but you can have a look any how:

```
cat /etc/host
127.0.0.1       localhost
127.0.1.1       <user>.domanename
```

should be

```
cat /etc/host
127.0.0.1       localhost
127.0.1.1       <user>.domanename      <user>
```



Jim

---

### Post by |{urse on 2008-06-25
try becoming root, why exactly did you think it was a bad idea?

> sudo su

then do the patch. You will still need to adduser etc. etc. at some point.

---

### Post by Titan8990 on 2008-06-25
If you all are wanting me to add myself to the admin group that has been done since the beginning. 

I don't have a problem logging on root but I do have a problem with leaving the server running with root logged in. It is a hassle to constantly log in and out when I should be able to just sudo most commands.

For now I am switching to tty3 and logging in to root from there temporarily. I would like to find out what is going on with my alternate user and sudo commands.

Cariboo, my /etc/hosts list is larger than that. I had to do a bit of experimenting with it to get exim4, apache, and samba functioning correctly.

Thank you guys for you input.

---

### Post by Titan8990 on 2008-06-26
bump

---

### Post by Titan8990 on 2008-06-26
Up again

---

### Post by Titan8990 on 2008-07-09
Alright, I am marking this as solved. If anyone is interested in my solution:

1) reformatted and reinstalled Ubuntu

2) redid all my work....

3) pulled out the eSATA drive before patching the kernel.

---

