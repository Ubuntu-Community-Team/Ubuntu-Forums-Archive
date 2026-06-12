---
title: "Please help me escape from this corner I've painted myself into"
date: 2013-06-11
forum: General Help
---

### Post by hawthornso23 on 2013-06-11
In the process of repurposing a machine I changed the hostname in /etc/hostname from <oldname> to <newname>. This apparently innocuous change killed my ability to use sudo. Sudo now responds

```
sudo: unable to resolve host <newname>
```

Some quick research reveals that the problem is I didn't also change the name in /etc/hosts to match. There is a really easy fix. I simply need to edit one of /etc/hostname or /etc/hosts to make the names match again. However both files are owned by root so I need to be root to edit them and sudo and gksudo don't work. I have not previously created a root user and password so I can't log in as root. I can't create a root password now because I'd need root privileges to do it and sudo doesn't work. Rebooting I can get into a grub menu and from there into a recovery terminal as root. But the filesystem is then mounted readonly so I still can't fix the problem.

My fix of last resort would be creating a bootable USB key or DVD and booting into that. I should then be able to mount the disk and edit the files. But as I don't have any bootable stuff lying around that is going to be time consuming and painful. Is there a quicker fix? Perhaps a way  to remount the file system read/write in the root recovery terminal so that I can fix the problem. 

A change of hostname killing sudo is very nasty and unexpected behavior. Shouldn't there at least be a comment in the hostname file warning of this issue? I can't be the first to trigger this trap.

---

### Post by Mariane on 2013-06-11
Boot your computer with a Ubuntu install disk, select the "Try Ubuntu without installing it" option, and you should be able to modify your files. 
Cheer up, it does not take very long :).

---

### Post by hawthornso23 on 2013-06-11
That is going to require a trip to the shop to buy some blank disks. But if I have to do it that way, I will.

---

### Post by hawthornso23 on 2013-06-11
Well blow me down with a feather - I seem to have fixed it. 
It looks like you simply need to wait long enough. Ten minutes or
so after the error message appeared sudo suddenly popped up a 
password prompt and then actually worked! So I was able to edit 
\etc\hosts and fix the problem. No idea why the long and confusing 
delay - some mysterious network timeout no doubt.

Problem fixed.

---

### Post by JKyleOKC on 2013-06-11
If you can get to a grub screen during the boot process, select the "recovery" option, normally the second one from the top. This should give you another menu, which includes the option to boot into the root user. It will be command-line, not a GUI, but you can use nano or vi to edit the appropriate file. Then reboot and you should be back in business.

While this may appear to be a huge security hole, remember that physical access to a machine is already the biggest security hole possible -- and the recovery option isn't available to remote users.

---

### Post by tgalati4 on 2013-06-11
It's possible that your router's host table got confused and the error message that you are seeing was simply a *wall* message (something sent to all consoles).  The long time pause was probably the continuous lookup failures, which eventually resolved itself with a remaking of the host table on the router.

Changing the hostname will break cups and a few other services without a clean reboot.  The hostname change probably broke the authentication framework and not sudo itself, but it has the same effect--you can't do anything.

Changing hostnames, user account names, or deleting anything in /usr/bin can have bad effects on a linux system.

---

### Post by Cheesemill on 2013-06-11
> **hawthornso23 said:**
> Rebooting I can get into a grub menu and from there into a recovery terminal as root. But the filesystem is then mounted readonly so I still can't fix the problem.

For future reference running the following command in the recovery terminal will remount the root filesystem in read/write mode...
```
mount -o rw,remount /
```

---

