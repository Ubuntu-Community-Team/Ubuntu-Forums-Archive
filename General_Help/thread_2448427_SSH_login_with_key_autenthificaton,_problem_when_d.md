---
title: "SSH login with key autenthificaton, problem when disabling password auth"
date: 2020-08-07
forum: General Help
---

### Post by daniflor on 2020-08-07
Hi everyone, hope you are having a nice day!

I have been working around key authentication ssh login from Windows CMD into one virtual server (Ubuntu 20.x) I have set up in my computer.

I generated and installed the keys, everything works fine. I can login with ssh -i C:\Users\user\key user@ip successfully.

Now I am trying to disable password login trough sshd_config. 

> When I set PasswordAuthentications = no and after run sudo service ssh restart I receive:

Job for ssh.service failed because the control process exited with error code.


> systemctl status ssh.service
ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
     Active: failed (Result: exit-code) since Fri 2020-08-07 15:36:52 PDT; 4s ago
       Docs: man:sshd(8)
             man:sshd_config(5)
    Process: 3201 ExecStartPre=/usr/sbin/sshd -t (code=exited, status=255/EXCEPTION)

> sudo sshd -t 
/etc/ssh/sshd_config: line 58: Bad configuration option: PasswordAuthentications

I am a new user in Linux, have been reading and trying everything I could find on the internet with no luck.. Any ideas?
It is just that line on sshd_config, if I revert that change, ssh works again. So probably there is some other setting I am missing in order to get succes..

Thank you in advance!

I am working on my English as well, I am sorry if there are some spelling mistakes...

---

### Post by TheFu on 2020-08-08
Incorrect:
```
PasswordAuthentications **[COLOR="#FF0000"]=[/COLOR]** no
```
Correct:
```
PasswordAuthentications no
```

---

### Post by daniflor on 2020-08-08
Hi TheFu, thanks for your answer. 

Actually I wrote it wrong in here, but my sshd_config file has no '='.

So, the problem remains.. if you have any other ideas for troubleshooting I will really aprecciate it.

---

### Post by deadflowr on 2020-08-08
Is it really PasswordAuthentications?
Shouldn't it be PasswordAuthentication, without an s?

---

### Post by TheFu on 2020-08-08
> **deadflowr said:**
> Is it really PasswordAuthentications?
Shouldn't it be PasswordAuthentication, without an s?

Good catch!
From my own sshd_config:

```
PasswordAuthentication no
Match Address 172.22.22.0/24,172.21.22.0/24,172.22.21.0/24
      PasswordAuthentication yes
```

This allows passwords from selected LAN subnets, but not anywhere else. Those lines are at the end of the file. The "Match Address" part allows all commands after that to be specific to connections from those subnets.

---

### Post by daniflor on 2020-08-08
> **deadflowr said:**
> Is it really PasswordAuthentications?
Shouldn't it be PasswordAuthentication, without an s?

That´s right ! Thank you! 

It seems I messed up that at some point without realizing.

Are there some ways to reset to default parameters config file? Besides having a back-up

---

### Post by TheFu on 2020-08-08
> **daniflor said:**
> That´s right ! Thank you! 

It seems I messed up that at some point without realizing.

Are there some ways to reset to default parameters config file? Besides having a back-up

Always have a backup.

---

### Post by deadflowr on 2020-08-08
The system should have a clean config file in /usr/share/openssh.
Should have an untouched sshd_config file there.

---

### Post by daniflor on 2020-08-08
Yes, there is! Thank you again!

---

