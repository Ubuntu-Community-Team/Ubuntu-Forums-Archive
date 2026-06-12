---
title: "Windows NFS share With AD folder permission problems"
date: 2023-10-05
forum: General Help
---

### Post by lavoiekeven on 2023-10-05
Hi,

We got and Active directory domain. Connected to this domain we have a Windows server 2022 and an Ubuntu desktop 22.04.

The windows server share a folder with nfs.

This folder is mounted on the ubuntu desktop from the fstab with this :
[HTML]
myhost.com:/Production  /media/Production  nfs       defaults,acl    0       0
[/HTML]


When I create a new folder within the mount let say for example /media/Production/Test

The folder is created but The windows server is not about to recognize the folder owner event if i'm connect with an LDAP user.

I try every combination of chmod / chown on the Test folder
I also tried with setfacl but it give me the error "Operation not supported"


I'm able to correct the folder from the Windows server with the permission wizard but I need to do it from the ubuntu.
Any ideas.

---

### Post by MAFoElffen on 2023-10-05
Is the Ubuntu machine joined to the Windows Domain through SSSD?

If so, then the user logging into the Domain is a part of the Domain User Group and is an LDAP (Active Domain) user, right? You want to be able to login as an LDAP user, authenticated via Kerberos. For that to happen, check the /etc/sssd/sssd.conf configuration file... It should be similar to this, to get a user to be able to log in as an ldap user:
```

[sssd]
config_file_version = 2
domains = example.com

[domain/example.com]
id_provider = ldap
ldap_uri = ldap://ldap01.example.com
ldap_search_base = dc=example,dc=com
auth_provider = krb5
krb5_server = kdc01.example.com,kdc02.example.com
krb5_kpasswd = kdc01.example.com
krb5_realm = EXAMPLE.COM
cache_credentials = True

```

---

### Post by lavoiekeven on 2023-10-06
I joined the domain with realmd.

This file was created automatically.

The LDAP authentication works on the ubuntu. But nether the user or the group is recongized by the Windows Share when I'm create new folder or new file. But on the ubuntu the Forlder is ok 

```

[sssd]
domains = mydomain.lan
config_file_version = 2
services = nss, pam


[domain/mydomain.lan]
default_shell = /bin/bash
krb5_store_password_if_offline = True
cache_credentials = True
krb5_realm = MYDOMAIN.LAN
realmd_tags = manages-system joined-with-adcli
id_provider = ad
fallback_homedir = /home/%u@%d
ad_domain = mydomain.lan
use_fully_qualified_names = True
ldap_id_mapping = True
access_provider = simple
simple_allow_groups = g_ssh_serveurs

```

Here what we see when I create a new folder on the Ubuntu:

[[IMG]https://i.postimg.cc/HV3XRjDM/ubuntu-created-bash.png[/IMG]]("https://postimg.cc/HV3XRjDM")

On the Windows server

[[IMG]https://i.postimg.cc/gxJ8WdmT/Windows-see.png[/IMG]]("https://postimg.cc/gxJ8WdmT")


[[IMG]https://i.postimg.cc/21KvjJ58/Windows-see-ex.png[/IMG]]("https://postimg.cc/21KvjJ58")

---

### Post by MAFoElffen on 2023-10-06
Not a pretty or easy fix... Here: [https://social.technet.microsoft.com/Forums/ie/en-US/070565a8-b031-4f16-a9ee-1319f07f42cf/how-to-mount-nfs-share-on-windows-10-pro-and-use-unix-attributes-from-active-directory-for?forum=winserverDS](https://social.technet.microsoft.com/Forums/ie/en-US/070565a8-b031-4f16-a9ee-1319f07f42cf/how-to-mount-nfs-share-on-windows-10-pro-and-use-unix-attributes-from-active-directory-for?forum=winserverDS)

It never seems to surprise me that Win Server 2003 had automatic remapping for Unix POSIX type uuid's and guid's to AD. But with current Win servers, it is a manual affair. It's like Windows went backwards with not making that easier and more sell-able over time.

---

### Post by lavoiekeven on 2023-10-12
Thank you, with the mapping within the the ad profil of my users and group it worked.

---

### Post by MAFoElffen on 2023-10-12
Glad to help, and happy it worked!!!

If solved, please select the "Thread Tools" link in the upper right to mark your thread as solved, so that other Users can find your solution to their similar problems.

---

