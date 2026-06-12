---
title: "mdadm monitor does not send email on boot"
date: 2015-02-17
forum: General Help
---

### Post by RayDeCampo on 2015-02-17
I have email set up and working from mdadm, tested by issuing the command:

```
sudo mdadm --monitor --scan --test --oneshot
```

I receive the email as expected.  Furthermore, I added --test to the /etc/default/mdadm file as below:

```
DAEMON_OPTIONS="--syslog --test"
```

Now if I restart the mdadm monitor service with the command below I also receive the email:

```
sudo service mdadm restart
```

So far so good.  However, when I reboot the system I do not receive an email from the mdadm monitor process.  Perhaps the process is starting before networking is available?  I'm not sure how to troubleshoot from here, I would appreciate any help.

Thanks,
Ray

---

