---
title: "How to &quot;Revert&quot; to Ubuntu's default firewall settings, that comes with install?"
date: 2015-05-10
forum: General Help
---

### Post by mikodo on 2015-05-10
I've had problems with setting ufw and gufw, on this new 14.04 install.    I want to revert to what comes with an install natively.    Can I just shut off gufw, delete it and ufw. Then, reboot?    Would that do it?  Or, is there a "proper way to do it?    Thanks.

---

### Post by coffeecat on 2015-05-10
> **mikodo said:**
> 
Can I just shut off gufw, delete it and say reboot?


That won't work as gufw is simply the frontend to ufw. The ufw rules that you defined in gufw will still be in place. These are in two files /lib/ufw/user.rules and /lib/ufw/user6.rules. 

The quick way would be simply to disable ufw with:

```
sudo ufw disable
```

But if you wish also to revert to the default set of ufw rules and create new user.rules and user6.rules files, these are the default contents in 15.04 - I don't have access to 14.04, but they are probably the same:

/lib/ufw/user.rules

```
*filter
:ufw-user-input - [0:0]
:ufw-user-output - [0:0]
:ufw-user-forward - [0:0]
:ufw-user-limit - [0:0]
:ufw-user-limit-accept - [0:0]
### RULES ###
-A ufw-user-limit -m limit --limit 3/minute -j LOG --log-prefix "[UFW LIMIT BLOCK] "
-A ufw-user-limit -j REJECT
-A ufw-user-limit-accept -j ACCEPT
COMMIT
```

/lib/ufw/user6.rules

```
*filter
:ufw6-user-input - [0:0]
:ufw6-user-output - [0:0]
:ufw6-user-forward - [0:0]
### RULES ###
COMMIT
```

Both of those need to be owned by root and have 640 permissions.

---

### Post by mikodo on 2015-05-10
> **coffeecat said:**
> That won't work as gufw is simply the frontend to ufw. The ufw rules that you defined in gufw will still be in place. These are in two files /lib/ufw/user.rules and /lib/ufw/user6.rules.   The quick way would be simply to disable ufw with:  ```
sudo ufw disable
```  Yes, I was going to change the body of text to state that I needed to disable ufw before deleting.  As, I am really not that aware of how to do any of the rest you mentioned, and I am pressed for time for learning, I hope just:   " sudo ufw disable"    Will be secure for my one and only desktop.  Thank you.

---

### Post by dino99 on 2015-05-10
if you disable ufw, then you cant be secure, as there is no more filtering ;)
[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)
from gufw, simply let the default : status=on, incoming=deny, outgoing=allow

---

### Post by mikodo on 2015-05-10
This is what I used before this new install but, I am having trouble connecting to services now. I don't know why now. Your right dino99, I should have at the very least Deny = Incoming.

```
$ sudo ufw status
[sudo] password for mikodo: 
Status: active

To                         Action      From
--                         ------      ----
25,53,80,110,143,443,8001/tcp ALLOW OUT   Anywhere
53,67,68/udp               ALLOW OUT   Anywhere
25,53,80,110,143,443,8001/tcp (v6) ALLOW OUT   Anywhere (v6)
53,67,68/udp (v6)          ALLOW OUT   Anywhere (v6)


```
Thank you, too.

EDIT: I figured out the problem for allowing the FTP file transfer, by setting the ufw as dino99 said in the earlier post. Then, reconfigured ufw back to what I had before. I think next install, I'll not bother with setting the ufw rules myself, and just use the Ubuntu Firewall.  Thanks.

---

