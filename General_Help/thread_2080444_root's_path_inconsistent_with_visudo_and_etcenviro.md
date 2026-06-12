---
title: "root's path inconsistent with visudo and /etc/environment in 12.04"
date: 2012-11-04
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2012-11-04
```
root@ubuntu:~# shutdown -h now
Command 'shutdown' is available in '/sbin/shutdown'
The command could not be located because '/sbin' is not included in the PATH environment variable.
This is most likely caused by the lack of administrative privileges associated with your user account.
shutdown: command not found
root@ubuntu:~# echo $PATH
/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games
root@ubuntu:~# 

```Content of /etc/environment:
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```sudoers, read with visudo, contains this line:
```
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"
```The file "shutdown" is in /sbin. Pcmanfm shows it as a "shared library" rather than an executable. There is no directory "/sbin/shutdown/". Whereis also finds shutdown in /sbin.

"sudo shutdown -h now" or with -r works fine from a regular user terminal.

This makes no sense to me unless it's a bug or some kind of file corruption. Am I missing something?

---

### Post by Dreamer Fithp Apprentice on 2012-11-04
It's not just shutdown. Synaptic is the same story. In the user account the .desktop file for synaptic contains the same command that is in the menu shortcut in lucid, synaptic -pkexec, but the menu entry doesn't work but I found "sudo synaptic" works fine. That and problems with bootcd and remastersys got me to looking at permissions more closely. By using the taboo root account I was able to determine the problems may not stem from permissions per se but from an improper path for root and or improper "secure path", despite the fact the only 2 files I know of that should set the root path (see above) have the right path.  I've spent days trying to get an lxde environment working RIGHT as opposed to 90% right under Precise and it just ain't happening. The trouble with 90% right is that while I can get around stuff like the dysfunctional shutdown button (I strongly suspect that's the same permissions/path problem) by using the command line there are still aps I can't get to work. I've reinstalled several times. I'm about ready to give up on Precise and try again with some other distro. In which case I'll be giving up days of work tweaking this system. Any ideas?

---

### Post by spjackson on 2012-11-04
I haven't tried to install LXDE on Ubuntu Precise. I did that on Lucid, and although it basically worked, it wasn't as smooth as installing Lubuntu. I don't have any significant issues with Lubuntu Precise which I use on my main work laptop.

The issues you are experiencing with root/sudo PATH are not normal. It is odd that your problems persist after reinstalling.

There are other elements that combine in setting PATH, including /etc/login.defs and I'm not that familiar with how these hang together. One factor that can confuse matters is that if you do:
```

sudo bash

```
it executes your own .bashrc, not ~root/.bashrc . This can be a surprise.

I don't expect that this will help you much, I'm afraid.

---

### Post by Dreamer Fithp Apprentice on 2012-11-04
Thanks, spjackson.
Interesting stuff even if it doesn't immediately point to a solution.  What fun, another config file to fiddle with! It contains these 2 lines that seem pertinent:
```
ENV_SUPATH    PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
ENV_PATH    PATH=/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games

```So it doesn't SEEM to be the problem. 

I was already downloading Lubuntu 12.10 when I opened your reply. One of my theories is that I have some unmet dependency issue with some lib or program that hasn't been properly indicated as a depend and that it hasn't been noticed because EVERYBODY has it (except for masochists that start with the mini iso like me)  I'd prefer the LTS version but I couldn't find it [added by edit later: mea culpa, mea downright dumbassa. I found it.]. If I can't get this working in the next few hours I'm giving up on Ubuntu variants. Spent too much time on it already. PClinuxOS does everything I want with no trouble but I was hankering to put together a similar system in a 64 bit version. I might try a plain Debian.

---

