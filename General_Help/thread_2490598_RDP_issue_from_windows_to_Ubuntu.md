---
title: "RDP issue from windows to Ubuntu"
date: 2023-09-08
forum: General Help
---

### Post by muklinux on 2023-09-08
Hello, 

I have just installed Ubuntu desktop 22.04.3 LTS today on a VMware server and joined to the domain while installing. After install I added an enterprise user to the system I have ben unable to RDP from a windows domain system to the Ubuntu desktop using either the enterprise credentials or the local credentials I created. each time I get " log in attempt failed" message. I have checked the sssd config and comparing to what saw online it looks right. This is a .LOCAL domain for my home lab if that matters.
I  have tried changing the login to the ubuntu_PC_Name\username and password and still get the error. 

I am quite inexperienced with Linux, but should the enterprise user even need created? I would think once on a domain all users could access. I am just not sure what else to check.

Here is the sssd.conf

[sssd]
domains = HomeLab.Local
config_file_version = 2
services = nss, pam


[domain/HomeLab.Local]
default_shell = /bin/bash
krb5_store_password_if_offline = True
cache_credentials = True
krb5_realm = HOMELAB.LOCAL
realmd_tags = manages-system joined-with-adcli
id_provider = ad
ldap_sasl_authid = ubuntu$
fallback_homedir = /home/%u@%d
ad_domain = HomeLab.Local
use_fully_qualified_names = True
ldap_id_mapping = True
access_provider = ad
simple_allow_users = testuser

---

### Post by MAFoElffen on 2023-09-08
Since you are a Windows User, you know that with RDP, you cannot be logged into the target with the same User you are trying to use in RDP. That seems obvious, but many people using RDP overlook that, so I thought I would throw that out first. A lot of place will create an RDP User account because of that limitation. Or ssh into the machine and disconnect "that user" in all sessions.

Next, your Ubuntu VM needs to have xrdp server installed, the service running, the port listening, and if UFW is enabled, that port opened up...

Of course, you also need a network path to it.

Can you ping it? Can you ssh into it with that same user credentials?

---

