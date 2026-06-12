---
title: "Server 16.04 - Hanging up on Shutdown"
date: 2017-08-27
forum: General Help
---

### Post by profdrhg on 2017-08-27
Hello,


when i try to shutdown my server with:
```
sudo shutdown now

```I get a "hang up" before it power off the mainboard (sometimes it works)


The last message is:


```
systemd-shutdown[1]: Failed to finalize  DM devices, ignoring

```
When the shutdown works i get the message "reboot: Power down" and the server shutdown but the most time it doesn't work and I get the error:
```

Info: task systemd-shutdown:1 blocked for more than 120 seconds
No tainted 4.4.0-92-generic #115-Ubuntu
Info: task kworker/0:1:31 blocked for more than 120 seconds
No tainted 4.4.0-92-generic #115-Ubuntu
```

---

