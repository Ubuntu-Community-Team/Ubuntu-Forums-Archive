---
title: "Amazon AWS connection problems"
date: 2018-09-23
forum: General Help
---

### Post by Jinx13 on 2018-09-23
Hello, I seem to be having some random connection issues with my amazon AWS I upgraded 2 servers. A home server through SSH and my amazon server through SSH one after the other.

MY home server has no issues with connecting to the internet but it seems that my amazon does only recently.

I noticed this code in MOTD and started to investigate.

I can connect fine with SSH and seem to check "some" updates the list seems very short but nothing fails with apt

```
Failed to connect to https://changelogs.ubuntu.com/meta-release-lts. Check your Internet connection or proxy settings


Last login: Sun Sep 23 12:19:05 2018 from 212.159.70.59
ubuntu@ip-***-**-**-**:~$ ping https://changelogs.ubuntu.com/meta-release-lts
ping: https://changelogs.ubuntu.com/meta-release-lts: Name or service not known
ubuntu@ip-***-**-**-**:~$ ping ubuntu.com
PING ubuntu.com (91.189.94.40) 56(84) bytes of data.

--- ubuntu.com ping statistics ---
68 packets transmitted, 0 received, 100% packet loss, time 68613ms

ubuntu@ip-***-**-**-**:~$ ping google.com
PING google.com (216.58.195.78) 56(84) bytes of data.
^C
--- google.com ping statistics ---
14 packets transmitted, 0 received, 100% packet loss, time 13292ms

ubuntu@ip-***-**-**-**:~$ sudo apt update
Hit:1 http://us-west-2.ec2.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://us-west-2.ec2.archive.ubuntu.com/ubuntu bionic-updates InRelease
Hit:3 http://us-west-2.ec2.archive.ubuntu.com/ubuntu bionic-backports InRelease
Hit:4 http://security.ubuntu.com/ubuntu bionic-security InRelease              
Reading package lists... Done                      
Building dependency tree       
Reading state information... Done
All packages are up to date.
ubuntu@ip-***-**-**-**:~$
```

Can anyone help?

I have checked my mailserver on ssl-tools and connection is fine. I have been receiving emails but just discovered that I cannot send emails.

Kind regards,

~Jinx13

---

