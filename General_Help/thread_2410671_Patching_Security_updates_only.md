---
title: "Patching Security updates only"
date: 2019-01-18
forum: General Help
---

### Post by greavette on 2019-01-18
Hello Forum,

on Red Hat we issue the following command to only patch RHSA Security updates and any kernel upgrades.

yum install --security

What is the command to only update security updates (not all applications) on Ubuntu machines?  We are looking to patch the kernel and/or upgrade the kernel and we are looking to apply any security related patches only.  Any application upgrades/patching we are leaving to the application owners who installed the apps to ensure that app upgrades are properly tested/managed by the application owners.  Basically I guess you can say that we are trying to just look after the O/S and patch security/kernel for the O/S.

Hope what I'm asking for makes sense.  Thanks in advance for any advice you can provide me.

---

### Post by TheFu on 2019-01-18
[https://askubuntu.com/questions/194/how-can-i-install-just-security-updates-from-the-command-line](https://askubuntu.com/questions/194/how-can-i-install-just-security-updates-from-the-command-line)

From the server documentation: [https://help.ubuntu.com/18.04/serverguide/automatic-updates.html](https://help.ubuntu.com/18.04/serverguide/automatic-updates.html)

The short answer is to use the  **unattended-upgrade** package.  I stopped using it when it removed mariaDB and installed mysql a long time ago (2012 or so), bringing down our project management server.  This was before the meta-package dependencies knew how to support either DBMS.  It is probably better now.

I get up at 4-5am every Saturday morning, remote into my workstation and patch using a script.  Gives me piece of mind, plus I'm a morning person anyways.  It has been years since any update broke anything, so perhaps I'm overly cautious.

I think of patching like changing the oil in my vehicles. If I didn't do the oil change myself, I'd probably wouldn't notice other important issues.  I suppose reviewing logs daily (heavily filtered) is part of that process too.

---

### Post by greavette on 2019-01-19
Hello TheFu and thank you very much for taking the time to reply to my post.  Very much appreciate it!

I will look into the unattended-upgrade package.  Very surprising that it broke something for you a few years back!  I'll see if I can dig a bit deeper into what caveats I need to be aware of when using it.  We always have a good backup before we patch our servers but I'd rather not have to use it for a restore if I don't have too.

Would you mind sharing your script you use for patching?  Is it only for O/S or security updates.  I wouldn't mind seeing how you handle updates so I can perhaps create my own update plan for our Ubuntu servers.

Thanks again for your reply.

---

### Post by #&amp;thj^% on 2019-01-19
TheFu's very wise advice on  "unattended-upgrade" to be careful with it, is a solid clue, you may want to take a peek at the action to be taken with:
```
sudo unattended-upgrade --dry-run -d
```
This will only give you a preview of what will take place.
INFO: 

When you run "apt-get --dry-run" without "sudo", you'll get a warning:
```

  NOTE: This is only a simulation!
  apt-get needs root privileges for real execution.
  Keep also in mind that locking is deactivated,
  **_so don't depend on the relevance to the real current situation!_**
```

So it is better to use sudo to get a real testing.

---

