---
title: "smbpasswd file missing"
date: 2005-05-28
forum: General Help
---

### Post by Sandomaphone on 2005-05-28
I have NO idea why, but whenever I try to add a SAMBA user...

#>smbpasswd -a user

It 'looks' like it works, but it doesn't append the encrypted password to /etc/samba/smbpasswd.  Not only that, but the smbpasswd file isn;t even created when the first user is created, like it's meant to.

...weirdness.  Any Ideas.  This is really crucial as it is preventing me from setting up a domain.

---

### Post by f.prisson on 2005-05-28
I had a quick look in google and found that you have to create an empty smbpasswd file with ```
sudo touch /etc/samba/smbpasswd
``` but I didn't try it. I also found this about th -a switch:> You can use the smbpasswd program with the -a option to automatically add any user that currently has a standard Unix system account on the server

---

### Post by masi on 2005-06-19
try:
#> smbpasswd -c '/etc/samba/smbpasswd' -a <username>

don't forget to insert at '/etc/samba/smb.conf' -> [global]:
"username map = /etc/samba/smbpasswd'

maybe you have to create the '/etc/samba/smbusers'-file, too.

on succsess 'smbpasswd' replies:
"Added user <username>"

good luck,
masi

---

