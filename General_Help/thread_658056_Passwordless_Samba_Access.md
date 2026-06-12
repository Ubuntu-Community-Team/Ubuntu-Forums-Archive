---
title: "Passwordless Samba Access"
date: 2008-01-04
forum: General Help
---

### Post by ignus on 2008-01-04
hi everyone

i have a strange question: is it possible to set up samba so that the other (windows) pcs in my house can access the shares (read only) on my ubuntu box without being prompted for a password?

basically im not sure how to configure samba.

at the moment (for some reason that escapes me) the xbox in my sitting room which is running XBoXMediaCenter can access the shares, browse and play content over the network without being asked for a password. i presume this is because XBMC uses samba but thats just a guess. 

any help would be greatly appreciated!! 

~/ignus

---

### Post by Nonno Bassotto on 2008-01-04
Disclaimer: I hope you understand the security issue in sharing your files without password. That said, if you want to do it, here are the instructions.

Edit the file /etc/samba/smb.conf and put the line
```

security=share

```
in the Administration section, rather than
```

security=user

```
Then for each shared folder add the line
```

guest ok = yes

```
making it look like this example
```

[MyFolder]
path = /home/MyName/MyFolder
guest ok = yes
comment = This is the folder I'm sharing
available = yes
public = yes
writable = no
browsable = yes

```

Save the file, restart Samba with the command
```

sudo /etc/init.d/samba restart

```
and you're done.

---

### Post by Nonno Bassotto on 2008-01-04
I should mention other typical issues that you may find when sharing folders.

1) Be sure that the firewall is not blocking the access to your ubuntu machine
2) Windows PCs can only see other computers on the same domain. So set the same domain name in all your computers. For Ubuntu, this is under System->Administration->Shared Folders (where else?). In windows XP this is under Computer name (it took me a week to find out this!)

---

### Post by ignus on 2008-01-04
this is awesome!!!!! thanks so much! i have been trying to get this working for so long. fantastic. thanks again!!

~/ignus

---

