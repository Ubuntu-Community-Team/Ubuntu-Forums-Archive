---
title: "unable to connect to SSH with NX client.."
date: 2008-05-21
forum: General Help
---

### Post by Mia_tech on 2008-05-21
after doing an upgrade of the Openssh server, I'm not able to connect to it with NX client, I know Openssh server is up and running b/c I can connect with putty...

any help appreciated

thanks

---

### Post by mrprefect on 2008-05-21
Care to elaborate a bit more? 
Did you add the user you want to connect with to nxserver? 
Did you copy the RSA public key to the client? 
What error are you getting when you try to connect?

---

### Post by superyounan1 on 2008-05-21
I had a problem too, and I got a very generic "NX error". I tried logging in from another machine (running ubuntu), and I got some other error about the server not being able to delete a file (I know my description is vague and weird), so I logged into the server and moved that file in the error, and vioala, it worked

try maybe updating your NX client incase there is a newer version that will give you a meaningful error or log

---

### Post by cenwesi on 2008-05-21
delete /usr/NX/home/nx/.ssh/known_host file 
restart nxserver (/etc/init.d/nxserver restart)
and you will be fine.

---

### Post by superyounan1 on 2008-05-21
deleting the known_hosts file might be needed, but that definitely wasn't what was giving me the error, but since i can't pony up more info, i digress

---

### Post by Mia_tech on 2008-05-22
this is the error I'm getting when trying to login

```
NX> 203 NXSSH running with pid: 3996
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: 10.200.50.5 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.1.0-5 - LFE
NX> 105 Hello NXCLIENT - Version 3.0.0
NX> 134 Accepted protocol: 3.0.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: jorge
NX> 102 Password: ********
NX> 500 Authentication failed
NX> 500 Remote host identification has changed
NX> 500 Offending key in /usr/NX/home/nx/.ssh/known_hosts
NX> 999 Bye.
NX> 280 Exiting on signal: 15

```
Thanks

---

### Post by Mia_tech on 2008-05-22
I solved my problem following cenwesi's post..

---

### Post by murlex on 2010-03-18
I am having the same problem, except that I dont have a known_host in /usr/NX/home/nx/.ssh/

Does anyone have a solution to this problem?

thanks in advance

---

### Post by doas777 on 2010-03-18
are you using a nx connection config from before? try creating a new config for that connection with the wizard and see if that has the same issue. i had somthing simmilar come up a few weeks ago, and I just created a new one.

---

