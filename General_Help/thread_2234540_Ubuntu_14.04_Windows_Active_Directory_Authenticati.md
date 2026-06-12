---
title: "Ubuntu 14.04 Windows Active Directory Authentication - Winbind"
date: 2014-07-15
forum: General Help
---

### Post by mpaiva on 2014-07-15
Hi,

to authenticate Ubuntu 14.04 in active directory:

1 - Install

sudo apt-get install winbind libpam-winbind libnss-winbind krb5-user krb5-config libpam-krb5

2 - Edit files

# /etc/nsswitch.conf

passwd:         compat winbind
group:          compat winbind
shadow:         compat


# /etc/krb5.conf

[libdefaults]
	default_realm = DOMAIN

[realms]
	DOMAIN = {
		kdc = adcserver1.domain
		Kdc = adcserver2.domain
 		admin_server = adcserver1.domain adcserver2.domain
	}

[domain_realm]
        adcserver1.domain = DOMAIN
 	adcserver2.domain = DOMAIN
	.domain = DOMAIN
        $HOSTNAME.domain = DOMAIN
        domain = DOMAIN


# /etc/samba/smb.conf

workgroup = DOMAIN
realm = DOMAIN
security = ADS
encrypt passwords = yes
password server = adcserver1.domain adcserver2.domain
idmap uid = 10000-20000
idmap gid = 10000-20000
winbind enum users = yes
winbind enum groups = yes
winbind refresh tickets = true
template homedir = /home/%D/%U
template shell = /bin/bash
winbind use default domain = yes
restrict anonymous = 2
winbind offline logon = yes


# /etc/pam.d/common-session (add at the end of the file)
# end of pam-auth-update config 
# create homedir for new users
session required pam_mkhomedir.so skel=/etc/skel umask=0022


# /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
[SeatDefaults]
user-session=ubuntu
greeter-show-manual-login=true

3 - Run
sudo service smbd restart
sudo service nmbd restart
sudo service winbind restart


4 - Add computer to domain
sudo kinit domain_user@LASALLE
sudo net ads join -U domain_user


5 - Test
wbinfo -u
wbinfo -g
getent passwd domain_user
su domain_user

6 - Reboot

---------------------

If you need to clear cache:
sudo net cache flush


Marcus Paiva

---

### Post by pla on 2014-12-20
Perfect. Thanks!

---

### Post by bo-guo on 2015-06-22
I spent most of the weekend going through various sources trying to get my newly-built 14.04 server talk to Windows AD with no avail.  This morning, I came upon this post and decided to give it as my final try for the moment.  Success!!!  Thank you so much for sharing.

---

### Post by ZippyDan on 2015-07-09
Fantastic guide.

Note that **Step 4**...

> [COLOR=#000000]4 - Add computer to domain[/COLOR]
[COLOR=#000000]sudo kinit domain_user@LASALLE[/COLOR]
[COLOR=#000000]sudo net ads join -U domain_user[/COLOR]

...will fail unless you have defined your machine with a hostname ON THE DOMAIN in /etc/hosts

You should possibly add another section to **Step 2 - Edit Files**

Something like this will fix your problems:

```
# sudo vi /etc/hosts

127.0.0.1 localhost
127.0.1.1 myPCname.domain myPCname
```

---

