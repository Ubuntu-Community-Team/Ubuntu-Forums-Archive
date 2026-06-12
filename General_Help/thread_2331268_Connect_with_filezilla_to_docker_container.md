---
title: "Connect with filezilla to docker container"
date: 2016-07-20
forum: General Help
---

### Post by cromat2 on 2016-07-20
I am running docker containers on Google Cloud virtual machine. I am trying for hours to connect from filezilla on my local computer to an running docker container. I have started docker image like this:
```
docker run -t -d --name test -p 2222:22 --link postgres7:postgres7 random_image /bin/bash
```

In my filezilla connection configuration I have set:

```
Host: Google Cloud IP address
Port: 2222
Protocol: SFTP
Logon Type: Normal
User: root (without password)
```

When trying to connect I get this error:
```
Status: Connecting to 130.211.63.182:2222...
Response:   fzSftp started
Command:    open "root@130.211.63.182" 2222
Error:  Connection refused
Error:  Could not connect to server
```
I have opened ports on google cloud engine and I am using Ubuntu 14.04 LTS locally and on google Cloud host.

---

