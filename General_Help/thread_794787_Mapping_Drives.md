---
title: "Mapping Drives"
date: 2008-05-14
forum: General Help
---

### Post by JHSheridan11 on 2008-05-14
I use Kubuntu 8.04 here at home, and I have a Unix account in the lab at my college. I know can get SSH access, but I need to transfer files as well sometimes. Is there any way to map a Unix drive to my Unix computer? Everything I find is Windows to Unix.

Thanks,
John

---

### Post by JHSheridan11 on 2008-05-15
bump...

---

### Post by prshah on 2008-05-15
> **JHSheridan11 said:**
> I use Kubuntu 8.04 here at home, and I have a Unix account in the lab at my college. I know can get SSH access, but I need to transfer files as well sometimes. Is there any way to map a Unix drive to my Unix computer? Everything I find is Windows to Unix.


scp (Secure copy) will do the job fine for you: Eg:
```

scp -P 22 username@ipaddress:~/somefiles* ~

```
will copy "somefiles*" using SSH protocol on "port 22" from your University "username" and university machine "ipaddress"'s "home" folder to your current machine's home folder.

To send the files back, you can reverse the order:
```

scp -P 22 somefiles* username@ipaddress:~

```

Not that port 22 is the default for SSH/scp, but just including the switch if you have changed the port for SSH.

"man scp" is also very detailed and helpful.

To mount a remote unix folder to a local directory, you need to use NFS; don't know how to set it up, so can't give you more details there.

---

