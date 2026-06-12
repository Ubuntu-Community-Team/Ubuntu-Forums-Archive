---
title: "sudoers problem, no sudo access"
date: 2017-02-09
forum: General Help
---

### Post by webmanoffesto on 2017-02-09
I'm trying to resolve a boot problem. While attempting to resolve that I ran into a "sudoers" problem. [https://ubuntuforums.org/showthread.php?t=2351994&page=2](https://ubuntuforums.org/showthread.php?t=2351994&page=2)
 Please help me to resolve this.
```

tom@TomsAsusK55A:~$ ls -al /etc/sudoers
-rwxrwxrwx 1 root root 669 May  3  2015 /etc/sudoer

tom@TomsAsusK55A:~$ sudo
sudo: /etc/sudoers is world writable
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin

```

> **Bashing-om said:**
> webmanoffesto; Ouch !
should be:
```

sysop@x1604:~$ ls -al /etc/sudoers
-r--r----- 1 root root 755 Aug 17 08:20 /etc/sudoers
sysop@x1604:~$

```


---

### Post by Bashing-om on 2017-02-09
webmanoffesto; Hey;

Think we also want to see the sudo config file:
Hold Shift immediately while booting so that you get the GRUB screen. Select the recovery mode. Choose to drop to a root terminal.
As you do not have copy/paste in this terminal we can transfer the file to a pastebin site:
```

cat /etc/sudoers | nc termbin.com 9999

```
the result is a URL back in terminal. pass this link back here .

We get an idea of what needs to be done.

[INDENT][INDENT]break 'buntu
[INDENT][INDENT][INDENT]put the pieces back together
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sisco311 on 2017-02-09
If your user is still in the admin group, then you can use pkexec to restore the file's permissions:
```
pkexec chmod 0440 /etc/sudoers
```

---

### Post by webmanoffesto on 2017-02-09
Problem solved, thanks
```
tom@TomsAsusK55A:~$ pkexec chmod 0440 /etc/sudoers
tom@TomsAsusK55A:~$ ls -al /etc/sudoers
-r--r----- 1 root root 669 May  3  2015 /etc/sudoers
```

---

