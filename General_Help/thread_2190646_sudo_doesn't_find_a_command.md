---
title: "sudo doesn't find a command"
date: 2013-11-28
forum: General Help
---

### Post by fabrice.lambert on 2013-11-28
Hi!

I'm trying to compile some fortran code using the Intel Fortran compiler, which I installed in /opt/intel/bin. I added /opt/intel/bin to the PATH and bash has no trouble finding it as either normal user or super-user. However, when I try to invoke ifort using sudo, it tells me "sudo: ifort: command not found":
```
fabrice@Lambert-Desktop:~$ ifort
ifort: command line error: no files specified; for help type "ifort -help"
fabrice@Lambert-Desktop:~$ sudo su
[sudo] password for fabrice: 
root@Lambert-Desktop:/home/fabrice# ifort
ifort: command line error: no files specified; for help type "ifort -help"
root@Lambert-Desktop:/home/fabrice# exit
exit
fabrice@Lambert-Desktop:~$ sudo ifort
sudo: ifort: command not found
fabrice@Lambert-Desktop:~$
```

How can I make sudo find the ifort command? Does sudo have some hidden PATH variable somewhere?

Thanks,
Fabrice

---

### Post by steeldriver on 2013-11-28
The root user has its own PATH, just like any other user - you can see what it is using

```
$ sudo sh -c 'echo $PATH'
```

