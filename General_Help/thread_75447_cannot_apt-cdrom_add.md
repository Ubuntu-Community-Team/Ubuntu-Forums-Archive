---
title: "cannot apt-cdrom add"
date: 2005-10-13
forum: General Help
---

### Post by pksings on 2005-10-13
I searched and could not find and answer to this.


[email]root@dell-pk:~/.ssh[/email] # apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [7800775d2ce00e630ff4fbae2bcd6551-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes and 1 signatures
Found label 'Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)'
This disc is called:
'Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)'
Copying package lists...gpgv: Signature made Wed Oct 12 09:25:36 2005 PDT using DSA key ID FBB75451gpgv: Can't check signature: public key not found
E: Sub-process gpgv returned an error code (2)
W: Signature verification failed for: /cdrom/dists/breezy/Release.gpg

[email]root@dell-pk:~/.ssh[/email] # apt-key list
/etc/apt/trusted.gpg
--------------------
pub  1024D/437D05B5 2004-09-12 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub  2048g/79164387 2004-09-12

---

