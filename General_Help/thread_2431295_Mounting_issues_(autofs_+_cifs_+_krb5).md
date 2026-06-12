---
title: "Mounting issues (autofs + cifs + krb5)"
date: 2019-11-14
forum: General Help
---

### Post by kveldulfur on 2019-11-14
This issue is occuring on ubuntu 18.04.3.


In an attempt to set up an SSO autofs mounting system for a cifs share (truenas) in my office using krb5, I started running into some very strange issues, no matter what setup and modifications I did to the auto.smb file I could never get it to mount, extensive digging gave me a unhelpful error in the autofs journal:
"mount error(2): No such file or directory
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)"
This was no issue on a second test machine running debian 9, everything just worked as expected there.


After a lot of testing I have discovered some facts about the problem:
After running the autofs service journalctl states:
```
...
nóv 12 14:08:41 kv-ubu-test automount[23332]: mount_mount: mount(generic): calling mount -t cifs -o multiuser,cruid=436214317,sec=krb5 //TRUENAS/vinnugogn /vi/truenas/vinnugogn
nóv 12 14:08:41 kv-ubu-test automount[23332]: >> mount error(2): No such file or directory
nóv 12 14:08:41 kv-ubu-test automount[23332]: >> Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```
*note: the auto.smb script exports KRB5CCNAME, confirmed by having auto.smb write it's current env to a file (unless autofs is somehow losing said variable after running auto.smb, but before attempting to mount)


But manually running as root shows the same mount call, no error, and the mount works properly:
```
root@kv-ubu-test:~# export KRB5CCNAME=FILE:/tmp/krb5cc_436214317_X8209T #This is just a hack to get the variable in, the auto.smb script should/will perform this action
root@kv-ubu-test:~# automount -f -vvv
...
mount_mount: mount(generic): calling mount -t cifs -o multiuser,cruid=436214317,sec=krb5 //TRUENAS/vinnugogn /vi/truenas/vinnugogn
mount_mount: mount(generic): mounted //TRUENAS/vinnugogn type cifs on /vi/truenas/vinnugogn
```


Some info: we have a dedicated inhouse DNS system that works fine.
dig on the hostname and FQDN return the same, correct, IP. 
sssd.conf and krb5.conf are identical between the debian and ubuntu machines.
kinit succeeds in fetching a key.
smb.conf only differs in hostname.

I am at a complete loss, strace and ltrace on the mount command have given me nothing helpful to work with. At this point I am wondering if there is a bug in the cifs-utils package or autofs?

If anyone has  any info or advice on what I can try next it would be greatly appriciated, alternatives to autofs are 100% acceptable, but I have not found any yet that seem promising (systemd mount comes to mind, but I can't find anything about how to make it play nice with krb5)



EDIT:
If anyone has this same issue, the solution seems to be changing the name of the krb5 credentials cache file, by adding this line to /etc/krb.conf under the [libdefaults] section

default_ccache_name = FILE:/tmp/krb5cc_%{uid}

Then suddenly autofs starts to play nice.

---

