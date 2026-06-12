---
title: "Problems with Target Folder in DFS under CIFS"
date: 2015-05-13
forum: General Help
---

### Post by dave2ym on 2015-05-13
Hello,

I have the following problem:
There is a DFS within our Active Directory infrastructure and within that NameSpace there are FolderTarget as Follows:
Namespace: mydomain.local\Public
Target Folder: DFSTest which points to \\some_windows_server.local\DFSTest$
Under a normal windows client that folder will be accessed as follows: \\mydomain.local\public\DFSTest

Under Ubuntu I am mounting it like this:
mount -t cifs //mydomain.local/public /mnt/a --verbose -o username=domainuser,domain=mydomain.local,sec=ntlmssp
And it mounts but then I get this:

vms mnt # ls /mnt/a/
DFSTest
vms mnt # ls /mnt/a/DFSTest/
ls: cannot access /mnt/a/DFSTest/: Input/output error

In dmesg I get this: [ 5729.826119] CIFS VFS: cifs_mount failed w/return code = -5

Remember that DFSTest (that folder above) is a target folder from DFS Management defined.

I tried it with Kerberos and I get the same result. No matter what kind of sec I specify.

Do you have any ideas?

Thank you

---

