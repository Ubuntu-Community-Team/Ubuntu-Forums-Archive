---
title: "xhost error on Ubuntu 22.04 in Windows11 subsystem"
date: 2023-07-18
forum: General Help
---

### Post by swania on 2023-07-18
I have Ubuntu 22.04 installed on Windows11.
I'm now running command 

[HTML]xhost +SI:localuser:root[/HTML]
[HTML]xhost:  unable to open display "localhost:1"[/HTML]

I tried almost all solutions I can find online, and the problem continous. I'm doing so cause I need to install Matlab 2023 on my Ubuntu. 

Solutions I tried:


[HTML] xeyes
Error: Can't open display: localhost:1
echo $DISPLAY $XAUTHORITYlocalhost:1
xdpyinfoxdpyinfo:  unable to open display "localhost:1".[/HTML]

Any suggestion would help! Thanks in advance.

---

### Post by TheFu on 2023-07-18
Don't use root.  Ubuntu is setup never to have any GUI logins with the root account.

Also, if you want to run X/Windows, you'll need for the computer you sit behind to be running an X/Server.  Remote systems are running X/Client software ... which is another term for any GUI program.

---

### Post by MAFoElffen on 2023-07-19
What "Edition" of Windows 11 do you have with what build#?

---

