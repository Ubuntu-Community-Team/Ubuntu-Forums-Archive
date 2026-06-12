---
title: "Nitroshare in Ubuntu 20.04"
date: 2020-10-07
forum: General Help
---

### Post by Nosphky on 2020-10-07
Did anybody get nitroshare working in 20.04 ?

I had it working fine in 18.04 and it proved very useful to pass files between a linux box and a W10 box with both on the same wifi network.

---

### Post by TheFu on 2020-10-07
Is there a reason that sftp can't be used?  It is pretty trivial to setup and 1000x more secure than most other file transfer methods.

On the Windows machine, use either Filezilla or WinSCP to connect into the Linux system. All the Linux machine needs is a normal openssh-server install.  **sudo apt install ssh fail2ban** is the install and setup and security single-command.  You can enable and run a firewall if you like, but fail2ban will automatically block failed login attempts for ssh, scp, sftp, sshfs, rsync, rdiff-backup and 50 other ssh-based tools.  All of them share the ssh port, which defaults to 22/tcp.

ssh is how Unix systems communicate, really.

Any Linux file manager can connect to any other Linux system using sftp:// URLs too, assuming ssh-server is installed and running.  Full drag-n-drop.  

For more convenience and more security, setup ssh-keys.  That's just 3 easy commands for a Linux client.  
If WSL is loaded on Windows10, it is nearly as easy, but not quite because the 3rd command isn't on Windows. [https://serverfault.com/questions/224810/is-there-an-equivalent-to-ssh-copy-id-for-windows](https://serverfault.com/questions/224810/is-there-an-equivalent-to-ssh-copy-id-for-windows) explains that missing tool and shows "crazy powershell scripts" to do 1 part of what ssh-copy-id does.

Or if you just want to pull some files, you can run a HTTP server in 1 line of python for quick access. Run this from the directory where there are files you'd like to share:
```
$ python -m SimpleHTTPServer 8000
```
Most scripting languages have a way to run a simple HTTP server in 1-3 lines.  Handy for read-only sharing with trusted people.  

For larger files, over the internet, there's wormhole. It is a snap package.

---

### Post by Nosphky on 2020-10-07
Hey, thanks TheFu. That's given me a whole heap of stuff to think about - all new to me.

 So it'll probably take a little while to get at it. I'll start right away.

---

### Post by HermanAB on 2020-10-08
SSH is nowadays included with W10.

---

### Post by ActionParsnip on 2020-10-08
If they are on the same network, install openssh-server on the Ubuntu system and connect to SFTP using FileZilla and you can upload and download files as you need

---

### Post by ajgreeny on 2021-01-25
I realise this is now an old thread but if you are going to use simplehttpserver in 20.04 for occasional transfer of files the command will now have to be either ```
python2 -m SimpleHTTPServer 8000
``` or ```
python -m http.server 8000
```due to the changes in python versions used.

However, as TheFu says, use it only for short periods to move just a few files, as security is very much a missing part of this server.

For a default or long term connection use ssh, the most secure method most users will need.

---

### Post by Morbius1 on 2021-01-25
> **ajgreeny said:**
> I realise this is now an old thread but if you are going to use simplehttpserver in 20.04 for occasional transfer of files the command will now have to be ```
python2 -m SimpleHTTPServer 8000
``` due to the changes in python versions used.

It will not work with python or python3 for some reason even though I have python, python2 and python3 installed.
However, as TheFu says, use it only for short periods to move just a few files, as security is very much a missing part of this server.

For a default or long term connection use ssh, the most secure method most users will need.
Don't mean to go down a rat hole but .....

SimpleHTTPServer in python3 is called http.server:
```
python3 -m http.server
```

[ATTACH=CONFIG]287817[/ATTACH]

---

### Post by ajgreeny on 2021-01-25
> **Morbius1 said:**
> Don't mean to go down a rat hole but .....

SimpleHTTPServer in python3 is called http.server:
```
python3 -m http.server
```

[ATTACH=CONFIG]287817[/ATTACH]
Note that before you posted I had already edited my post above; you do not need to specify **python3**, just **python** does it.

I don't really use this any more but just came across the thread by accident today so tried it and found the old command does not work now, hence my post.

---

### Post by Morbius1 on 2021-01-25
> **ajgreeny said:**
> Note that before you posted I had already edited my post above; you do not need to specify **python3**, just **python** does it.

If we are still talking about Ubuntu 20.04 just using python will not work:
> tester@vub2004:~$ python -m http.server

Command 'python' not found, did you mean:

  command 'python3' from deb python3
  command 'python' from deb python-is-python3


Unless python-is-python3 is installed:
> In Ubuntu, all python packages use explicit python3 or python2
interpreter and do not use unversioned /usr/bin/python at all. Some
third-party code is now predominantly python3 based, yet may use
/usr/bin/python.

This is a convenience package which ships a symlink to point
the /usr/bin/python interpreter at the current default python3. It may
improve compatibility with other modern systems, whilst breaking some
obsolete or 3rd-party software.


---

### Post by ajgreeny on 2021-01-26
Interesting!

I see from my package installations in the dpkg logs that I do have **python-is-python2** installed, probably as a dependency of **virtualbox-6.1** installed from the VBox repos.  I was not actually aware of this, and I see there is a package called python-is-python3 as well, which in my case is not installed.

I now no longer use VBox so could if I wanted remove the python-is-python2 package, I assume, but as it is so tiny there seems little point in doing so.
If I try to add python-is-python3 package it removes the current python-is-python2 version so I shall leave things as they are.

---

