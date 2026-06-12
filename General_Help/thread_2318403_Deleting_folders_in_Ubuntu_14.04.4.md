---
title: "Deleting folders in Ubuntu 14.04.4"
date: 2016-03-25
forum: General Help
---

### Post by lakeshore2985 on 2016-03-25
So I was trying to remove non-empty folders in Ubuntu and after several tries, finally managed to do it but only if "*sudo -i*" first.

Why is that so? I thought a simple "*rm -r <folder>*" or "*rmdir -R <folder>*" would do it but didn't. Would somebody please explain?

Thanks!

---

### Post by buzzingrobot on 2016-03-25
A user can alter or remove files and folders that user owns.  But, a user cannot do the same with files/folders that user does not own.

You own all the files and folder typically found in your home folder. 

It is possible to put files in your home folder that you don't own. One way might be to expand an archive you've downloaded from someplace that contains files or folders owned by the root user.

To alter or delete files you don't own, you need to temporarily acquire the capabilities that otherwise belong exclusively to the root user. That's called "privilege escalation" and, in Ubuntu, it's done with "sudo". You can preface a single command with sudo, or use it as "sudo -i", which escalates your privileges for a period of time. Any command you enter after that will be executed with root's privileges.  You'll see that the prompt in the terminal window changes when you do that.

In Linux, files and folders outside your home folder are usually owned by the root user.

Permissions -- who can do what to which files -- can also come into it, but that's more complex.

---

### Post by QIII on 2016-03-25
Hello!

Great care should be taken if removing directories outside your /home.

What sort of things have you been removing?

---

### Post by grahammechanical on 2016-03-25
> Why is that so?

It stops a program with malicious code from deleting the OS. It stops anyone who gains access to the OS who does not have authority from deleting the OS. 

Regards.

---

### Post by lakeshore2985 on 2016-03-25
> **buzzingrobot said:**
> To alter or delete files you don't own, you need to temporarily acquire  the capabilities that otherwise belong exclusively to the root user.  That's called "privilege escalation" and, in Ubuntu, it's done with  "sudo". You can preface a single command with sudo, or use it as "sudo  -i", which escalates your privileges for a period of time.

Yes, and this is exactly my problem. Forgot to mention in my original post that such command "*sudo rm -r / sudo rmdir -R*" is not working under Ubuntu 14.04.4. As I said, only if I "*sudo -i*" first to delete VM folders/files inside home directory.

---

### Post by bab1 on 2016-03-25
> **lakeshore2985 said:**
> Yes, and this is exactly my problem. Forgot to mention in my original post that such command "*sudo rm -r / sudo rmdir -R*" is not working under Ubuntu 14.04.4. As I said, only if I "*sudo -i*" first to delete VM folders/files inside home directory.
You have to show the exact command you used.  The command rmdir has no recursive permissions and specifically does not allow removing a directory that has files in it.  See the man page excerpt```
NAME
       rmdir - [COLOR="#FF0000"]**remove empty directories**[/COLOR]

SYNOPSIS
       rmdir [OPTION]... DIRECTORY...

DESCRIPTION
       Remove the DIRECTORY(ies),[COLOR="#FF0000"]** if they are empty.**[/COLOR]

```

There is no switch for recursive or to override the fact that there are files in the directory.

You can use rm as root to do this however (rm -rf), but not rmdir.

---

### Post by lakeshore2985 on 2016-03-25
> **bab1 said:**
> You have to show the exact command you used.  The command rmdir has no recursive permissions and specifically does not allow removing a directory that has files in it.  See the man page excerpt```
NAME
       rmdir - [COLOR=#FF0000]**remove empty directories**[/COLOR]

SYNOPSIS
       rmdir [OPTION]... DIRECTORY...

DESCRIPTION
       Remove the DIRECTORY(ies),[COLOR=#FF0000]** if they are empty.**[/COLOR]

```

There is no switch for recursive or to override the fact that there are files in the directory.

You can use rm as root to do this however (rm -rf), but not rmdir.

Yes, thank you for the additional information.

Actually I was able to finally delete the directories by first running "*sudo i*" and then "*rm -r VirtualBox\ VMs/*" (a little side note is that these VM directories and pertaining files are from a different user than root, if it makes any difference). 

So first I tried many different combinations of commands, just to give a few examples:

*sudo rmdir -R VirtualBox\ VMs* --> not working
*sudo rmdir -r VirtualBox\ VMs* --> not working
*sudo rm -R VirtualBox\ VMs* --> not working
*sudo rm -r VirtualBox\ VMs* --> this is supposedly correct but not working strangely / has to effectively become root in order to work

---

### Post by bab1 on 2016-03-25
> sudo rm -r VirtualBox\ VMs --> this is supposedly correct but not working strangely / has to effectively become root in order to work 
Most likely this has to do with what user owns the VirtualBox\ VMs and the existing shell environment.  The command sudo without the -i switch uses the root user's environment.  FWIW, any user can delete their own directories with files still present as long as they own the directory and the files.  I alter that action by adding an alias to use *rm -i *(interactive) instead of just rm.  It asks me for confirmation on each file to be deleted.  So If I know what I'm deleting I use *sudo rm -rf *to force the deletion without asking.

---

### Post by lakeshore2985 on 2016-03-25
> **bab1 said:**
> Most likely this has to do with what user owns the VirtualBox\ VMs and the existing shell environment.  The command sudo without the -i switch uses the root user's environment.  FWIW, any user can delete their own directories with files still present as long as they own the directory and the files.  I alter that action by adding an alias to use *rm -i *(interactive) instead of just rm.  It asks me for confirmation on each file to be deleted.  So If I know what I'm deleting I use *sudo rm -rf *to force the deletion without asking.

Thanks, I'll look into it further. 

First "*sudo rm -i*" then "*sudo rm -rf*" seems like good practice.

---

