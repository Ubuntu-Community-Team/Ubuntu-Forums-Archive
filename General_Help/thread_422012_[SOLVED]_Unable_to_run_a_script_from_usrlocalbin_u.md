---
title: "[SOLVED] Unable to run a script from /usr/local/bin unless su?"
date: 2007-04-24
forum: General Help
---

### Post by rrwo on 2007-04-24
Here's a stumper. I have a shell script that when put in /usr/local/bin, I get an error. Bash says no such file or directory.  But if I run it sudo, then it runs.

If I put the same script in /usr/bin, I can run it without sudo.

I've checked the perms. World has read rights to it.  And /usr/local/bin is in my path.

Why? That's just weird.

FWIW, I am running Feisty.

---

### Post by dcstar on 2007-04-24
> **rrwo said:**
> Here's a stumper. I have a shell script that when put in /usr/local/bin, I get an error. Bash says no such file or directory.  But if I run it sudo, then it runs.

If I put the same script in /usr/bin, I can run it without sudo.

I've checked the perms. World has read rights to it.  And /usr/local/bin is in my path.

Why? That's just weird.

FWIW, I am running Feisty.

Read rights are not Execute rights.

---

### Post by Azakus on 2007-04-24
Easy fix
```
sudo chmod a+x /usr/local/whateverprogramyouwanttouse
```

---

### Post by GuitarRocker2562 on 2007-04-24
what is a+x do?

---

### Post by DoktorSeven on 2007-04-24
a = all users (world)
+x = add executable permissions

---

### Post by rrwo on 2007-04-25
> **dcstar said:**
> Read rights are not Execute rights.

It had the execute bit set, so that's not the problem.

---

### Post by rrwo on 2007-04-25
> **Azakus said:**
> Easy fix
```
sudo chmod a+x /usr/local/whateverprogramyouwanttouse
```

No, it doesn't fix it.

FYI, the error that I get is:
```
bash: /usr/bin/proofgeneral: No such file or directory
```
(proofgeneral is the script).

Strange thing is that it's in /usr/local/bin, not /usr/bin.  I don't get any improved messages adding the -v flag to it.  Adding an echo statement right after the shebang doesn't help: it's not run.  So I think there's a problem with it not being found.

---

### Post by tom56 on 2007-04-25
You need to either move the script to /usr/bin or add /usr/local/bin to your $PATH.

[http://www.troubleshooters.com/linux/prepostpath.htm#_singleuser](http://www.troubleshooters.com/linux/prepostpath.htm#_singleuser)

EDIT: Sorry, didn't read the original post properly - you said you have it in your $PATH already

---

### Post by rrwo on 2007-04-25
I should add that if I explicitly state /usr/local/bin/script, then the program runs.

I think the problem is with bash completion, or something that tells bash it's in the wrong path.

---

### Post by rrwo on 2007-04-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/bash/+bug/109927](https://bugs.launchpad.net/ubuntu/+source/bash/+bug/109927) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This has nothing to do with permissions. It's a bug with /etc/bash_completion.

When I comment out the use of it in my .bashrc file, the problem goes away.

---

