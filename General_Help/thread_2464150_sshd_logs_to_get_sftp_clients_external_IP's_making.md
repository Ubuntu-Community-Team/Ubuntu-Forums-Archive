---
title: "sshd logs to get sftp clients external IP's making sftp connections"
date: 2021-06-25
forum: General Help
---

### Post by atulrajput0786 on 2021-06-25
hi folks,

I'm not able to gather logs from auth.log files for last 1 year. question is does sshd saves logs for this period?. if yes how should i able to gather it. I only can see last month logs. 

Thanks


A

---

### Post by scorp123 on 2021-06-25
> **atulrajput0786 said:**
>  I only can see last month logs. 



Did you check the contents of **"/var/log"** ??  Chances are **[COLOR="#B22222"]log rotation[/COLOR]** is active and the old logs have been compressed and are now stored as ***.gz** (Gnu ZIP) files.

---

### Post by coffeecat on 2021-06-26
Support, not chat.

*Thread moved to **General Help**.*

---

### Post by TheFu on 2021-06-27
You can configure logs to be retained for as long as you like.  When it comes to ssh and related sensitive network connections, those should be locked down by firewall rules to a whitelist.  If users will only come from your country, no need to allow the other 190+ country IPs to have any access at all. Block them

You can also use DenyHosts or Fail2Ban to dynamically block failed attempts, but I've seen where 3 attempts will come from each IP of about 1,000 and stop. Then they come back 62 minutes later and try again. Over and over and over.  Why 62 minutes?  Because the default firewall blocking is 1 hr.  Change it to 1 week or 1 month to drastically reduce it.  Also, ssh in the sshd_config file can force connections to only use key-based authentication or to allow passwords only from a few trusted subnets.

Don't allow anyone without a legitimate need access to ssh, scp, rsync, sftp, or the 50 other connection stuff that is based on ssh.  
And one last thing. For a WAN connection, never use the default ssh port 22/tcp.  Always shift that somewhere else.

---

