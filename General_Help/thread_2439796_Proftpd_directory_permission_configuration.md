---
title: "Proftpd directory permission configuration"
date: 2020-04-01
forum: General Help
---

### Post by vjp1978 on 2020-04-01
Hi all,

I need a big help to configuring my sftp directories permissions. I've about 20 users they are in about 10 groups, we have severals folders. I'd like to give different permissions to the different folders like this:

Everybody logs in to the ftp folder here we've folder1 folder2 folder3 etc. 

I tried this but it failed
<Global>
<Directory /ftp>
AllowOverwrite on
DeleteAbortedStores on
HiddenStores on
HideNoAccess on
AllowRetrieveRestart on
AllowStoreRestart on
<Limit ALL>
AllowGroup admins
DenyAll
</Limit>
<Limit READ>
AllowGroup users
</Limit>
<Limit DIRS>
AllowGroup users
</Limit>
</Directory>
</Global>

<Directory /mnt/ftp/folder1>
<Limit ALL>
AllowGroup admins
Allowgroup folder1_rw
</Limit>
<Limit DIRS>
AllowGroup folder1_ro
</Limit>
<Limit READ>
AllowGroup folder1_ro
</Limit>
</Directory>

The access of the ftp folde is working properly but the 2nd level folder is not. How could I do it?

---

