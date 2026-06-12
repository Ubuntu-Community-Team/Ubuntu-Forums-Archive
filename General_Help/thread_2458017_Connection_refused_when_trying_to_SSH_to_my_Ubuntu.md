---
title: "Connection refused when trying to SSH to my Ubuntu 20.04 from other network"
date: 2021-02-14
forum: General Help
---

### Post by forumate on 2021-02-14
Hello,

Following my other topic on how to make my own "cloud" backup, I decided to use FileZilla via SSH.

I installed Ubuntu 20.4.2.0 LTS on VMware Workstation. Then I installed OpenSSH server and created a private and public key. I copied the public key to my Windows host for testing. I allowed port 22 using "***sudo ufw allow ssh".*** I see SSH server is active and running. But when I try to SSH from outside I get "Connection refused". I tried with FileZilla, PuTTY and also Windows built-in SSH command. All of them refused. Could it be that my ISP just won't allow it? Or the router I have? Or it has nothing to do with these two?

thanks

---

### Post by CelticWarrior on 2021-02-14
If you didn't set the port forwarding rule in your router then that's the reason.

---

### Post by forumate on 2021-02-15
> **CelticWarrior said:**
> If you didn't set the port forwarding rule in your router then that's the reason.

I just contacted my ISP and they opened a rule. Still refused. I may be doing something wrong with the keys. Is there a way to test it by removing key-pair and SSH without anything? Just the password and username?

---

### Post by tc2020 on 2021-02-15
My setup may not be the same as yours but I have a device running Ubuntu 20.04 server LTS. It has SSH enabled and sits behind a broadband router. All I had to do was to set its port forwarding  as suggested in previous post. Nothing to do with ISP nor private/public keys. People from different countries can PuTTY SSH to it. Maybe just log on your router and double check your settings?. Also, my router uses IP dynamically assigned by ISP (but hardly changed even after reboots) so I have to check it from time to time and let people know the IP if it's changed so they can access the device.

---

### Post by The Cog on 2021-02-15
"Conection refused" is different to getting the username/password wrong. Connection refused happens when the TCP connection is actively refused by the OS (or possibly by networking kit somewhere in the path between you and the intended destination). 
If you get the username/password wrong then the connection is first accepted, and then closed once the server decides you are not authorised (e.g. wrong password or key).

You can test with netcat. e.g. connecting to my own PC - the server reports its ssh version - this proves the network connection succeeds:
```
$ netcat -v 127.0.0.1 22
Connection to 127.0.0.1 22 port [tcp/ssh] succeeded!
SSH-2.0-OpenSSH_8.2p1 Ubuntu-4ubuntu0.1
```

---

### Post by Doug S on 2021-02-15
+1 to all the above advice.

now,
> **forumate said:**
> I installed Ubuntu 20.4.2.0 LTS on VMware Workstation.
please describe in more detail. what computer and OS is the host? Is the client on a bridged network, and therefore on the same sub-net as the host? If not, then no you can not reach the client directly from anywhere else. You would have to either change it to bridged or implement another layer of port forwarding between the host and the client. Anyway please clarify. If you are unfamiliar with terms like "bridged", then just tell us the IP addresses, including sub-net mask for each of the host and the client, because we can tell from that information.

---

### Post by HermanAB on 2021-02-16
The important point to remember is that wfor a network service to work, the underlying packet routing must work - so test that first.

The example above uses the 'netcat' command.  I'm not sure whether that is correct - try the short form 'nc':

$ nc -v 127.0.0.1 22
Connection to 127.0.0.1 port 22 [tcp/ssh] succeeded!
SSH-2.0-OpenSSH_8.1

If you do not get a response from the ssh daemon, then you have a routing problem and have to fix that first, before trying the ssh client again.

---

### Post by Doug S on 2021-02-16
> **HermanAB said:**
> The example above uses the 'netcat' command.  I'm not sure whether that is correct - try the short form 'nc':???

they are the exact same thing:

```
doug@s18:~$ ls -l /usr/bin/nc
lrwxrwxrwx 1 root root 20 Jan 23  2020 /usr/bin/nc -> /etc/alternatives/nc
doug@s18:~$ ls -l /etc/alternatives/nc
lrwxrwxrwx 1 root root 15 Jan 23  2020 /etc/alternatives/nc -> /bin/nc.openbsd
doug@s18:~$ ls -l /usr/bin/netcat
lrwxrwxrwx 1 root root 24 Jan 23  2020 /usr/bin/netcat -> /etc/alternatives/netcat
doug@s18:~$ ls -l /etc/alternatives/netcat
lrwxrwxrwx 1 root root 15 Jan 23  2020 /etc/alternatives/netcat -> /bin/nc.openbsd

```

---

### Post by TheFu on 2021-02-16
```
ssh -vvv userid@host
```

BTW, it is handy never to have port 22 open to the internet unless you want 10,000 attacks daily.
[https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections) has more ssh troubleshooting steps. It also has links to securing ssh and some surprising ways that ssh can be used that Windows people don't know.

For unix-to-unix backups, sftp is a poor choice for backups.  Use a real backup too that works over ssh. Most do.  If you are running the backup server, it is probably best to "pull" the backups, not "push" them, so any malware on a client doesn't get a chance to destroy backup files.

---

