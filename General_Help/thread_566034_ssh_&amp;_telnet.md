---
title: "ssh &amp; telnet"
date: 2007-10-03
forum: General Help
---

### Post by xGutsAndGloryx on 2007-10-03
i am wanting to learn how to use ssh & telnet. Can you do ssh & telnet from a linux pc to windows pc? if so how?

---

### Post by thelocust on 2007-10-03
I know you can ssh from windows to linux using a program called winscp.

---

### Post by xGutsAndGloryx on 2007-10-03
does the program work in linux?

---

### Post by thelocust on 2007-10-03
I dont think so the computer you are hooking up to has to be running ssh to get a connection and I dont know how that works on windows. I'm sure it's possible.

---

### Post by thelocust on 2007-10-03
Thers a program called PuTTY that works in windows and linux. No idea what the install intails though.

---

### Post by bodhi.zazen on 2007-10-03
[uwiki]SSHHowto[/uwiki]

And for security : [uwiki]AdvancedOpenSSH[/uwiki]

From Linux you need to use putty, an ssh client.

From Linux -> Windows you would need to install a ssh server on Windows. I would advise cygwin

From linux -> linux, all command line 

ssh user@ip
scp user@ip:/file_to_copy /home/user

And on ...

I would NOT telnet due to security concerns (ssh encodes data)

---

### Post by xGutsAndGloryx on 2007-10-03
The only reason i am wanting to learn telnet is a job i'm applying for request it.

---

### Post by bodhi.zazen on 2007-10-03
OK, see this link then : [http://www.ubuntugeek.com/setting-up-a-telnet-server-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-a-telnet-server-in-ubuntu.html)

And GOOD LUCK with the job :twisted:

---

