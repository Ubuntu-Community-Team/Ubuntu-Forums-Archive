---
title: "Not updating"
date: 2013-08-27
forum: General Help
---

### Post by josh17 on 2013-08-27
For some reason my ubuntu refuses to update. it says something is currently using the file it needs in order to preform the update, and i think it might be the "searching" thing in the software center. But that has been stuck on "applying changes" since yesterday aand the progress bar hasn't moved. I've tried resetting my computer to no avail. what do I need to do?!? !D:

---

### Post by ian-weisser on 2013-08-27
Please provide the entire, exact message.

---

### Post by josh17 on 2013-08-27
"Not all updates can be installed
Run a partial upgrade, to install as many updates as possible
 This can be caused by
  *A previous upgrade which didn't complete
 *Problems with some of the installed software
  *Unofficial software packages not provided by Ubuntu
  *Normal changes of pre-released versions of ubuntu "

*Clicks partial upgrade*

"Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first."

---

### Post by ian-weisser on 2013-08-27
> **josh17 said:**
> 
"Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first."

First things first.
What other applications, terminal windows, updates, and package managers do you have open?
Only one can be working at a time. If you try to run more than one, you get that message.
> **josh17 said:**
> 
"Not all updates can be installed
Run a partial upgrade, to install as many updates as possible


Tell us **everything** you know or suspect about previous update problems.

---

### Post by josh17 on 2013-08-27
At the time i Had software center open, but i get that message when literally no other window is open.

---

### Post by ian-weisser on 2013-08-27
Please open a terminal, and try the following command. Post the entire output here inside code tags.
```
ls -l /var/lib/dpkg/lock
```

Please tell us **everything** you know or suspect about previous update problems, including aborted updates, power loss or network loss during updates, etc.

---

### Post by josh17 on 2013-08-27
> **ian-weisser said:**
> Please open a terminal, and try the following command. Post the entire output here inside code tags.
```
ls -l /var/lib/dpkg/lock
```

Please tell us **everything** you know or suspect about previous update problems, including aborted updates, power loss or network loss during updates, etc.

The output was 
```
-rw-r----- 1 root root 0 Aug 27 16:33 /var/lib/dpkg/lock
```
And as for aborted updates, all that comes to mind is the installtion of a program on the software center that I had to shut down in the middle because my computer froze, but the program is on my computer so i'd assume it installed correctly beforehand.

---

### Post by ian-weisser on 2013-08-27
1) Log out of your system.

2) Then log back in.

3) Open a terminal. Try the commands
```
sudo apt-get update
sudo apt-get upgrade
```

4) If the commands work without error, then close the terminal window and wave your hands in happiness. Your problem should be fixed.

5) If you get another "unable to get lock file" message, then try the command:
```
sudo rm /var/lib/dpkg/lock
```
Then repeat steps 3 and 4.

6) If you are STILL getting an error message, post the entire terminal session here so we can see what worked, what went wrong, and those very-helpful error messages.

---

### Post by josh17 on 2013-08-27
> **ian-weisser said:**
> 1) Log out of your system.

2) Then log back in.

3) Open a terminal. Try the commands
```
sudo apt-get update
sudo apt-get upgrade
```

4) If the commands work without error, then close the terminal window and wave your hands in happiness. Your problem should be fixed.

5) If you get another "unable to get lock file" message, then try the command:
```
sudo rm /var/lib/dpkg/lock
```
Then repeat steps 3 and 4.

6) If you are STILL getting an error message, post the entire terminal session here so we can see what worked, what went wrong, and those very-helpful error messages.

```
josh@ubuntu:~$ sudo apt-get update
[sudo] password for josh: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
josh@ubuntu:~$ sudo apt-get upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
josh@ubuntu:~$ sudo rm /var/lib/dpkg/lock
josh@ubuntu:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
josh@ubuntu:~$ sudo dpkg --configure -a
Setting up sandboxgamemaker (2.7.1+dfsg-1) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing sandboxgamemaker (--configure):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 sandboxgamemaker
josh@ubuntu:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
```

---

### Post by ian-weisser on 2013-08-27
There are two problems in that session.

First, there is another lock file. Let's get rid of it first.
```
sudo rm /var/lib/apt/lists/lock
```

Second, there is an unconfigured package. Perhaps from that disrupted install?
```
sudo dpkg --configure sandboxgamemaker
```

Finally, let's see if it works:
```
sudo apt-get update
sudo apt-get upgrade
```

As before, please post the entire session so we can see errors.
We're making progress, and you are doing great.

---

### Post by josh17 on 2013-08-27
> **ian-weisser said:**
> There are two problems in that session.

First, there is another lock file. Let's get rid of it first.
```
sudo rm /var/lib/apt/lists/lock
```

Second, there is an unconfigured package. Perhaps from that disrupted install?
```
sudo dpkg --configure sandboxgamemaker
```

