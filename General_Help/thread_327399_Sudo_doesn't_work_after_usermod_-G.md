---
title: "Sudo doesn't work after usermod -G"
date: 2006-12-29
forum: General Help
---

### Post by mhueting on 2006-12-29
Hello,

I'm trying to configure CUPS, and in the process I wanted to add my username to the lpadmin group. I did sudo usermod -G lpadmin [username]. After this command, my complete sudo stopped working. If I type "sudo gvim", it just gives me back my prompt, and nothing happens.

I have no clue how to get back my sudo :( I can't live without it!

---

### Post by bapoumba on 2006-12-29
Hi,
what do **groups** and **cat /etc/group |grep <your_username>** return ?

---

### Post by mhueting on 2006-12-29
Fixed it.

I booted into recovery mode, and said "cat /etc/group | grep admin". I wasn't in the admin group, so I did "adduser [username] admin" and I rebooted. Worked great :D

---

### Post by bapoumba on 2006-12-29
Nice, that's what I was going to suggest depending on your answer ;)

---

### Post by whizbaby on 2006-12-29
The way to do it is

[B]sudo adduser <user> <group>
[/B]
the usermod command (if you really only did what you wrote) should have removed you from ALL groups not equal to lpadmin (according to its manual), so better check if you are in any other group...

---

