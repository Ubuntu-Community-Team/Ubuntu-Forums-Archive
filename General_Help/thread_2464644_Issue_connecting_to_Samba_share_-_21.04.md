---
title: "Issue connecting to Samba share - 21.04"
date: 2021-07-07
forum: General Help
---

### Post by pallen38 on 2021-07-07
Hi all,

I have samba set up on 21.04. Works great, I can connect from all machines - iOS, Mac, Windows - except one Windows box. Comparing the Windows box to one that works, I have noticed the following:

Machine A - Windows 10 Enterprise - can not connect to samba share - in a domain

Machine B - Windows 10 Pro - can connect to samba share - workgroup WORKGROUP

Machine C - Ubuntu 21.04 - hosts samba share - workgroup WORKGROUP

A can connect to B, and B to A, both showing protocol 3.1.1.
B can connect to C, using 3.1.1.
A gets "Windows can't find '\\192.168.1.34'. Check the spelling and try again.' when trying to connect to C

On A, in WSL I can see the shares on C using smbclient.

Both windows machines have SMB 1.0/CIFS Client feature enabled. I tried it disabled on the one that doesn't work with no change in outcome.

I am using a very stripped down smb.conf so there are as few variables as possible (attached).

I have checked everything I can think of, and may have forgotten to add some things. I appologize in advance if I've left out any important information. Does anyone have any thoughts on what else I should check?

Thanks!

Patrick

---

### Post by rsteinmetz70112 on 2021-07-08
```
"Windows can't find '\\192.168.1.34'
```

Sounds more like a networking issue, can you ping the ip etc?

---

### Post by pallen38 on 2021-07-08
I can ping it, and can even do smbclient on the SAME machine and see the shares, both with hostname and ip.

---

### Post by TheFu on 2021-07-08
Firewall?
**testparm** output?

---

### Post by pallen38 on 2021-07-12
testparm output:
```

Load smb config files from /etc/samba/smb.conf 
Loaded services file OK. 
Weak crypto is allowed 
Server role: ROLE_STANDALONE 

# Global parameters 
[global] 
    log file = /var/log/samba/log.%m 
    logging = file 
    map to guest = Bad User 
    max log size = 1000 
    panic action = /usr/share/samba/panic-action %d 
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* . 
    passwd program = /usr/bin/passwd %u 
    registry shares = Yes 
    usershare allow guests = Yes 
    idmap config * : backend = tdb 
 
 
[SHARE] 
    path = /share 
    read only = No 
    valid users = @share pallen38 
 
 
[Public] 
    comment = Public 
    guest ok = Yes 
    path = /share/public 
    read only = No 

```

My firewall is inactive.

---

### Post by TheFu on 2021-07-12
Add these to the [global] section:

```
   workgroup = WORKGROUP
   security = user
; This is for the smb server; 2 is Win7 and later
   min protocol = SMB2
```

For both *share* sections, add:
```
  comment = Some valid comment
  browseable = yes
  guest ok = yes/no depending.
  writable = yes/no depending.
  create mask = 0664
  directory mask = 0775
```
After the changes to all 2 sections, restart smb.

I have some hosts allow/deny settings to prevent accidental access outside specific subnets, but with low security, that may not matter to you.

**smbpasswd** must be used for all userids to have Samba passwords which you want to provide access. This is often overlooked in a reasonable expectation that the Unix userid and password would be used. Unix passwords are not used.

---

### Post by pallen38 on 2021-07-12
Hi, 
thanks for the help. One thing I'm confused about is when I saw you wanted me to add the workgroup, I thought surely that's already there but didn't see it in the testparm output. Taking a look at my /etc/samba/smb.conf:
```

pallen38@Desktop01:~$ sudo cat /etc/samba/smb.conf 
[sudo] password for pallen38:  
[global] 
 
   workgroup = WORKGROUP 
 
   log file = /var/log/samba/log.%m 
 
   max log size = 1000 
 
   logging = file 
 
   panic action = /usr/share/samba/panic-action %d 
 
   passwd program = /usr/bin/passwd %u 
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* . 
 
   map to guest = bad user 
 
   usershare allow guests = yes 
 
[SHARE] 
    comment = Share 
    path = /share 
    browsable = yes 
    guest ok = no 
    valid users = @share 
    read only = no 
[Public] 
    comment = Public 
    path = /share/public 
    guest ok = yes 
    browsable = yes 
    read only = no 

```

And, just to make sure I wasn't nuts, I did testparm again, and here is the output, including where it loaded the file from:
```

pallen38@Desktop01:~$ testparm 
Load smb config files from /etc/samba/smb.conf 
Loaded services file OK. 
Weak crypto is allowed 
Server role: ROLE_STANDALONE 
 
Press enter to see a dump of your service definitions 
 
# Global parameters 
[global] 
    log file = /var/log/samba/log.%m 
    logging = file 
    map to guest = Bad User 
    max log size = 1000 
    panic action = /usr/share/samba/panic-action %d 
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* . 
    passwd program = /usr/bin/passwd %u 
    usershare allow guests = Yes 
    idmap config * : backend = tdb 
 
 
[SHARE] 
    comment = Share 
    path = /share 
    read only = No 
    valid users = @share 
 
 
[Public] 
    comment = Public 
    guest ok = Yes 
    path = /share/public 
    read only = No 


```

This is quite odd. At any rate, I will be implementing the rest of the changes you mentioned and testing.

---

### Post by TheFu on 2021-07-12
Errrr.   Both of the outputs above are using cat with sudo, not testparm.  Run **testparm**. That shows what is actually seen by samba.  Appears to be a select/paste error above.


On my system, sudo isn't needed to view anything related to samba - except credentials for connections to other samba shares on the network.

---

### Post by pallen38 on 2021-07-12
Sorry I had posted the same thing twice. I have corrected the post.

---

### Post by pallen38 on 2021-07-12
I have added the lines you mentioned that didn't already exist, and restarted the daemon. The results are the same - I can access through Windows Explorer from on Windows machine. On the other, I still get the "Windows can't find..." in Windows Explorer, but can still connect through WSL smbclient on the same machine.

---

### Post by TheFu on 2021-07-12
Odd that the 
```
security = user
```
isn't showing up.  I'd check the smb.conf manpage for any clear conflicts and correct those.

And just for fun, remove the group and put in 1 or two usernames so we can rule that out as an issue too. I haven't used groups in my samba in about 20 yrs. I've been using 
```
valid users = %S
```

Any chance you could make a text-only chart for which connections work and which do not?  To start:
```
Server - Client - Username - Client OS 
```
Either hostname or IP for the 1st two columns. However you attempt to connect.
I assume all the systems can ping each other too, yes?

I'm not the best at following text buried across multiple posts when the settings change in unknown ways for each.

I take it you've already looked at the log files to see any issues? /var/log/samba  They are per-connection per-client on my system, so it should be easy to get the difference between the systems that connect and those that don't.  It is also possible to run the smbd in debug mode so all the verbose connection data is thrown to a terminal. Tried that?

About now is when Morbius comes in, points out something I missed and figures everything out. We can hope.

---

### Post by rsteinmetz70112 on 2021-07-12
Just a note ```
writable = yes
``` and```
 read only = no
``` do the same thing. The man page calls them an "inverted synonym"

---

### Post by ActionParsnip on 2021-07-12
Is there anything in the Windows system or application logs, or in the Samba log in the server side?

---

### Post by ActionParsnip on 2021-07-12
Make sure the problematic client has the local firewall allowing the traffic.

---

