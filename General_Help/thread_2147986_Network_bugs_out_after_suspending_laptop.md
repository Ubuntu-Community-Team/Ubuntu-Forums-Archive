---
title: "Network bugs out after suspending laptop"
date: 2013-05-23
forum: General Help
---

### Post by Bro0kLyNz on 2013-05-23
I'm using Ubuntu 12.04 on a Toshiba Satellite C655. Ubuntu works just fine. So far I've only encountered two problems, one of which I have already solved (magnet links). The problem I'm encountering now is, whenever the laptop is resumed from suspend mode my network bugs out. I'll try and explain as best I can, but I'm not sure what's going on.

I can suspend the laptop for 10 minutes and resume it without any issues. If the laptop is left in suspend mode for more than 10 minutes, on resume it can't connect to any network (wireless, haven't tested wired) I have to restart for the laptop to connect to my router. Basically, ubuntu asks to enter the password for the network connection.. I enter the password, it attempts to connect, fails and asks me to enter the password again. This goes on for sometime before I decided to restart.

On startup it connects to my router without problems. Which is why I think the issue is when the computer stays in suspend mode for too long. Any ideas?


EDIT:
It's not a major issue. because Ubuntu is so fast, I don't mind restarting. but it would be nice to fix this.

---

### Post by HiImTye on 2013-05-23
does
```
pkill network-manager; network-manager
``` fix it?

---

### Post by Bro0kLyNz on 2013-05-23
I'll try it when it happens again. I'll let you know if it works. (it will take some time to recreate it)

btw, what will the command do exactly?

---

### Post by HiImTye on 2013-05-23
it stops and then starts network manager
pkill kills a process by name and the ; tells the shell to start a new command irrespective of the output of the previous command

---

### Post by Bro0kLyNz on 2013-05-23
Alright thanks. I haven't tested it out yet because I'm busy, but I'm sure this will work. Thanks for the command :)

---

### Post by Bro0kLyNz on 2013-05-23
command not found :(

edit:
this works
```
sudo service network-manager restart
```

---

