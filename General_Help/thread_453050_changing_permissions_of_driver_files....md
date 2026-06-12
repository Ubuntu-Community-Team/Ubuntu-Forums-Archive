---
title: "changing permissions of driver files...?"
date: 2007-05-23
forum: General Help
---

### Post by electrifice on 2007-05-23
I have a Sony VAIO for which I have loaded the sony_acpi module. The module loads on its own and I believe it creates the folder /proc/acpi/sony/ upon booting up. I need to use a file from that directory through the command "echo 'n' > brightness" (where n is a number) to set the brightness. However, each time the computer reboots, the permissions on that file are reset and I have to chown it on each bootup. How can I automate it?

---

### Post by cantormath on 2007-05-24
> **electrifice said:**
> I have a Sony VAIO for which I have loaded the sony_acpi module. The module loads on its own and I believe it creates the folder /proc/acpi/sony/ upon booting up. I need to use a file from that directory through the command "echo 'n' > brightness" (where n is a number) to set the brightness. However, each time the computer reboots, the permissions on that file are reset and I have to chown it on each bootup. How can I automate it?

First, if you want to run something and there is a permissions problem, use sudo
```
 :~$ sudo "echo 'n' > brightness"
```you are probably better off not chowning stuff like that.....its not to safe.  If you want it to run at boot time you have to add it to /init.d/
Here is the idea:
[http://www.debian-administration.org/articles/28](http://www.debian-administration.org/articles/28)
[http://www.linux.com/article.pl?sid=06/01/03/1728227](http://www.linux.com/article.pl?sid=06/01/03/1728227)
Im not sure you just want to copy that script into your /etc/init.d file, but I think you can make a link to the script, put it in /etc/init.d, and it should load at boot.
or you can write a script that runs a command that runs the script in question and then put it in /etc/init.d.  Make sure you look at the howto, there are a few steps.

hope that helps..

---

### Post by electrifice on 2007-05-24
Yes, I understand the potential "harm" in chowning a file like that... but what I really want to do is create a keyboard shortcut that will invoke the "sudo echo..." command. My VAIOs fn keys don't work and its just much easier to assign an alternate shortcut key I can use to adjust the brightness. The only problem is that when I'm using a shortcut to "sudo echo" I don't want to have to put in a password.
How it works is that there is another file called sonybright.sh (I forget where exactly), and at this point I can just say "sudo sh sonybright.sh" and this file will increase the value in the "brightness" file... but first I have to chmod 777 (or chown) the /proc/acpi/sony/brightness file. So in either case I'm having to change the permissions of that file because even with the "sudo" it returns with an "operation not permitted" (even with a chmod 755). This behavior is rather odd and beyond my understanding... I appreciate any help. Below is a diagram of what I'm trying to do...

First scenario:
[Press Ctrl+F5] -> [xbindkeys invokes "sh sonybright.sh"] -> ["sonybright.sh" script increases the value in "/proc/acpi/sony/brightness"] -> [Error: "Operation not permitted"]

Alternate scenario:
[type 'sudo echo 'n' > /proc/acpi/sony/brightness' after logging in] -> [type password] -> [Error: "Operation not permitted"]

Problem: doesn't work unless I chown or chmod 777 'brightness'
Solution: ??

---

