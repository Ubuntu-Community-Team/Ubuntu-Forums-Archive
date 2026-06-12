---
title: "Samba / Winbind Multiple Instances."
date: 2016-03-31
forum: General Help
---

### Post by andrew292 on 2016-03-31
Dear All.

I am using Ubuntu 15.10 and Samba 4.1.17-Ubuntu with libnss-winbind, libpam-winbind, and krb5-user. Samba is configured as a member-server.

I am trying to get two 'instances' of Samba and Winbind running together on the same Ubuntu installation so that I can authenticate users from two separate Windows AD domains at once and so share a common set of files out to both domains. Please note that i cannot trust the two AD domains to each other (one is SBS).

I am able to use symbolic links to start two smbd, nmbd and winbindd processes. I have modified the start up scripts appropriately to start the processes using separate config files with 'instance' specific lock, private, cache, log directories, pid files etc. I have configured two network interfaces and set the two sambas to listen on each as appropriate. I am able to join to the two windows AD domains without errors. Everything was going well until i tried to start up two winbindd processes at once. This didn't work, i could only have one winbindd process running at the same time. When i try to start a second process at the same time it doesn't start. Both windbindds work but just not at the same time. So i have this system working, joined to two domains etc etc, but winbindd only works if i start one winbindd or the other and so i can share files out to only one AD domain at once.

ie:

nano /etc/samba/smb.1.conf
nano /etc/samba/smb.2.conf (with appropriate entries changed : interfaces =  and dirs to samba.2)

```
[global]

   workgroup = mydomain
   server string = Samba Server Version %v
   security = ads
   realm = CORP.COMPANY.COM
   socket options = TCP_NODELAY IPTOS_LOWDELAY SO_RCVBUF=131072 SO_SNDBUF=131072
   use sendfile = true

   interfaces = eth0
   bind interfaces only = yes

   wins support = no

   idmap config * : backend = tdb
   idmap config * : range = 100000-299999
   idmap config TEST : backend = rid
   idmap config TEST : range = 10000-99999

   winbind separator = /
   winbind enum users = yes
   winbind enum groups = yes
   winbind use default domain = yes
   winbind refresh tickets = yes
   winbind max domain connections = 10

   restrict anonymous = 2
   log file = /var/log/samba/log.%m
   max log size = 50

   #winbindd:socket dir = /var/run/samba.1/winbindd
   #winbindd socket directory = /var/run/samba.1/winbindd <- this doesn't work
   #winbindd:privileged socket dir = /var/run/samba.1/winbindd_privileged <- this doesn't work

   pid directory = /var/run/samba.1
   lock directory = /var/run/samba.1
   ncalrpc dir = /var/run/samba.1/ncalrpc
   cache directory = /var/cache/samba.1

   #============================ Share Definitions ==============================

   [testshare]

   comment = Test share
   path = /xvdb1
   read only = no
   #force group = "Domain Users"
   directory mask = 0770
   force directory mode = 0770
   create mask = 0660
   create mask = 0660
   force create mode = 0660
   valid users = domain/username
   admin users = domain/username

```

testparm /etc/samba/smb.1.conf and testparm /etc/samba/smb.2.conf return no errors

It was noted that the init.d script for winbind is incorrect :

mkdir -p /var/run/samba/winbindd_privileged || return 1

Whereas the actual winbindd_privileged directory is in /var/lib/samba. Using the winbindd:privileged socket dir = directive in smb.conf doesn't appear to work. I will tackle this later if it impacts on what i'm trying to achieve.

cd /usr/sbin

ln -s smbd /usr/sbin/smbd.1
ln -s smbd /usr/sbin/smbd.2
ln -s nmbd /usr/sbin/nmbd.1
ln -s nmbd /usr/sbin/nmbd.2
ln -s winbindd /usr/sbin/winbindd.1
ln -s winbindd /usr/sbin/winbindd.2

/usr/sbin/smbd.1 -D -s /etc/samba/smb.1.conf
/usr/sbin/smbd.2 -D -s /etc/samba/smb.2.conf
/usr/sbin/nmbd.1 -D -s /etc/samba/smb.1.conf
/usr/sbin/nmbd.2 -D -s /etc/samba/smb.2.conf
/usr/sbin/winbindd.1 -D -s /etc/samba/smb.1.conf
/usr/sbin/winbindd.2 -D -s /etc/samba/smb.2.conf

ps aux | grep smbd -> yes there are two yay
ps aux | grep nmbd -> yes there are two yay
ps aux | grep winbindd -> only one no boo

So for both domains but only using one winbindd at once ...

wbinfo -u works
wbinfo -g works
getent passwd works
getent group works
kinit administrator works
chhown domain/user directory works
accessing shares with AD permissions set, from windows logged in as AD user works

I suspected that the winbindd socket was the problem. If I use the winbindd:socket dir = directive in smb.conf, i can move the winbind pipe to a different directory, and so set up two winbindds using symbolic links with separate smb.conf files to use separate winbindd pipes. I have tested this, and when using separate winbindd socket directories i can get two winbindd s running at once, so this has confirmed that this is why two would not run at once before when using only one winbindd socket.

The problem is that once i move the winbindd socket using winbindd:socket dir = in smb.conf , winbind/nss ? stops working. I'm confused at to which services need to access the winbindd pipe. I must have to tell some process that the windbindd socket is now in a different directory right ? Do i need to tell nss to use the moved socket ? I gather that smbd knows that the socket has moved as it's in the smb.conf file. Winbindd obviously knows as the socket was actually moved to the new directory. Is a socket used to accept tcp connections from windows clients to samba and if so which one ?

with winbindd:socket dir = xxx set

wbinfo -u not work
wbinfo -g not work
getent passwd not work
getent group not work
kinit administrator works
chhown domain/user directory not work
accessing shares with AD permissions set, from windows logged in as AD user not work

Can anyone tell me in nss_switch.conf when i put winbind, how does this find the winbind service ? how can i point it to the winbind which uses the moved socket ... ?

Can anyone help with this ? or point me to the right documentation ..

I would love to read an overview of how Samba, Winbind and nss work together but have been unable to find such a thing.

Any help much appreciated.

Andrew.

---

### Post by oldos2er on 2016-04-01
Are you aware that 10.04 is no longer supported?

---

### Post by lisati on 2016-04-14
I notice that the OP has been edited multiple times, including an update to the Ubuntu version number being used.

If you're going to include information from configuration files, placing the information between [noparse]```
 and 
```[/noparse] can help make the post easier to read.

---

### Post by andrew292 on 2016-04-14
Thank you - i will do this from now on. I am just getting the details correct. And sorry for deleting the code tags, that was an accident as i am editing my post in notepad and pasting into the forum, and didn't notice you made the changes so they got overridden.

Andrew.

---

