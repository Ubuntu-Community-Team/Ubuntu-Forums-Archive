---
title: "Crontab on Boot Up"
date: 2007-10-09
forum: General Help
---

### Post by tomthecabinboy on 2007-10-09
I have been told that you can configure Crontab to run on boot up.
I have googled and googled and googled, and not found anything.

Does anyone know how to configure cron to run a script when you start up.

I am running Ubuntu 7.04 for info

Thanks

Tom

---

### Post by 5-HT on 2007-10-09
/etc/rc.local is parsed for run on bootup and you can dump a link to the script there. Easiest to just keep cron for scheduling tasks.
cheers,

---

### Post by tomthecabinboy on 2007-10-09
Hi 5HT

Thanks for your reply. I am pretty new to Linux BUT I am making good progress.
I have found the file you referred to and it looks pretty straight forward.

BUT Thinking it through in my head. I am assuming that if this is done through bootup the permissions will be root.

Basically my script is an rsync script that backs up my photographs and my emails to a mirrored drive on my server. When I am logged on the script works like a dream but like I said I am assuming that on boot up the script will be run under root.

Ami I right? do I need to do anything to ensure the script still runs??

Tom

---

### Post by 5-HT on 2007-10-09
> **tomthecabinboy said:**
> 

Thinking it through in my head. I am assuming that if this is done through bootup the permissions will be root. 

Absolutely right.

> **tomthecabinboy said:**
> 

Basically my script is an rsync script that backs up my photographs and my emails to a mirrored drive on my server. When I am logged on the script works like a dream but like I said I am assuming that on boot up the script will be run under root.

Ami I right? do I need to do anything to ensure the script still runs?? 

In that case, yup, it would be better to run the script as a normal user.

```
 sudo -U <username>
``` will run a given command as the specified user.

So your script may look something like this if your username is 'foo':
```
#!/bin/bash
sudo -U foo rsync BLAH BLAH BLAH
etc...
```If you preface every wanted command with sudo -U <username>, the script will be run as root (because it's being called by /etc/rc./local) but all of its commands will be run as the user of your choice.

If you don't necessarily want to run the script at every boot but would like it to run say every day or week etc..., doing this as a cron job (or even anacron which will play catchup and run the script the next time the computer is on in case it was off during the scheduled task)  for your user would be an excellent way as well.

Hope that helps,
cheers

---

### Post by dcstar on 2007-10-10
> **tomthecabinboy said:**
> I have been told that you can configure Crontab to run on boot up.
I have googled and googled and googled, and not found anything.

Does anyone know how to configure cron to run a script when you start up.

I am running Ubuntu 7.04 for info

Thanks

Tom

anacron will run cron jobs on start up that were missed because the machine was off, however if you want things to always run on boot you don't use cron, you just set it up in the way things are supposed to be to achieve this.

Plenty of posts in the forum on how to set up things to run on boot.

---

### Post by tomthecabinboy on 2007-10-12
THANKS 5-HT

Most Helpful :-)

---

