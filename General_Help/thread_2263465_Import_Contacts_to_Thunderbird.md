---
title: "Import Contacts to Thunderbird"
date: 2015-02-01
forum: General Help
---

### Post by rbengr on 2015-02-01
Hi,

I would like to import my Contacts from OS X to Thunderbird.  I have saved the file Contacts.vcf to my OS X desktop.  When I go to the import area of Thumderbird, it asks me to select a file to import.  But it only allows a selection from within Ubuntu.  This doesn't make sense to me because the file is not imported yet.  I guess I need to get the file into Ubuntu somehow?

Thanks

---

### Post by TheFu on 2015-02-01
Well - have you moved the vcf file to the ubuntu machine?
I'm seeing options to import .vcf, LDIF, .tab, .csv, and .txt files into the current thunderbird here.

---

### Post by rbengr on 2015-02-01
No, the file is still on the OS X desktop.  I don't know how to get it into Ubuntu.

---

### Post by TheFu on 2015-02-01
> **rbengr said:**
> No, the file is still on the OS X desktop.  I don't know how to get it into Ubuntu.

Since these are both Unix systems, use sftp.  One of them must have the ssh server running, then the other system can use that to pull/push the file as needed.
[https://www.digitalocean.com/community/tutorials/how-to-use-sftp-to-securely-transfer-files-with-a-remote-server](https://www.digitalocean.com/community/tutorials/how-to-use-sftp-to-securely-transfer-files-with-a-remote-server)

If you make ssh available over the internet, definitely secure it: [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures)

ssh is so powerful, it is the only port you need to have open to support
[LIST]
[*]    secure remote access to files via sftp
[*]    secure remote filesystem access via sshfs
[*]    secure remote CLI/shell access to systems with plain ssh
[*]    secure remote desktops via x2go/freenx
[*]    secure remote file replication with rsync (ssh is the default rsync protocol)
[*]    secure port forwarding of selected ports
[*]    secure remote editing with vim/gvim and other editors
[*]    pseudo-VPN with sshuttle <— this may be helpful.
[/LIST]

ssh really is the toolbox for remote connectivity.

---

### Post by ajgreeny on 2015-02-01
Or what about a flash drive, or even send it to yourself by email and pick it up on Ubuntu?

It can't be that difficult to move a file surely!

---

### Post by rbengr on 2015-02-01
Yes.  Isent myself an email.  It worked.  Thanks

---

