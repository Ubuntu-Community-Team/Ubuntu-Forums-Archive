---
title: "command mount"
date: 2014-05-17
forum: General Help
---

### Post by sv8bur-gmail on 2014-05-17
Hi 
I want to mount a directory which is in a different PC than that I have Ubuntu how can I give the mount command the IP of the oter PC is let's say 192.168.X.XXX
Thank you very much
Pericles

---

### Post by sudodus on 2014-05-17
You must run a server program in the other PC, for example an SSH server.

[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

---

### Post by sv8bur-gmail on 2014-05-17
Thank you very much but the other PC has Windows 7

---

### Post by sudodus on 2014-05-17
OK.

There are versions of SSH server for Windows too, but if you want to run Windows's server, you can connect to it from linux via ***Samba***.

Anyway you must enable the server in the computer with Windows, otherwise there is no way to connect to it. The server is not enabled by default, because it increases the risk of intrusion via the internet. (At least it used to be like this, I have not used Windows as a server for several years, so I might be wrong.)

---

### Post by sv8bur-gmail on 2014-05-17
ok thank you for your help I will see what I can do

---

### Post by sv8bur-gmail on 2014-05-17
If you still here I have change machine and I moved the files I am interesting to a machine with linux which have openssh-server intstalled can you tell me now how can I give the command mount I've tried many possible ways but I didn't managed to make it can you help me?
Thank you 
Pericles

---

### Post by sudodus on 2014-05-17
Do you want to log in remotely to the server? The crude way is to use the terminal window command ssh

Example: ```
ssh sv8bur@192.168.0.2
```

Do you want to 'see' and get or put files from or to the server? The crude way is to use the terminal window command sftp

Example: ```
sftp sv8bur@192.168.0.2
```

You can also 'mount', actually connect to the server via your file browser (it is similar but not exactly the same in Nautilus, Thunar and Pcmanfm). You can save the connecting procedure as a bookmark to make it convenient in the future.

In Windows you can use Filezilla or WinSCP for file transfer with a graphical interface to an SSH server.

---

### Post by Bashing-om on 2014-05-17
sv8bur-gmail; Hello,

In addition:
easiest way to copy files between two 'buntus that share the same router/house (Morbius1)
[http://ubuntuforums.org/showthread.php?t=2159449](http://ubuntuforums.org/showthread.php?t=2159449)

My little bit
[INDENT][INDENT]to try and help
[/INDENT][/INDENT]

---

### Post by sv8bur-gmail on 2014-05-17
I found the command which is sudo mount -t cifs //192.168.0.5 /media/cdrom it will be needed the cifs-utils
Thank you for all:P

---

