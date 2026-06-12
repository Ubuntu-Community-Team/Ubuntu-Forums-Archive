---
title: "Docker on ubuntu server 18.04"
date: 2018-06-01
forum: General Help
---

### Post by BigYellowDog on 2018-06-01
I can not seem to get docker to start on my ubuntu server.  I installed docker.io, but it will not start

```
[user@ubuntu] ~ $ sudo systemctl status docker
&#9679; docker.service
   Loaded: masked (/dev/null; bad)
   Active: failed (Result: exit-code) since Fri 2018-06-01 14:15:19 EDT; 48min ago
 Main PID: 11607 (code=exited, status=1/FAILURE)

Jun 01 14:15:19 ubuntu systemd[1]: Failed to start Docker Application Container Engine.
Jun 01 14:15:19 ubuntu systemd[1]: docker.service: Service hold-off time over, scheduling restart.
Jun 01 14:15:19 ubuntu systemd[1]: docker.service: Scheduled restart job, restart counter is at 3.
Jun 01 14:15:19 ubuntu systemd[1]: Stopped Docker Application Container Engine.
Jun 01 14:15:19 ubuntu systemd[1]: docker.service: Start request repeated too quickly.
Jun 01 14:15:19 ubuntu systemd[1]: docker.service: Failed with result 'exit-code'.
Jun 01 14:15:19 ubuntu systemd[1]: Failed to start Docker Application Container Engine.

```

I have docker running perfectly on ubuntu desktop 18.04, not really sure what's different.  Any help would be appreciated

---

### Post by nlee2 on 2018-06-01
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"] 
[/TD]
[/TR]
[TR]
[/TR]
[/TABLE]
Have you tried

systemctl unmask docker.socket

systemctl unmask docker.service

systemctl start docker.service[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"] 
[/TD]
[/TR]
[TR]
[/TR]
[/TABLE]

---

### Post by BigYellowDog on 2018-06-02
I tried running /usr/bin/docker and I received a message about not being able to use my network configuration, or something like that.

I am running OpenVPN.  I stopped OpenVPN, and was able to start docker.  With docker running I was able to restart OPenVPN.  Both are running on the server.

Not really sure why OpenVPN would not allow docker to start.  

Thanks for the help.

---

