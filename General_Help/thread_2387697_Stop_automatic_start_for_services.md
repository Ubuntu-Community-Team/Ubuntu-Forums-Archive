---
title: "Stop automatic start for services"
date: 2018-03-22
forum: General Help
---

### Post by dam034 on 2018-03-22
Dear users,

I have a Raspberry Pi 3 with Raspbian, but I didn't find any differences on the CLI, so I post here the question.

There are ssh server and samba service on it, regarding ssh I can't start it, and when I want to see the status I get this:
[ATTACH=CONFIG]279048[/ATTACH]

I want to block the automatic start for ssh (after I solved it) and samba, and I want to start it manually from CLI only when I need, and to stop them also via CLI (with service sshd/smbd stop).

How can I do?

Thanks

---

### Post by again? on 2018-03-22
Using ssh service as example.
Check status.
```
systemctl status ssh.service
```
Disable autostart.
```
sudo systemctl disable ssh.service
```
Manual control.
```
sudo systemctl stop ssh.service
sudo systemctl start ssh.service
```

To re-enable autostart.
```
sudo systemctl enable ssh.service
```

The commands are run on services by default so you dont have to add the .service suffix.
i.e. you can just run **systemctl status ssh**

---

