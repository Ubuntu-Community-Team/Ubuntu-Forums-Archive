---
title: "Samba change killed my setup"
date: 2016-04-20
forum: General Help
---

### Post by jeff.sadowski on 2016-04-20
When ubuntu 14.04 went from samba 4.1.6 to 4.3.8 it killed my setup. Before the change I was able to run wbinfo -u and get a list of users. Now when I run  wbinfo -u it returns nothing. I tried dis-joining and rejoining the domain with no luck,

Here is my complete smb.conf
```

[global]
   security = ads
   realm = SUBDOMAIN.DOMAIN.TOP
   workgroup = SUBDOMAIN
   idmap config * : backend = tdb
   idmap config * : range = 2000-7999
   idmap config SUBDOMAIN:backend = ad
   idmap config SUBDOMAIN:schema_mode = rfc2307
   idmap config SUBDOMAIN:range = 8000-9999999
   winbind nss info = rfc2307
   winbind use default domain = yes

```

Here is my script to connect to the domain. I call it net_join.sh
```

echo Enter a Machine Name
read machine
echo $machine > /etc/hostname
hostname `cat /etc/hostname`
echo Enter a Domain Admin Account ex:Administrator
read admin
net ads join -U $admin osName="`lsb_release -a|grep "^Distributor ID:"|cut -d: -f2|awk '{print $1}'` joined `date "+%F"`" osVersion=`lsb_release -a|grep "^Release:"|cut -d: -f2|awk '{print $1}'`

```

Here is my script to leave the domain. I call it net_leave.sh
```

read admin
net ads leave -U $admin

```

Here is my script to clear winbind. I call it winbind_clear.sh
```

service winbind stop
#service smbd stop
service samba stop
net cache flush
rm -f /var/lib/samba/*.tdb
rm -f /var/lib/samba/group_mapping.ldb
sleep 1
service samba start
#service smbd start
service winbind start

```

Can anyone point me to why my setup has stopped working? Or maybe some steps I can take to learn why it is failing. Do I need to add something for debugging?

---

### Post by i-u0untu-4 on 2016-04-20
I got exactly the same problem here. What is your AD-DC? Mine is an old w2k3 Server. 
I got another domain member with Ubuntu 14.04 LTS but without Samba Update to 4.3 running with the same config files and it is still able to wbinfo -u, so im pretty sure the problem is 4.3 here.

My first guess is: Some default options, mostly security/encryption related to badlock bug, changed. See [https://wiki.samba.org/index.php/Sam...b.conf_options]("https://wiki.samba.org/index.php/Samba_4.3_Features_added/changed#New_smb.conf_options") 
Maybe one of these changes prevent talking to outdated Domain Controllers. (in my case, windows 2003, very outdated, i know).

---

### Post by i-u0untu-4 on 2016-04-20
My first guess is: Some default options, mostly security/encryption related to badlock bug, changed. See [https://wiki.samba.org/index.php/Samba_4.3_Features_added/changed#New_smb.conf_options](https://wiki.samba.org/index.php/Samba_4.3_Features_added/changed#New_smb.conf_options) 
Maybe one of these changes prevent talking to outdated Domain Controllers. (in my case, windows 2003, very outdated, i know).

---

### Post by jeff.sadowski on 2016-04-20
My favorite AC DC song is Highway to Hell.... Oh wait you asked for my AD DC, I have 2 at 2008 and one at 2012 I agree with your idea that it may be a default option and I am looking through the samba mailing list which I follow regularly to find an answer.

client ldap sasl wrapping = plain seems to work a little better for me but I get "Error looking up domain users" when I do a wbinfo -u

I have like 12 computers on ubuntu that are still with the older samba.

-----------------------
Update 2016-04-21: thanks i-u0untu-4 the link you gave, gave me a bunch of options to try. The relevant options for me were

```

ldap server require strong auth = no
client ldap sasl wrapping = plain

```

I added them to my smb.conf and it all works again.

---

