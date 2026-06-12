---
title: "Need help, &quot;bash fork bomb&quot; ? Terminal command"
date: 2007-05-13
forum: General Help
---

### Post by ubuntu27 on 2007-05-13
I typed the following into my Konsole (Terminal) 

[COLOR=DarkRed]**Do not try the following command on your computer unless you know what you are doing:**[/COLOR]

```

 :(){ :|:& };:
``` for a friend was asking me if it was true that this command will "kill" or make Linus OS unresponsive. I thought that was ridiculous so I tried it.

At first it seemed that nothing happened. But then I realized that my computer, Kubuntu become rather slow... slower than usual.

Looks like that command created multiple random process and consumes a lot of RAM which makes the computer unresponsive... (specially if you have less RAM)


**How can I fix this problem?**

Visit this site for a little reading about that command: 

[http://www.euglug.org/pipermail/euglug/2005-August/004338.html](http://www.euglug.org/pipermail/euglug/2005-August/004338.html)

---

### Post by matthew on 2007-05-14
Two comments: 

-If you have any thoughts about how to help this guy, please chime in.

-Do not, under any circumstances, type the above in your terminal.

---

### Post by heimo on 2007-05-14
Reading and ways to prevent users to forkbomb your system:
[http://wiki.craz1.homelinux.com/index.php/Linux:Security:Forkbomb](http://wiki.craz1.homelinux.com/index.php/Linux:Security:Forkbomb)
[http://www.napolifirewall.com/Forkbombing.htm](http://www.napolifirewall.com/Forkbombing.htm)

---

### Post by Subban on 2007-05-14
A fast fix :

```
gksudo gedit /etc/security/limits.conf
```

and add this following line:

```
*           	 hard    nproc           512
```

Credit for this solution goes to Offhand on these forums posted [here]("http://ubuntuforums.org/showthread.php?t=375267")

---

