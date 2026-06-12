---
title: "AppArmor running amok (blocking docker and smbd)"
date: 2024-10-05
forum: General Help
---

### Post by mowieco on 2024-10-05
Hello everyone!

Suddenly several things stopped working von my Ubuntu 24.04.1 LTS system. First thing I noticed was that AppArmor denied me to restart or stop docker containers which i was allowed to do until now. 

```
kernel: audit: type=1400 audit(1728155313.822:270): apparmor="DENIED" operation="signal" class="signal" profile="docker-default" pid=1621 comm="dockerd" requested_mask="receive" denied_mask="receive" signal=kill peer="snap.docker.dockerd"
```



But even worse, apparmor also seems to mess with the samba server, blocking the network access to shared folders:


```
kernel: audit: type=1400 audit(1728158918.984:703): apparmor="DENIED" operation="open" class="file" profile="smbd" name="/media/noraid/public/" pid=6576 comm="smbd[192.168.0." requested_mask="r" denied_mask="r" fsuid=1001 ouid=0
```

I know that each if of the problems can be fixed somewhere in the apparmor profiles. But I would like to understand why all of the sudden this app blocks basic functions of the OS. Was this really intended and recently rolled out as an update or did I accidentally break something bigger in my system?

Any suggestions?

Regards

---

