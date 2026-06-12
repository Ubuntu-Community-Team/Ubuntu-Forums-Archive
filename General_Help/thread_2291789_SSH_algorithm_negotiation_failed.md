---
title: "SSH algorithm negotiation failed"
date: 2015-08-22
forum: General Help
---

### Post by jremington on 2015-08-22
I recently installed 15.04 on a Dell desktop system (Xubuntu desktop). Everything is working perfectly, except that I can't log to the new system in via remote SSH, using SSH Secure Shell 3.2.9 on Windows 7. The attempt immediately fails with the message > Algorithm negotiation failed.
Key exchange with the remote host failed. This can happen if the host does not support the selected algorithms. No error messages appear in the host's syslog  or dmesg files.

Of the many systems I use, this is the first time I've encountered this problem. I **can** log in using command line ssh from other 'nix systems, or with Putty on Windows, but I would prefer to use Secure Shell 3.2.9, as it offers a convenient file transfer mechanism. I've made sure that all the cipher possibilities are activated in 3.2.9, but doubt that is the problem. I've tried from two completely different Win7 systems, with no success.

Here are the most basic system specs of the new host:

uname -a
Linux Dell960 3.19.0-26-generic #28-Ubuntu SMP Tue Aug 11 14:16:45 UTC 2015 i686 i686 i686 GNU/Linux

I've done quite a bit of Googling and have not found anything that  helped solve the problem.  Suggestions would be appreciated!

---

### Post by sandyd on 2015-08-22
It is possibly the same error as [https://bugzilla.redhat.com/show_bug.cgi?id=1228013](https://bugzilla.redhat.com/show_bug.cgi?id=1228013)

Your client can only use CBC modes, which are not supported due to security reasons.

Try WinSCP if you want to transfer files.

---

### Post by jremington on 2015-08-22
> Your client can only use CBC modes, which are not supported due to security reasons.Thanks, but I'm a bit confused. Did you mean the client "does not support" CBC modes, as those are listed among the ciphers supported by the Ubuntu 15.04 host?

sshd -T returns: ```

jim@Dell960:~$ sudo sshd -T | grep cipher
ciphers 3des-cbc,blowfish-cbc,cast128-cbc,arcfour,arcfour128,arcfour256,aes128-cbc,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com

```

The client lists blowfish, aes128, etc. without the -cbc suffix

Most of our systems run CentOS 6.7 and I can log in to those with the Secure Shell 3.2.9 client. Those systems support the following ciphers:
```
[root@www ~]# sshd -T | grep cipher
ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se

```

So evidently, the absence of a suffix in the cipher list provided by my client is not very informative.

---

### Post by HermanAB on 2015-08-22
SSH was upgraded recently and known insecure cyphers were removed, in order to actively discourage their use - after all, what is the point in using an insecure algorithm?  

To figure out what exactly is going on, try the very verbose ssh mode with the -vvv option.

It is possible to recompile ssh yourself and enable the insecure mode, but it would be far better to upgrade all the other machines instead, otherwise you are just fooling yourself by running insecure algos.

---

### Post by sandyd on 2015-08-22
> **jremington said:**
> Thanks, but I'm a bit confused. Did you mean the client "does not support" CBC modes, as those are listed among the ciphers supported by the Ubuntu 15.04 host?

sshd -T returns: ```

jim@Dell960:~$ sudo sshd -T | grep cipher
ciphers 3des-cbc,blowfish-cbc,cast128-cbc,arcfour,arcfour128,arcfour256,aes128-cbc,aes192-cbc,aes256-cbc,rijndael-cbc@lysator.liu.se,aes128-ctr,aes192-ctr,aes256-ctr,aes128-gcm@openssh.com,aes256-gcm@openssh.com,chacha20-poly1305@openssh.com

```

The client lists blowfish, aes128, etc. without the -cbc suffix

Most of our systems run CentOS 6.7 and I can log in to those with the Secure Shell 3.2.9 client. Those systems support the following ciphers:
```
[root@www ~]# sshd -T | grep cipher
ciphers aes128-ctr,aes192-ctr,aes256-ctr,arcfour256,arcfour128,aes128-cbc,3des-cbc,blowfish-cbc,cast128-cbc,aes192-cbc,aes256-cbc,arcfour,rijndael-cbc@lysator.liu.se

```

So evidently, the absence of a suffix in the cipher list provided by my client is not very informative.
The bug report noted on [comment #9]("https://bugzilla.redhat.com/show_bug.cgi?id=1228013#c9") that oddity even if it shows to be enabled (and is enabled forcefully in the config), the SSH binary prevents it from being used. Copying over the sshd binary from a machine that supported using cbc as a cipher fixed it, but is highly not recommended for security reasons.

---

