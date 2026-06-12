---
title: "ssh connection not working"
date: 2019-06-19
forum: General Help
---

### Post by rcrahul60 on 2019-06-19
i have 2 ubuntu machine and i am making a ssh connection for ansible so i generate ssh and trying ssh-copy-id username@ipofsecondmachine but its showing permission denied and i also tried changing sshd_config setting but it doesn't work

---

### Post by TheFu on 2019-06-20
More details please.
Explain what you've done like we are old and senile, please.
ssh troubleshooter: [https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)

Often, the problem can be found quickly by increasing verbosity.

```
$ ssh -vvv username@ipofsecondmachine
```

---

