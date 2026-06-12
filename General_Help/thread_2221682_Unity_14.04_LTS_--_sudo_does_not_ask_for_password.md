---
title: "Unity 14.04 LTS -- sudo does not ask for password"
date: 2014-05-03
forum: General Help
---

### Post by sadhu44 on 2014-05-03
I think there's something wrong with my setup. Yes, I do have a password, I am required to enter it on login, software update, etc.

I don't recall setting these variables. Perhaps a miscreant has invaded my machine.  Example:```
sadhu@desktop:~$ whoami
sadhu
sadhu@desktop:~$ sudo su
root@desktop:/home/sadhu# 
```
When I entered "sudo su" there was a quick flash of something being written to terminal, then erased. Elsewhere I was asked to report the result of these commands. Here they are again. I don't know what they mean.```
sadhu@desktop:~$ sudo -l
Matching Defaults entries for sadhu on desktop:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User sadhu may run the following commands on desktop:
    (ALL : ALL) ALL
    (ALL) NOPASSWD: ALL
    (ALL) NOPASSWD: ALL
    (ALL) NOPASSWD: ALL
sadhu@desktop:~$
``` Should I run visudo and change those lines in sudoers to ALL: ALL? 

I uninstalled all that garbage cannonical spyware stuff under the dash (Amazon, automatic web searches, etc.)--did this perhaps broke something? 

-sadhu

---

### Post by LastDino on 2014-05-03
Well, technically speaking only keeping first line and getting rid of the all 3 following it which actually mention ''nopasswd'' and saving the file should do that job, but** I would wait for someone more knowledgeable to guide you through process. I'm fairly new to this as well.**

What I'm curious about is how those values changed (As you are as well), uninstalling the things you mentioned don't do anything of this sort. I've uninstalled them too.
 Did you install something from some PPA source recently as sudo? Or followed some command guide to do something from some website? 
Do you've someone else who also has access to your administrative account and probably changed it?

/this is simply curiosity talking, don't get mad if I'm wasting time.lol

---

