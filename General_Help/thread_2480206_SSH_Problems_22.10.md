---
title: "SSH Problems 22.10"
date: 2022-10-22
forum: General Help
---

### Post by gummipunkt on 2022-10-22
Hi,
upgraded yesterday from 22.04 to 22.10. Now I can't connect to two of my three servers:

gummipunkt@gummibook:~$ ssh [email]user@domain.eu[/email] -p 65022
This service allows sftp connections only.
Connection to domain.eu closed.

I thought I'd misconfigured my servers, but this wasn't possible because I haven't touched anything the last days. Then I booted Windows and there it works. After that I tried Termux and there it worked too. Worked with 22.04 as expected. Just an problem with 22.10.

Has anyone a glue what could be happened during the update?

Best,
gummipunkt

---

### Post by philhughes on 2022-10-22
There has been a change in 22.10 to the way sshd is configured, which in particular affects non-standard port configurations. This should be migrated automatically, but possibly your difficulties are related to this. The following discussion may help:

[https://discourse.ubuntu.com/t/sshd-now-uses-socket-based-activation-ubuntu-22-10-and-later/30189](https://discourse.ubuntu.com/t/sshd-now-uses-socket-based-activation-ubuntu-22-10-and-later/30189)

---

### Post by gummipunkt on 2022-10-22
Hi,

Unfortunately not. As far as I can see, it's a change for the listening port but I want to connect. Have now connected via VNC, changed the SSH port but still don't work.

---

### Post by MAFoElffen on 2022-10-22
Maybe... as from the way I read that, sshd's default behavior is installed but not enabled.
```

sudo systemctl status sshd  | grep 'Loaded: '
sudo lsof -i:22

```
The 1st command would check to see if sshd is enabled and loaded.

The second command would check both sides of port 22, to see if it is listening and if any connections are made...

---

### Post by gummipunkt on 2022-10-23
```
gummipunkt@gummibook:~$ sudo systemctl status sshd  | grep 'Loaded: '
Unit sshd.service could not be found.


gummipunkt@gummibook:~$ sudo systemctl start sshd
Failed to start sshd.service: Unit sshd.service not found.


gummipunkt@gummibook:~$ sudo systemctl start ssh
gummipunkt@gummibook:~$ sudo systemctl status sshd  | grep 'Loaded: '
Unit sshd.service could not be found.


gummipunkt@gummibook:~$ sudo systemctl status ssh  | grep 'Loaded: '
     Loaded: loaded (/lib/systemd/system/ssh.service; disabled; preset: enabled)


gummipunkt@gummibook:~$ sudo lsof -i:22
COMMAND   PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
systemd     1 root   58u  IPv6  28332      0t0  TCP *:ssh (LISTEN)
sshd    60848 root    3u  IPv6  28332      0t0  TCP *:ssh (LISTEN)

```

still no changes. :-/

---

### Post by philhughes on 2022-10-23
Any commands you need to run on your server, not the PC you are trying to connect from (ie on domain.eu).

Seeing as you are able to connect by VNC, run this on the server to see what port sshd is listening on (this is on 22.04, I assume it is the same on 22.10):

```
$  journalctl --boot 0 | grep sshd
Oct 23 09:13:06 hostname sshd[1447]: Server listening on 0.0.0.0 port 2222.
Oct 23 09:13:06 hostname sshd[1447]: Server listening on :: port 2222.
```

How did you change the ssh port? If you have been migrated to the new configuration, you cannot change it in sshd_config. You have to create a systemd override file as suggested in the last post in the discourse thread. So I would try something like the following if you want to listen on port 65022 as in your original post.

```
mkdir -p /etc/systemd/system/ssh.socket.d
cat >/etc/systemd/system/ssh.socket.d/listen.conf <<EOF
[Socket]
ListenStream=
ListenStream=65022
EOF
```

If this doesn't work, just delete the file /etc/systemd/system/ssh.socket.d/listen.conf and you will be back to where you started.

There is another person in the discourse post saying they couldn't connect, so it seems you are not alone and hopefully there will be more in the thread next week.

---

### Post by MAFoElffen on 2022-10-23
LOL. I see that problem now.

Try this instead

On 21.10 server
```

sudo systemctl enable ssh
sudo systemctl status ssh

```
The serveice for 21.10 is now called ssh.service instead of sshd.service...

From client to server, try:
```

ssh -F none -p 22 user@domain.eu

```
I'll explain after it connects...

---

### Post by MAFoElffen on 2022-10-23
I spun up a 22.10 server on my KVM main server and tested... Yes, sshd.service from 22.04 is now called ssh.service and uses sshd.socket in 21.10 and does works differently under the covers. 

To adjust: Enable ssh.service... as the default is disabled.

See screen shot, which is ssh'ed from a VM on my laptop >> to my server, then again ssh'ed from my server into a VM guest there (the virt 22.10 server guest).

---

### Post by philhughes on 2022-10-24
In 22.04, the systemd service is actually ssh.service. sshd.service is an alias for ssh.service, which you can see by looking at the service file. There is also a symlink in etc/systemd/system. ssh.service is enabled by default.

ssh.socket is also present, but is disabled by default. On a 22.04 system (some lines removed for brevity):

```
$ systemctl status ssh.service
&#9679; ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
     Active: active (running) since Mon 2022-10-24 09:33:01 BST; 8min ago
...

$ systemctl status ssh.socket
&#9675; ssh.socket - OpenBSD Secure Shell server socket
     Loaded: loaded (/lib/systemd/system/ssh.socket; disabled; vendor preset: enabled)
     Active: inactive (dead)
...
```

The point of the change (from the Discourse post) is that sshd will not be started until an incoming connection request is received. This has been done to reduce the memory consumed by Ubuntu Server instances by default.

Thus by enabling ssh.service, you are going back to the old way of doing things. This may be what you want if you are having problems and just want sshd to work and don't care about the small amount of memory used. (You may also want to disable ssh.socket.)

I have migrated a system running 22.04 with sshd on a non-standard port (and with the port specified in an Include file) to 22.10, and the migration to socket based activation just worked. I did not have to do anything extra.

Before anyone ssh's in, on 22.10 you see the following:

```
$ systemctl status ssh.service
&#9675; ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/lib/systemd/system/ssh.service; disabled; preset: enabled)
    Drop-In: /etc/systemd/system/ssh.service.d
             &#9492;&#9472;00-socket.conf
     Active: inactive (dead)
TriggeredBy: &#9679; ssh.socket

$ systemctl status ssh.socket
&#9679; ssh.socket - OpenBSD Secure Shell server socket
     Loaded: loaded (/lib/systemd/system/ssh.socket; enabled; preset: enabled)
    Drop-In: /etc/systemd/system/ssh.socket.d
             &#9492;&#9472;addresses.conf
     Active: active (listening) since Mon 2022-10-24 12:02:37 BST; 5min ago
      Until: Mon 2022-10-24 12:02:37 BST; 5min ago
   Triggers: &#9679; ssh.service
     Listen: [::]:2222 (Stream)

$ journalctl --boot 0 | grep sshd
$
```

After someone ssh's in:

```
$ systemctl status ssh.service
&#9679; ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/lib/systemd/system/ssh.service; disabled; preset: enabled)
    Drop-In: /etc/systemd/system/ssh.service.d
             &#9492;&#9472;00-socket.conf
     Active: active (running) since Mon 2022-10-24 12:20:35 BST; 4s ago
TriggeredBy: &#9679; ssh.socket

Oct 24 12:20:35 hostname sshd[2841]: Server listening on :: port 2222.
Oct 24 12:20:35 hostname systemd[1]: Started OpenBSD Secure Shell server.
Oct 24 12:20:35 hostname sshd[2842]: Connection from 192.168.1.51 port 54050 on 192.168.1.52 port 2222 rdomain ""

$ systemctl status ssh.socket
&#9679; ssh.socket - OpenBSD Secure Shell server socket
     Loaded: loaded (/lib/systemd/system/ssh.socket; enabled; preset: enabled)
    Drop-In: /etc/systemd/system/ssh.socket.d
             &#9492;&#9472;addresses.conf
     Active: active (running) since Mon 2022-10-24 12:02:37 BST; 18min ago
      Until: Mon 2022-10-24 12:02:37 BST; 18min ago
   Triggers: &#9679; ssh.service
     Listen: [::]:2222 (Stream)

$ journalctl --boot 0 | grep sshd
Oct 24 12:20:35 hostname sshd[2841]: Server listening on :: port 2222.
Oct 24 12:20:35 hostname sshd[2842]: Connection from 192.168.1.51 port 54050 on 192.168.1.52 port 2222 rdomain ""
```

Two files have been created in /etc/systemd/system:

```
$ cat /etc/systemd/system/ssh.service.d/00-socket.conf
[Unit]
After=ssh.socket
Requires=ssh.socket

$ cat /etc/systemd/system/ssh.socket.d/addresses.conf
[Socket]
ListenStream=
ListenStream=2222
```

Sorry for the long post, but I hope this helps for those people who are having problems. Keep a watch on the Discourse thread.

---

