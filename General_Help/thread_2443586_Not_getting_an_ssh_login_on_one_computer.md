---
title: "Not getting an ssh login on one computer"
date: 2020-05-17
forum: General Help
---

### Post by rsteinmetz70112 on 2020-05-17
I have a couple of Ubuntu 18.04 computers at home. Since using them more for work recently I decided to set up ssh on the so I could do remover administration.
I installed openssh-server on both one works fine, the other initially worked but now doesn't prompt for a password when I try to access it and eventually times out. I can't find anything in the logs to give me a clue as to why.
I've never had this problem before openssh-server has simply just worked.
I've compared the configuration files and as afar as I can tell they are the defaults loaded when I installed the server.
The one significant difference between the tow is that one is on the WiFi network and the other is one a wired network.

OK I found this in syslog:
```
syslog:May 17 15:49:55 apartment systemd[1290]: Closed GnuPG cryptographic agent (ssh-agent emulation).
syslog:May 17 15:49:55 <machinename> systemd[1464]: Listening on GnuPG cryptographic agent (ssh-agent emulation).
syslog:May 17 15:49:57 <machinename> gnome-keyring-ssh.desktop[1547]: SSH_AUTH_SOCK=/run/user/1001/keyring/ssh
```

user 1001 is a different user than the user I'm attempting to login in as

A successful login to the other machine only lists the following:

```
May 17 11:09:53 <machinename> systemd[1514]: Closed GnuPG cryptographic agent (ssh-agent emulation).
May 17 11:09:54 <machinename>  systemd[1708]: Listening on GnuPG cryptographic agent (ssh-agent emulation).
```

---

### Post by TheFu on 2020-05-17
All systems have static ips?

Setting up ssh w/ keys is pretty easy.  Think 3 commands.  I&#8217;ve posted them here a few times. Look for ssh-keygen, ssh-copy-id and some ~/.ssh/config setup.  [https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386](https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386)

---

### Post by HermanAB on 2020-05-18
You can debug ssh with: 
$ ssh -vvv user@server

---

### Post by rsteinmetz70112 on 2020-05-18
> **HermanAB said:**
> You can debug ssh with: 
$ ssh -vvv user@server

```
$ ssh -vvv me@machinename
OpenSSH_7.6p1 Ubuntu-4ubuntu0.3, OpenSSL 1.0.2n  7 Dec 2017
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolving "machinename" port 22
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to machinename [192.168.2.51] port 22.
ssh: connect to host apartment port 22: Connection timed out
```

That doesn't seem to tell me anything I didn't already know - the connection to the remote machine nae is timing out.

---

### Post by rsteinmetz70112 on 2020-05-18
> **TheFu said:**
> All systems have static ips?
The remote machine is DHCP, but it never changes.

> Setting up ssh w/ keys is pretty easy.  Think 3 commands.  I’ve posted them here a few times. Look for ssh-keygen, ssh-copy-id and some ~/.ssh/config setup.  [https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386](https://ubuntuforums.org/showthread.php?t=2433034&p=13916386#post13916386)

I'm not sure the problem is with ssh.

---

### Post by TheFu on 2020-05-18
> **rsteinmetz70112 said:**
> ```
$ ssh -vvv me@machinename
OpenSSH_7.6p1 Ubuntu-4ubuntu0.3, OpenSSL 1.0.2n  7 Dec 2017
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: resolving "machinename" port 22
debug2: ssh_connect_direct: needpriv 0
debug1: Connecting to machinename [192.168.2.51] port 22.
ssh: connect to host apartment port 22: Connection timed out
```

That doesn't seem to tell me anything I didn't already know - the connection to the remote machine nae is timing out.

It tells me that there isn't an sshd listing on the IP address that the client is pointing at.  Hence, the question about static IPs.

Can you $ ping machinename?
Is sshd running on the other machine?
Is there a firewall blocking inbound connections on the other machine?
Those are pretty much the problems for this symptom.

---

### Post by rsteinmetz70112 on 2020-05-18
> **TheFu said:**
> It tells me that there isn't an sshd listing on the IP address that the client is pointing at.  Hence, the question about static IPs.

Can you $ ping machinename?
Yes  by name or IP address
> Is sshd running on the other machine?
Yes
> Is there a firewall blocking inbound connections on the other machine?
No
> Those are pretty much the problems for this symptom.
Which is why I can't figure out why it's not working. ;)

---

### Post by TheFu on 2020-05-18
Good info.  Something should show up in the logs and with -vvvv.  Time to break out the packet sniffer on the client. Perhaps ipv6 has taken over 1 machine?  Had to add a new setting to an sshd_config to disable ipv6 on a few of my boxes last year.   But connection attempts were showing up in my logs.  The setting ....
```
AddressFamily inet
```

I’m assuming all the rest of the settings are default.

---

### Post by rsteinmetz70112 on 2020-05-18
> **TheFu said:**
> Good info.  Something should show up in the logs and with -vvvv.  Time to break out the packet sniffer on the client. Perhaps ipv6 has taken over 1 machine?  Had to add a new setting to an sshd_config to disable ipv6 on a few of my boxes last year.   But connection attempts were showing up in my logs.  The setting ....
```
AddressFamily inet
```

I&#8217;m assuming all the rest of the settings are default.

All settings are the defaults. In fact I've never needed anything else in the past to get it to work on Ubuntu.
I guess I'll go back through the logs and see if I can find anything.
Unfortunately I think the -vvv will only affect the initiating machine(client) and nothing much seems to be happening of the receiving machine(server). 
I think as you said above the ssh command is not making contact with sshd on the server.
ifconfig reports the correct ipv4 address so I don't think ipv6 has taken over although is also has ipv6 addresses.

---

### Post by btindie on 2020-05-19
If you've still got an issue you could try running _sshd_ in debug mode on the server
```
sudo /usr/sbin/sshd -ddd -p 2022
```
which will make it listen on port 2022 and make it show any connection attempts.
Then from your client try with
```
ssh -p 2022 -vvv me@machinename
```

If that doesn't work then it may be your home router/wifi. I think with some you can restrict inbound connections to wifi connected devices.

It's pretty easy to test network connectivity between systems using netcat / socat
server:
```
nc -l -p 2022
```
client:
```
nc remotehost 2022
```
You can then send messages between the two systems by typing and pressing enter.

If that works, the network / wifi is fine and it's something going on on that host with ssh / port 22.

You can check for firewall rules using
```
sudo iptables-save
```

---

### Post by HermanAB on 2020-05-19
Test SSH on the destination machine itself.  If it doesn't work there, then it won't work remotely either.

You can check address resolver issues with 'nslookup', 'dig' and 'traceroute' and you can also check network issues with 'telnet servername 22'.  Telnet doesn't support the SSH protocol, but you should get the server banner.  

Trying different tools to reach the server will give you different error messages, which will help you figure out where the problem is.

---

### Post by bobnn on 2020-05-19
> **btindie said:**
> If that doesn't work then it may be your home router/wifi. I think with some you can restrict inbound connections to wifi connected devices.

Some WiFi routers will go into that mode by themselves without configuration - I've seen it happen on wifi routers that didn't even document the feature.

Try powering the router off, then on again.

---

### Post by rsteinmetz70112 on 2020-05-20
Thanks for the suggestions. I'm going to be traveling for a week or so so I won't be able to check until I get back.

---

### Post by ActionParsnip on 2020-05-20
Do you use SSH keys to connect in?

---

### Post by rsteinmetz70112 on 2020-05-22
> **ActionParsnip said:**
> Do you use SSH keys to connect in?

no

---