Finally, let's see if it works:
```
sudo apt-get update
sudo apt-get upgrade
```

As before, please post the entire session so we can see errors.
We're making progress, and you are doing great.

So it's at this right now:
```
[sudo] password for josh: 
josh@ubuntu:~$ sudo dpkg --configure sandboxgamemaker
Setting up sandboxgamemaker (2.7.1+dfsg-1) ...
Cleaned old data
--2013-08-27 18:49:23--  http://sandboxgamemaker.com/sandbox/PlatinumArtsSandbox2.7.1Multiplatform.zip
Resolving sandboxgamemaker.com (sandboxgamemaker.com)... 173.236.241.215
Connecting to sandboxgamemaker.com (sandboxgamemaker.com)|173.236.241.215|:80... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: http://www.sandboxgamemaker.com/sandbox/PlatinumArtsSandbox2.7.1Multiplatform.zip [following]
--2013-08-27 18:49:34--  http://www.sandboxgamemaker.com/sandbox/PlatinumArtsSandbox2.7.1Multiplatform.zip
Resolving www.sandboxgamemaker.com (www.sandboxgamemaker.com)... 173.236.241.215
Connecting to www.sandboxgamemaker.com (www.sandboxgamemaker.com)|173.236.241.215|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

replace PlatinumArtsSandbox2.7.1/bin/jpeg.dll? [y]es, [n]o, [A]ll, [N]one, [r]ename: y


```
and this has happened once before when I tried to update, it took me to this kinda thing and when i presses y it didnt do anything and jus stayed like that. and it's doing that now as well.

---

### Post by ian-weisser on 2013-08-27
If the terminal window won't respond, first try CTRL+C to abort the running job and return to a command prompt.
If that does not work, then close (really close, not minimize) the terminal window. And open a new terminal window.

Do you use sandboxgamemaker?

> Description-en: 3D game maker and 3D game design program
 Platinum Arts Sandbox is an open source, easy-to-use, standalone 3D game
 maker and 3D game design program. It is currently based on the Cube 2
 engine used in schools around the world that allows kids and adults to
 create their own video games, worlds, levels, adventures, and quests,
 even cooperatively. The goal is to make it accessible to kids but also
 powerful enough for full game projects.

If you don't use it, try the command [B]sudo apt-get remove sandboxgamemaker
[/B]
If you do use it, remove it anyway (temporarily). After the package manager problem is fixed, we can reinstall it with the command **sudo apt-get install sandboxgamemaker**

After removing, please do a **sudo apt-get update **and **sudo apt-get upgrade** again.

And, again, please show us what happens.

---

### Post by josh17 on 2013-08-28
> **ian-weisser said:**
> If the terminal window won't respond, first try CTRL+C to abort the running job and return to a command prompt.
If that does not work, then close (really close, not minimize) the terminal window. And open a new terminal window.

Do you use sandboxgamemaker?



If you don't use it, try the command [B]sudo apt-get remove sandboxgamemaker
[/B]
If you do use it, remove it anyway (temporarily). After the package manager problem is fixed, we can reinstall it with the command **sudo apt-get install sandboxgamemaker**

After removing, please do a **sudo apt-get update **and **sudo apt-get upgrade** again.

And, again, please show us what happens.

```
josh@ubuntu:~$ sudo apt-get remove sandboxgamemaker
[sudo] password for josh: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


```

---

### Post by josh17 on 2013-08-28
and now it won't let me startup at all, it says [sdb] asking for cache failed 

[sdb] assuming drive cache: write through

and before says something about a graphic driver failing to start (its scrolled down so I can't get the exact message)

this has happened before and I hand to reinstall Ubuntu which took a long time, rather not go through that again

---

### Post by ian-weisser on 2013-08-28
> **josh17 said:**
> [sdb] assuming drive cache: write through
Usually not a big problem, a kernel message caused when some storage hardware does not respond properly to probing...often by (poor) design.


> **josh17 said:**
> and before says something about a graphic driver failing to start (its scrolled down so I can't get the exact message)
See if you can find the error messages in /var/log/syslog or /var/log/dmesg

Your graphic driver failing to start may be completely unrelated to you package manager problem, you should open a new thread on that. Or they could both be symptoms of another issue. The last time my graphics failed was 2006 - twice in a short period for unknown reason seems quite unusual.

---

### Post by josh17 on 2013-08-28
how do I check for error messages when I can't log in?

---

### Post by josh17 on 2013-08-28
> **ian-weisser said:**
> 
Your graphic driver failing to start may be completely unrelated to you package manager problem, you should open a new thread on that.

I have made a thread in this issue the first time it happened, 5 days ago. no one posted a solution on it.

---

### Post by josh17 on 2013-08-28
I somehow managed to make it work, thanks for all the help you gave me!

---

