---
title: "AAD Logon from Ubuntu 23"
date: 2023-12-21
forum: General Help
---

### Post by schiffne on 2023-12-21
Hi everyone,

maybe someone is able to help me. I am trying to configure Azure Active Directory logon with Ubuntu. The tutorials are normally straight forward, like this one: [https://blog.nevinpjohn.in/posts/AAD-auth-Ubuntu-Desktop-23.04/](https://blog.nevinpjohn.in/posts/AAD-auth-Ubuntu-Desktop-23.04/) but I am struggling with the APP-ID and the secret. The Conf file contains only the Tenant-ID, App-ID but where does the secret need to get written to?
Thanks for your help
Marco__PRESENT

---

### Post by ActionParsnip on 2023-12-21
From the page you linked, it seems that the app_id line uses the client secret value
[https://blog.nevinpjohn.in/posts/AAD-auth-Ubuntu-Desktop-23.04/#configuring-ubuntu](https://blog.nevinpjohn.in/posts/AAD-auth-Ubuntu-Desktop-23.04/#configuring-ubuntu)

---

### Post by ottfro on 2024-02-23
[https://github.com/ubuntu/aad-auth](https://github.com/ubuntu/aad-auth)
[https://ubuntu.com/blog/azure-ad-authentication-comes-to-ubuntu-desktop-23-04](https://ubuntu.com/blog/azure-ad-authentication-comes-to-ubuntu-desktop-23-04)

we are on 23.10 using azure vm 
[COLOR=#646464][FONT=az_ea_font]Image offer [/FONT][/COLOR][COLOR=#292827][FONT=az_ea_font]0001-com-ubuntu-server-mantic[/FONT][/COLOR][COLOR=#646464][FONT=az_ea_font]
[/FONT][/COLOR]



In 23.10 there are some problems

[LIST]
[*]**the aad-cli**[COLOR=#1F2328][FONT=-apple-system]** command line tool  is missing**
[/FONT][/COLOR]
[*][COLOR=#1F2328][FONT=-apple-system]**only the first user can login, the next users trying to login are failed with "**[/FONT][/COLOR]**user unknown" and "invalid user"**
[/LIST]
[COLOR=#1F2328][FONT=-apple-system]

[/FONT][/COLOR]2024-02-23T08:59:32.028940+00:00 Ubuntu sshd[9230]: pam_unix(sshd:auth): check pass; user unknown
2024-02-23T08:59:32.029238+00:00 Ubuntu sshd[9230]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=147.161.189.82
2024-02-23T08:59:34.724554+00:00 Ubuntu sshd[9230]: Failed password for invalid user [email]userid@company.com[/email] from 147.161.189.82 port 25980 ssh2



I think the secret is not needed for the app id field, just app id is needed.

---

