---
title: "[B]tcp contradiction[/B]"
date: 2021-11-30
forum: General Help
---

### Post by Old Jimma on 2021-11-30
Hello Ubuntuers:


I need your help understanding a "**tcp contradiction**."

I have a raspberry pi that is a server that backs up other linux computer clients on my network. 

I'm in the process of making this process more secure by modifying the **sshd_config** file to "do business" on another port number... let's call it port number **XYZ** just for fun.

Before i began making the possess of making tcp more secure, 
[LIST]
[*]tcp business was conducted over port 22, and 
[*]the UFW file on each client included a line that restricted the tcp session to the raspberry pi's IP address
[*]
[/LIST]

tcp business was conducted over port 22, the line in each computer's UFW file was:

> 
To                          Action       From
--                          ------         ----           
**22**                      ALLOW       pi's IP address  


That line is still in each clent's UFW file, the **sshd_config** file  on the server indicates that tcp business is to take place over port XYX... and the backups still work, and I don't know why. 

I thought that because the clients were restrict tcp business over port 22 only, the backups would not work.

Can someone explain why they continue to work?

How do I verify that tcp business is taking place over port **XYX**?

Should I modify the line in clients' UFW file to indicate that tcp business can take place only over port **XYZ** from the raspberry's IP address (it current seems like doing that won't have any effect, or provide any security).

[B]Old Jimma
Confused Old Man in the Old Country[/B]

---

### Post by Doug S on 2021-11-30
Does your pi server do all the backup work? For example does it "pull" the data from the clients? Could you show us the relevant portion of your client's sshd_config file. For example, here is one of mine (where, and because it is internal on my LAN only, I have not changed away from the default port 22):

```
doug@s19:~/tmp/tmp$ [COLOR="#FF0000"]grep -B 2 -A 5 "Port " /etc/ssh/sshd_config[/COLOR]
Include /etc/ssh/sshd_config.d/*.conf

[COLOR="#FF0000"]#Port 22[/COLOR]
#AddressFamily any
#ListenAddress 0.0.0.0
#ListenAddress ::

#HostKey /etc/ssh/ssh_host_rsa_key
```

Could you also show us an example of at least one of your client's listening ports. For example:

```
doug@s19:~/tmp/tmp$ [COLOR="#FF0000"]sudo ss -lntup[/COLOR]
Netid               State                Recv-Q                Send-Q                                     Local Address:Port                               Peer Address:Port               Process
udp                 UNCONN               0                     0                                          127.0.0.53%lo:53                                      0.0.0.0:*                   users:(("systemd-resolve",pid=821,fd=12))
udp                 UNCONN               0                     0                                    192.168.111.136%br0:68                                      0.0.0.0:*                   users:(("systemd-network",pid=557,fd=16))
tcp                 LISTEN               0                     50                                               0.0.0.0:139                                     0.0.0.0:*                   users:(("smbd",pid=1210,fd=48))
tcp                 LISTEN               0                     1                                                0.0.0.0:5900                                    0.0.0.0:*                   users:(("qemu-system-x86",pid=1436868,fd=24))
tcp                 LISTEN               0                     4096                                       127.0.0.53%lo:53                                      0.0.0.0:*                   users:(("systemd-resolve",pid=821,fd=13))
[COLOR="#FF0000"]tcp                 LISTEN               0                     128                                              0.0.0.0:22                                      0.0.0.0:*                   users:(("sshd",pid=1030,fd=3))[/COLOR]
tcp                 LISTEN               0                     50                                               0.0.0.0:445                                     0.0.0.0:*                   users:(("smbd",pid=1210,fd=47))
```

To determine if port XYZ is being used during a backup, look for it during an in progress backup. I'll use port 22, and have 2 ssh sessions to a server at 192.168.111.136:

```
doug@s19:~/tmp/tmp$ [COLOR="#FF0000"]ss -nt | grep :22[/COLOR]
ESTAB  0       0        192.168.111.136:[COLOR="#FF0000"]22[/COLOR]      192.168.111.122:53671
ESTAB  0       36       192.168.111.136:[COLOR="#FF0000"]22[/COLOR]      192.168.111.122:53781
```

---

### Post by Old Jimma on 2021-11-30
[B]Hi Doug S:

Here are the data you requested:[/B]

> Does your pi server do all the backup work?
 Yes the pi does all of the work.

 > For example does it "pull" the data from the clients?
Yes the pi "pulls" data from each client to a drive mounted on the pi. Here is an example of the rsync command

> 
rsync --delete -az -e ssh [email]client@clent.ip[/email]:/home/client/ /mnt/mounted_drive_on_pi



> 
$ grep -B 2 -A 5 "Port " /etc/ssh/sshd_config


> 
## [https://www.digitalocean.com/community/tutorials/ssh-essentials-working-with-ssh-servers-clients-and-keys](https://www.digitalocean.com/community/tutorials/ssh-essentials-working-with-ssh-servers-clients-and-keys)
## from
#Port 22
## to
Port 45629
########################################################



> 
ss -nt | grep :22


> 
ESTAB      0       79392    192.168.1.161:22        192.168.1.136:45629


[B]Thanks, 
Old Jim[/B]

---

### Post by Doug S on 2021-11-30
Is the Pi server 192.168.1.161 and the client 192.168.1.136?

Could you also show us an example of at least one of your client's ssh listening ports. For example: "[COLOR="#FF0000"]sudo ss -lntup[/COLOR]'

---

### Post by Old Jimma on 2021-12-01
Hi Doug S:

192.168.1.161 is the pi server.

192.168.1.136 is a client.

sudo ss -lntup

the forum won't let me include this output saying:

> 

The following errors occurred with your submission

    You have included a total of 35 images in your message. The maximum number that you may include is 8. Please correct the problem and then continue again.

    Images include use of smilies, the BB code [img] tag, and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.




---

### Post by Doug S on 2021-12-01
Well, it seems to be working fine. UFW is just a front end for iptables.

Potentially the issue is that the pi is using port 22, and sometimes iptables rules do not discern between source and destination ports.

rsync is figuring out the correct client port and is using it.

Myself, I would still modify the client's UFW allow rule.

---

