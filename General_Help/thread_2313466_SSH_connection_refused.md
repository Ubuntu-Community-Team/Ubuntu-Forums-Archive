---
title: "SSH connection refused"
date: 2016-02-12
forum: General Help
---

### Post by Turrrbulence on 2016-02-12
After changing the ssh config file to a root no login and a different port, the terminal returns a connection error for port 22 connections and an operation timed out on the port 1234 (which I had set the config file to).

---

### Post by nerdtron on 2016-02-13
What exact options did you changed on the /etc/ssh/sshd_config file? Did you restarted the sshd service and is your firewall activated?

---

### Post by Turrrbulence on 2016-02-13
On /etc/ssh/sshd_config, these two lines were added:
Permitrootlogin no
Port 1234
The server is a 14.04 ubuntu and when ssh has been restarted, the connection was refused.

---

### Post by SeijiSensei on 2016-02-13
Is the machine running a firewall? If so, did you open port 1234.

On the machine itself, try connecting like this:
```
ssh -p 1234 ip.addr.of.host
```
so if your machine has IP address, 10.10.10.10, use that for "ip.addr.of.host".  Can you connect?

---

### Post by Turrrbulence on 2016-02-14
If the port is on default (22), the connection is refused but if port 1234 is set, the operation is timed out. 
I can't access the server so the sshd configuration cannot be modified.

---

### Post by nerdtron on 2016-02-15
> **Turrrbulence said:**
> If the port is on default (22), the connection is refused but if port 1234 is set, the operation is timed out. 
I can't access the server so the sshd configuration cannot be modified.

Try to use verbose mode of ssh to see the error messages:
```
ssh -v -p 1234 ip.addr.of.host 
```

And from your error, Connection refused is different from Connection Timeout. 
Connection refused means your SSH connection reached the server, but since the port is now different, the server will refuse your connection to port 22.
Connection timeout can mean a few things, like your SSH connection did not reached the server (could be a network connectivity problem). But since your previous ssh is working, I think it's more likely that a **firewall **is blocking port 1234. If your server does not have firewall/iptables configured you may need to consult with your network admin and consult if there are any rules blocking port 1234.

---

### Post by SeijiSensei on 2016-02-15
> **nerdtron said:**
> Try to use verbose mode of ssh to see the error messages:
```
ssh -p 1234 ip.addr.of.host 
```

I think you meant
```
ssh -v -p 1234 ip.addr.of host
```

---

### Post by Turrrbulence on 2016-02-21
OpenSSH_6.9p1 Ubuntu-2ubuntu0.1, OpenSSL 1.0.2d 9 Jul 2015
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for xx.xx.xx.xx.xx
debug1: Connecting to xx.xx.xx.xx.xx [xx.xx.xx.xx.xx] port 22.
debug1: connect to address xx.xx.xx.xx.xx port 22: Connection timed out
ssh: connect to host xx.xx.xx.xx.xx port 22: Connection timed out

This is on AWS and after attaching the volume to a new server instance, the ssh returned a connection timeout. The issue comes from the configuration files that I had edited on the server to point to a different port. Do you know of a way to access the server without ssh on port 22 ?

---

### Post by nerdtron on 2016-02-22
> **Turrrbulence said:**
> OpenSSH_6.9p1 Ubuntu-2ubuntu0.1, OpenSSL 1.0.2d 9 Jul 2015
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for xx.xx.xx.xx.xx
debug1: Connecting to xx.xx.xx.xx.xx [xx.xx.xx.xx.xx] port 22.
debug1: connect to address xx.xx.xx.xx.xx port 22: Connection timed out
ssh: connect to host xx.xx.xx.xx.xx port 22: Connection timed out

This is on AWS and after attaching the volume to a new server instance, the ssh returned a connection timeout. The issue comes from the configuration files that I had edited on the server to point to a different port. Do you know of a way to access the server without ssh on port 22 ?


The output of the above commands shows you are still trying to connect to port 22? You should use port 1234 since you said you changed it already. Connect like this:
```
 ssh -vp 1234 IP.Address.here 
```


Also, if you changed the SSH port of the server other than port 22, you should also changed the security group firewall setting on the AWS instance to allow incoming connections to port 1234.

---

