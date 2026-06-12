---
title: "Crontab for rsync not working"
date: 2007-05-16
forum: General Help
---

### Post by globemast on 2007-05-16
Hello guys,

I am trying to create a crontab entry (for my username) for rsync but i am having some difficulties.

```

48 10 * * 1-5 /usr/bin/rsync --delete -e ssh -v -r -l -H /home/home_nick_backup/ nick@remoteserver.com\:DesktopSnapshots/ >> /home/nick/rsync.log

```

I have tried to run the above rsync command from the prompt and it works just fine. 

As for the ssh key passphrase this is stored in ssh_agent and i don't need to provide it

I tried the following in the crontab and it works 
```

date >> /home/nickl/date.log

```

Please note that the crontab is not run as sudo. 

Any suggestions ???

Thanks in advance.

---

### Post by fanatik on 2007-05-16
cron won't know about your ssh_agent.. you might want to set up a specific key with no password, just for the purposes of rsync.

---

