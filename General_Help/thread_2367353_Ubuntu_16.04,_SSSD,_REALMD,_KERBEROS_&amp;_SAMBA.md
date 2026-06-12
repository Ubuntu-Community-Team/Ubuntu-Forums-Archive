---
title: "Ubuntu 16.04, SSSD, REALMD, KERBEROS &amp; SAMBA"
date: 2017-07-29
forum: General Help
---

### Post by msw1970 on 2017-07-29
Hi All

I'm having a real issue getting Ubuntu 16.04 joined to an Active Directory domain and be able to access Samba defined shares. I'm pretty sure I have SSSD, REALMD and KERBEROS setup correctly as I"m able to login to the server via SSH using an active directory user and further 'sudo getent passwd' lists all of the domain users. A machine account exists in AD for the server and the domain join with adcli is successful so I'm confident that this element is correctly configured.

However, I simply cannot get SAMBA to work with this. My smb.conf config is as follows..

> #======================= Global Settings =======================


[global]
   workgroup = EXAMPLE
   realm = EXAMPLE.COM
   security = ads
   client signing = yes
   client use spnego = yes
   kerberos method = system keytab
   server string = %h server (Samba %v, Ubuntu)
   dns proxy = no
   log file = /var/log/samba/log.%m
   max log size = 1000
   syslog = 0
   panic action = /usr/share/samba/panic-action %d
   server role = standalone server
#   passdb backend = tdbsam
    client use spnego = yes
    client ntlmv2 auth = yes
    encrypt passwords = yes
   obey pam restrictions = yes
   unix password sync = yes
   passwd program = /usr/bin/passwd %u
   passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
   pam password change = yes
   map to guest = bad user
   usershare allow guests = yes


[Public]
   comment = Public
   path = /opt
   public = yes
   writable = yes
   create mask = 0775


[Admin]
   comment = Admin folder
   path = /etc
[FONT=&amp]public =[/FONT][FONT=&amp]no[/FONT]

I can access the "Public" share without issue, but when I try to access the "Admin" share using the SAME AD credentials that I use to SSH to the server I get the following error in my samba logfile..

> [2017/07/29 08:37:11.509576,  0] ../source3/auth/auth_domain.c:121(connect_to_domain_password_server)
  connect_to_domain_password_server: unable to open the domain client session to machine DC.EXAMPLE.COM. Error was : NT_STATUS_CANT_ACCESS_DOMAIN_INFO.
[2017/07/29 08:37:11.520267,  0] ../source3/auth/auth_domain.c:121(connect_to_domain_password_server)
  connect_to_domain_password_server: unable to open the domain client session to machine DC.EXAMPLE.COM. Error was : NT_STATUS_CANT_ACCESS_DOMAIN_INFO.
[2017/07/29 08:37:11.528663,  0] ../source3/auth/auth_domain.c:121(connect_to_domain_password_server)
  connect_to_domain_password_server: unable to open the domain client session to machine DC.EXAMPLE.COM. Error was : NT_STATUS_CANT_ACCESS_DOMAIN_INFO.
[2017/07/29 08:37:11.528817,  0] ../source3/auth/auth_domain.c:184(domain_client_validate)
domain_client_validate: Domain password server not available.

Has anyone managed to get this kind of setup to work?

Thanks

---

