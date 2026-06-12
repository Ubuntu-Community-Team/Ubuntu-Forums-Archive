---
title: "SSH port dissapeared in netstat"
date: 2007-08-23
forum: General Help
---

### Post by caitseith on 2007-08-23
I configured my SSH to run over port 4321. It worked fine for a while. But today I found out that the computer refused to accept connections. I returned the port to 22, but still it doesn't work. I checked the comand:
netstat -na --inet
It doesn't display either port anymore.
Any ideas?

---

### Post by jamvegan on 2007-08-24
Have you confirmed that the ssh daemon is running?
```
ps -e | grep sshd
```
If that produces no output, try:
```
sudo /etc/init.d/ssh start
```

---

