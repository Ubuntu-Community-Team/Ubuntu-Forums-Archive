---
title: "Install OpenSSH 7.6 on ubuntu 16.4"
date: 2017-12-12
forum: General Help
---

### Post by ajouve on 2017-12-12
I would like to update OpenSSH to version 7.6 but I can't find how to do that


I tried to do what was written in this gist [https://gist.github.com/techgaun/df66d37379df37838482c4c3470bc48e](https://gist.github.com/techgaun/df66d37379df37838482c4c3470bc48e) changing the following line wget "```
http://mirrors.evowise.com/pub/OpenBSD/OpenSSH/portable/openssh-7.6p1.tar.gz
````


So now when I am runing ```
ssh -V
``` I have ```
OpenSSH_7.6p1, OpenSSL 1.0.2g  1 Mar 2016
```


But ```
dpkg --list openssh\*
``` is returning me 


    ```
Desired=Unknown/Install/Remove/Purge/Hold
    | Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
    |/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
    ||/ Name                                                  Version                         Architecture                    Description
    +++-=====================================================-===============================-===============================-================================================================================================================
    ii  openssh-client                                        1:7.3p1-1                       amd64                           secure shell (SSH) client, for secure access to remote machines
    ii  openssh-server                                        1:7.3p1-1                       amd64                           secure shell (SSH) server, for secure access from remote machines
    ii  openssh-sftp-server                                   1:7.3p1-1                       amd64                           secure shell (SSH) sftp server module, for SFTP access from remote machines
```


I woud like to update this one as well but I have no idea how to do that

---

### Post by deadflowr on 2017-12-12
You installed 7.6 from source, so you will need to update it by installing again from source.
dpkg lists only packages installed from deb binaries, so nothing you ever make install from source will show there.
(You can however use a package called checkinstall in place of the make install command that will create a deb binary of the package, which will actually show in the dpkg listing.)
But even with installing a package using checkinstall you will still need to compile newer versions from source yourself to get them updated.
fwiw, checkinstall: [https://help.ubuntu.com/community/CheckInstall]("https://help.ubuntu.com/community/CheckInstall")

---

### Post by ajouve on 2017-12-13
Thanks for the answer deadflowr

the thing I am not understanding is that now I have the version 7.6 but when I am connection to the server I have the version 7.2

```
Remote protocol version 2.0, remote software version OpenSSH_7.2p2 Ubuntu-4ubuntu2.2
```

I have this output connection with verbose

How can I pass the openssh_server in 7.6 ?

---

### Post by deadflowr on 2017-12-13
The machine you're locally on (the client) would use 7.6.
Any other machine would have whatever version it has installed, and not whatever is installed on the machine you are locally at.
This
```
Remote protocol version 2.0, remote software version OpenSSH_7.2p2 Ubuntu-4ubuntu2.2
```
is the version the remote machine is using.

If you want to remote server to use the 7.6 version, then you need to install it there.

Hope that makes sense.

---

### Post by ajouve on 2017-12-13
Yes but I want to update the ssh version of the remote machine.

when I enter `ssh -V` on the remote machine, I have `OpenSSH_7.6p1, OpenSSL 1.0.2g  1 Mar 2016` but when I am connecting to the remote machine I have `debug1: Remote protocol version 2.0, remote software version OpenSSH_7.2p2 Ubuntu-4ubuntu2.2` and I would like to have `OpenSSH_7.6p1` instead.

Thanks

---

### Post by deadflowr on 2017-12-13
Have you restarted the ssh service on the remote machine?

---

### Post by ajouve on 2017-12-13
Yes I restarted the server

But I am on EC2 is there any possibility that Amazone is using kind of middleware in the connection ?

---

### Post by deadflowr on 2017-12-13
> But I am on EC2 is there any possibility that Amazone is using kind of middleware in the connection ?
I have no idea. sorry

---

### Post by Holger_Gehrke on 2017-12-13
Uhm, aren't client (ssh) and server (ssh**d**) two separate pieces of software ? And wouldn't a new server need some changes to the system configuration, probably in a .service file for systemd ?

Holger

---

### Post by ajouve on 2017-12-14
sshd -V is returning me OpenSSH_7.6p1, OpenSSL 1.0.2g  1 Mar 2016 as well, what should I change in the [COLOR=#000000] .service ?

I really do not understand why during the connection I have [/COLOR][COLOR=#000000][FONT=&quot]Remote protocol version 2.0, remote software version OpenSSH_7.2p2 Ubuntu-4ubuntu2.2[/FONT][/COLOR]

---

