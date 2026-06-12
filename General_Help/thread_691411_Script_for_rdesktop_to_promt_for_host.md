---
title: "Script for rdesktop to promt for host"
date: 2008-02-08
forum: General Help
---

### Post by cyberblade3001 on 2008-02-08
Ok-I run Ubuntu on my main machine-but I often have to log in to Windows machines and servers.

I have created Launchers on my desktop in the following fashion:

Type: Application in terminal
Name: rdesktop-$server
Command:  rdesktop -u $username -d $domain -p $password $server

now this of course means I have one for each server. I want to have one launcher that will keep all the variables except $server. So that upon launching it would prompt me for $server, I would type that in-then it would log me in to it with the standard login ($username, $domain, $password). 

How do I do that?

---

### Post by SpaceTeddy on 2008-02-09
don't know if you want to hear this... but i usually use tsclient to do these things. It has a few quirks, but it let's you configure profiles for different machines and saves them.

---