(note the use of single quotes - not double quotes - to prevent the user's shell from expanding $PATH **before **passing the command to the sudo shell). You can either try adding the -E option to tell sudo to preserve the invoking user's environment (it may not be allowed, depending on security policy I think), or set the PATH explicitly on the command line

```

sudo PATH=$PATH sh -c 'echo $PATH'

```

---

### Post by fabrice.lambert on 2013-11-28
Hi, thanks for looking at this.

I see. Why does sudo have a different path than the super user?

```
fabrice@Lambert-Desktop:~$ sudo sh -c 'echo $PATH'
[sudo] password for fabrice: 
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
fabrice@Lambert-Desktop:~$ sudo su
root@Lambert-Desktop:/home/fabrice# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/opt/intel/bin
root@Lambert-Desktop:/home/fabrice# 
```

---

### Post by Lars Noodén on 2013-11-28
In some cases you might be able to launch sudo with -E to preserve the existing environment variables for the new user.  It looks like Ubuntu's sudoers is set up to allow that.

---

### Post by steeldriver on 2013-11-28
> **fabrice.lambert said:**
> Hi, thanks for looking at this.

The problem is exactly that even though /opt/intel/bin is in both the user's and the super-user's path, sudo cannot find the binary:

```
fabrice@Lambert-Desktop:~$ sudo PATH=$PATH sh -c 'echo $PATH'
[sudo] password for fabrice: 
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/opt/intel/bin
fabrice@Lambert-Desktop:~$ echo $PATH
/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/opt/intel/bin
fabrice@Lambert-Desktop:~$ ifort
ifort: command line error: no files specified; for help type "ifort -help"
fabrice@Lambert-Desktop:~$ sudo ifort
sudo: ifort: command not found
fabrice@Lambert-Desktop:~$ 
```

Any idea what's going on?

I'm not seeing anything in your output that confirms your assertion that /opt/intel/bin is in the superuser's (root's) PATH - what happens if you do

```

sudo sh -c 'echo $PATH'

```
without the PATH=$PATH? what happens if you do
```

sudo PATH=$PATH ifort

```

---

### Post by fabrice.lambert on 2013-11-28
Sorry for all the edits:

fabrice@Lambert-Desktop:~$ sudo -E ifort
sudo: ifort: command not found
fabrice@Lambert-Desktop:~$ sudo PATH=$PATH ifort
sudo: ifort: command not found
fabrice@Lambert-Desktop:~$

---

### Post by fabrice.lambert on 2013-11-28
sudo sh -c 'echo $PATH' does not include /opt/intel/bin.

I thought that if I'm logged in as root and echo $PATH I would get root's PATH, is that not correct?

---

### Post by steeldriver on 2013-11-28
Hmm... how about

```
sudo **env **PATH=$PATH ifort
```

---

### Post by fabrice.lambert on 2013-11-28
YES! That worked: 
fabrice@Lambert-Desktop:~$ sudo env PATH=$PATH ifort
ifort: command line error: no files specified; for help type "ifort -help"
fabrice@Lambert-Desktop:~$

Thanks a lot! I'll mark the thread as solved.
-Fabrice

---

### Post by steeldriver on 2013-11-28
It's not an elegant solution imho - since you have sudo access, have you considered creating a symlink from /opt/intel/bin/ifort to somewhere that *is* on root's PATH (like /usr/local/bin/ifort)?

Do you really need root to run ifort anyway? usually when we build and install programs, it is only the final stage (installing to a system location) that requires root - and that's usually just done with things like 'mkdir' and 'cp' to copy the already-built binaries - rather than running the compiler itself as root.

---

### Post by fabrice.lambert on 2013-11-28
Well, I set the install directory to "/usr/local/netcdf", so I need to run "make install" as sudo because it needs to write the files there. I guess a simlink would be a good idea, but I don't compile things that often...

---

### Post by bab1 on 2013-11-28
> **steeldriver said:**
> It's not an elegant solution imho - since you have sudo access, have you considered creating a symlink from /opt/intel/bin/ifort to somewhere that *is* on root's PATH (like /usr/local/bin/ifort)?

Do you really need root to run ifort anyway? usually when we build and install programs, it is only the final stage (installing to a system location) that requires root - and that's usually just done with things like 'mkdir' and 'cp' to copy the already-built binaries - rather than running the compiler itself as root.

/opt is owned by root:root and the OP hasn't changed any of the subdirectories to accommodate a mortal user ( a logged in user).  This is the most elegant way.  Change the ownership and add the subdirectory path (/opt/<something>) to the users path only.

---

### Post by bab1 on 2013-11-28
> **fabrice.lambert said:**
> Well, I set the install directory to "/usr/local/netcdf", so I need to run "make install" as sudo because it needs to write the files there. I guess a simlink would be a good idea, but I don't compile things that often...

As root you can create a subdirectory of /opt that is owned by the user.  The user can travers the /opt directory to the new subdirectory without changes to the /opt directory itself.  Then you don't need symlinks or the need of sudo or su.  FYI paths are not something related to sudo or su.  The path is a configuration related to the user (root is a user too).

---

### Post by fabrice.lambert on 2013-11-28
Thanks for the clarification on paths, Bab1.

Even though all the files in /opt/intel/bin are owned by root, they all have 777 mode. This way any user can execute them. The need for su or sudo arises from the fact that the install directory set by ./configure is in /usr/local, which is also owned by root:root.
However, I could create a directory in /usr/local owned by the user and install in there; that should indeed remove the need for su or sudo.

---

### Post by bab1 on 2013-11-28
> **fabrice.lambert said:**
> Thanks for the clarification on paths, Bab1.

Even though all the files in /opt/intel/bin are owned by root, they all have 777 mode. This way any user can execute them.

Using 777 is the brute force method.
> 

The need for su or sudo arises from the fact that the install directory set by ./configure is in /usr/local, which is also owned by root:root.
However, I could create a directory in /usr/local owned by the user and install in there; that should indeed remove the need for su or sudo.
From my point of view the mortal user needs to have a workplace to create, not the root user.  I would provide that with a separate directory (a commonly owned directory under /opt/intel/bin and then move the final executable to /usr/local/<something> .  If you want the user to be able to execute the bin or script file then make the group ownership a common to the user owner.  I use the group called: *users*.    This way I can limit the user to executing the script but not allow modification.

---

### Post by steeldriver on 2013-11-28
^^^ agreed - I either build stuff as a 'mortal user' in my homedir, then do 'sudo make install' at the end, or use /usr/local/src which I have set up as

```
drw**s**rwsr-x  7 root **staff** 4096 May 12  2013 src
```

The setgid bit allows users who are in the 'staff' group to create their own directories there to build stuff - again without elevating their permissions. It's kind of oldschool but keeps things tidy.

---

### Post by bab1 on 2013-11-28
> **steeldriver said:**
> ^^^ agreed - I either build stuff as a 'mortal user' in my homedir, then do 'sudo make install' at the end, or use /usr/local/src which I have set up as

```
drw**s**rwsr-x  7 root **staff** 4096 May 12  2013 src
```

The setgid bit allows users who are in the 'staff' group to create their own directories there to build stuff - again without elevating their permissions. It's kind of oldschool but keeps things tidy.

Yes, I kinda miss the wheel group but I've been lazy now that I use Ubuntu. 

The end result is that you allow mortal users to create and install while NOT creating a hole that others could exploit by modifying your code or worse yet substituting their own bin or script files. I kinda miss the wheel group but I've been lazy now that I use Ubuntu.

---

### Post by fabrice.lambert on 2013-11-28
Yes, the 777 seems a bit over-the-top. It's how the installer set things up, I didn't change that myself.

As for the rest, I agree that it is safer, but I am working on my desktop computer where I am the sole user, so I only need to limit myself from doing anything stupid :-)

---

### Post by bab1 on 2013-11-28
> **fabrice.lambert said:**
> Yes, the 777 seems a bit over-the-top. It's how the installer set things up, I didn't change that myself.

As for the rest, I agree that it is safer, but I am working on my desktop computer where I am the sole user, so I only need to limit myself from doing anything stupid :-)
I'd worry about the package maintainer if that is how lazy they are.  In the end, as you say you only need to protect you from yourself.  I have had experiences where I was glad I took the time to set things up properly.  It is just habit now.

---

