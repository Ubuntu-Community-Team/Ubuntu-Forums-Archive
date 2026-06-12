---
title: "Access Ubuntu directory over samba from a windows machine"
date: 2012-11-04
forum: General Help
---

### Post by themkn on 2012-11-04
Hi

I want to access a directory on the ubuntu server over samba from a windows machine. I installed samba and in the smb.conf file I added the following lines:

```
comment = Ubuntu File Server Share
path = /srv/samba/share
browsable = yes
guest ok = no
read only = no
create mask = 0755
admin users = admin
```

On the windows machine I mount the network drive with \\172.20.1.2 and then I click on browse and I see the share folder. When I want to access that share folder, it asks for the credentials. I enter the credentials (username: admin, password: secret) and then I see a error msg.
```
\\172.20.1.2\share is not accessible. You might not have permission to use this network resource
```

I am sure that smb works fine because when I change the lines in the smb.conf from ```
guests ok = no
``` to ```
guest ok = yes
``` then I can mount the drive.

I have also generated the user admin as a samba user. When I run ```
sudo pdbedit -L -v
``` it shows me the following
```
Unix username:        admin
NT username:          
Account Flags:        [U          ]
User SID:             someID
Primary Group SID:   someID
Full Name:            admin
Home Directory:       \\aa1-app-001\admin
HomeDir Drive:        
Logon Script:         
Profile Path:         \\aa1-app-001\admin\profile
Domain:               AA1-APP-001
Account desc:         
Workstations:         
Munged dial:          
Logon time:           0
Logoff time:         a date
Kickoff time:         a date
Password last set:    a date
Password can change:  a date
Password must change: a date
Last bad password   : 0
Bad password count  : 0
Logon hours         : FFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF
```

Does anyone know what I am doing wrong or what else I should check to see what is the problem?

---

### Post by Mark Phelps on 2012-11-04
Don't do this myself ... but you could look through the details in the linked thread: 

[http://www.noobslab.com/2012/03/configure-samba-sharing-between-ubuntu.html]("http://www.noobslab.com/2012/03/configure-samba-sharing-between-ubuntu.html")

---

### Post by themkn on 2012-11-05
What I found out now is that I can mount the samba share from a Mac OSX but not from the windows machine??

>> Solution: restart windows machine :). The windows machine cached or saved an old credential

---

