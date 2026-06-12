---
title: "ubuntu 20.04 LTS server - SAMBA DOMAIN CONTROLLER"
date: 2021-10-22
forum: General Help
---

### Post by peter99-theonly on 2021-10-22
Hi.

I followed the steps in the original documentation:

[https://ubuntu.com/server/docs/samba-domain-controller](https://ubuntu.com/server/docs/samba-domain-controller)

An this point:
"[COLOR=#111111][FONT=Ubuntu]Also, rights need to be explicitly provided to the [/FONT][/COLOR]*Domain Admins*[COLOR=#111111][FONT=Ubuntu] group to allow the [/FONT][/COLOR]*add machine script*[COLOR=#111111][FONT=Ubuntu] (and other admin functions) to work. This is achieved by executing:"
[/FONT][/COLOR]net rpc rights grant -U sysadmin "EXAMPLE\Domain Admins" SeMachineAccountPrivilege \
SePrintOperatorPrivilege SeAddUsersPrivilege SeDiskOperatorPrivilege \
SeRemoteShutdownPrivilege[COLOR=#111111][FONT=Ubuntu]I get an error message, and i dont know what is the problem.
The message is:

[/FONT][/COLOR]failed to grant privileges for EXAMPLE\Domain Admins (nt_status_no_such_user)[COLOR=#111111][FONT=Ubuntu]

What is the problem? 

[/FONT][/COLOR]

---

### Post by rsteinmetz70112 on 2021-10-25
Run testparm it may give you a clue, if not post the results for the [Global] section. 
I've never had to run a command like that to get it to work.

The link you posted sets up an NT4 style domain and may require changes to the Windows computers.
There are plans for Samba to remove that option and require and AD style network.

I'm not even sure if Windows 11 will join an NT4 style domain.

---

