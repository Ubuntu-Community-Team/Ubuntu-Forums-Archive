---
title: "Firefox could not start because /bin/which removed itself"
date: 2022-01-25
forum: General Help
---

### Post by KBar on 2022-01-25
Good morning to all!

Although, it wasn't particularly good for me. I turned on my laptop, the desktop started as usual. I launch frequently used apps through keyboard shortcuts. I pressed Super+W to launch Web Browser, which is set to Firefox, and it greeted me with an error message that it couldn't do that due to some input/output error. Launching it from the Whisker Menu did not change the situation. I figured it would be better to do that through the shell, since it tends to be more verbose and transparent with its output. Here is where the "fun" begins. Let's take a look at relevant lines because I also tried updating in-between and looked into some of the logs:

```
08:12:50 ~ firefox
/usr/bin/firefox: 1: which: not found
08:13:11 ~ type -a firefox
firefox is /usr/bin/firefox
firefox is /bin/firefox
08:13:15 ~ firefox
/usr/bin/firefox: 1: which: not found
08:13:41 ~ journalctl --follow
^C
08:13:52 ~ sudo apt update
08:16:36 ~ firefox
/usr/bin/firefox: 1: which: not found
08:17:02 ~ which -a firefox

Command 'which' not found, but can be installed with:

sudo apt install debianutils

08:17:16 ~ less /var/log/apt/history.log
08:17:57 ~ which 

Command 'which' not found, but can be installed with:

sudo apt install debianutils

08:18:02 ~ type -a which
bash: type: which: not found
08:18:17 ~ dpkg -L debianutils | less
08:18:25 ~ ls /bin/which
ls: cannot access '/bin/which': No such file or directory
08:18:50 ~ less /var/log/dpkg.log
08:19:46 ~ sudo apt reinstall debianutils
```

I looked into both *history.log* and *dpkg.log*, and the *debianutils* package wasn't touched at all. The last entries in my *.bash_history* concerning **which** are these:
```
1186  dpkg -S $(which -a paplay)
1797  dpkg -S $(which -a lesspipe)
1807  dpkg -S $(which -a pdftotext)
```

The last entries from yesterday are:
```
 1985  fre
 1986  free
 1987  top
 1988  x
 1989  top
 1990  x
 1991  top
 1992  man pkill
 1993  top
 1994  x
```

As you can see, nothing of relevance in here as well apart from a few x's, which is just an alias to the exit command. As soon as I reinstalled the *debianutils* package, everything went back to normal and Firefox launches with no errors now.

The question, of course, is: what the hell happened? Why did **which** decide to purge itself? Who or what caused its removal? Me? Never! At least I hope so. There were no commands like **sudo rm -rf /bin/which** issued though, that's for sure.

---

### Post by Impavidus on 2022-01-26
I'm quite sure which didn't remove itself. Although application can do that, I don't think which can remove anything and to remove itelf it would have to run as the root user.

Maybe something bad happened while installing an upgrade. Maybe it's a hard drive problem.

---

### Post by KBar on 2022-01-26
> **Impavidus said:**
> I'm quite sure which didn't remove itself. Although application can do that, I don't think which can remove anything and to remove itelf it would have to run as the root user.
I'm 100% positive as well but it happened. I was very surprised and confused.

> Maybe something bad happened while installing an upgrade.
Hmm, there were no updates the day before, only installed and removed* gnome-terminal* a couple of times:
```

Start-Date: 2022-01-25  14:49:02
Commandline: apt install gnome-terminal
Requested-By: kbar (1000)
Install: nautilus-extension-gnome-terminal:amd64 (3.36.2-1ubuntu1~20.04, automatic), libnautilus-extension1a:amd64 (1:3.36.3-0ubuntu1.20.04.1, automatic), gnome-terminal-data:amd64 (3.36.2-1ubuntu1~20.04, automatic), gnome-terminal:amd64 (3.36.2-1ubuntu1~20.04)
End-Date: 2022-01-25  14:49:06

Start-Date: 2022-01-25  14:51:38
Commandline: apt purge gnome-terminal
Requested-By: kbar (1000)
Purge: nautilus-extension-gnome-terminal:amd64 (3.36.2-1ubuntu1~20.04), gnome-terminal:amd64 (3.36.2-1ubuntu1~20.04)
End-Date: 2022-01-25  14:51:41

Start-Date: 2022-01-25  14:52:24
Commandline: apt autopurge
Requested-By: kbar (1000)
Purge: libnautilus-extension1a:amd64 (1:3.36.3-0ubuntu1.20.04.1), gnome-terminal-data:amd64 (3.36.2-1ubuntu1~20.04)
End-Date: 2022-01-25  14:52:24

```

I doubt that these four packages could affect *debianutils* or **which** itself. 

 > Maybe it's a hard drive problem.
You might be onto something. It's an SSD and I checked it with *smartmontools* not too long ago. It did not detect any problems or defects, though. Is that tool reliable or should use something else?

---

### Post by Impavidus on 2022-01-27
None of those packages affects which, which can only be removed by removing the package debianutils, by removing the file without using the package manager, by bugs or malware or by filesystem damage.

Smartmontools is reliable, but never gives guarantees. No tool can. So, if this just happens once, I'd just leave it at that. Don't forget your backups though. If unexplained missing files happen more often, it's time to worry.

---

