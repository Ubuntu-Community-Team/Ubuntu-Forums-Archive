---
title: "Permissions issue"
date: 2021-08-10
forum: General Help
---

### Post by andre46 on 2021-08-10
I am migrating all my Docker containers from 1 VM to a different one. Both VMs are Ubuntu 19.10. All the data for each of my docker containers was being saved to a shared network drive in /mnt/. Many of these files are owned by root. I have migrated my containers in /var/lib/docker, but they all fail to launch. I'm realizing now that the issue is actually the data on the shared drive in /mnt/. The drive is shared via NFS to both VMs from an OpenMediaVault VM. The root user on new new VM is not able to access the files created by the root user of the other device. The root user for both device had the same password.

Is anybody able to explain what I can do to remedy this?

---

### Post by TheFu on 2021-08-11
Support for 19.10 ended over a year ago.  Get onto a supported release, please.

---

### Post by andre46 on 2021-08-11
This has nothing to do with the version of Ubuntu, and we both know it. I had issues previously trying to upgrade, and I just haven't tried again recently. This task is part of project that will hopefully allow me to upgrade Ubuntu on the VM.

Luckily for me, I resolved this on my own. I still wish I understood what was wrong, as I probably didn't resolve it the most efficient way

```
sudo rsync -ravhp root@myIP:/path/to/data/ /path/to/data_new
```

This essentially gave me root on both devices via SSH connection and I just made a clone of the data on the same shared drive. I got a ton of errors saying there were permission errors, however it appears that everything was actually more or less successful and my docker containers all now work. The only issue I had is one folder that is owned by a user that doesn't exist on the new server.

---

### Post by TheFu on 2021-08-11
Well, I don't trust docker to be secure and don't really use it for anything serious. 

I do know that NFS doesn't translate root access to NFS clients. That's part of the NFS spec. There is an option to allow root on an nfs client to behave with root on the nfs-server storage, but that's never recommended. The option is controlled in the /etc/exports and documented in that section 5 manpage.

Helping with unsupported releases here dilutes volunteer efforts to support people running actively supported releases.  That's the normal line in these forums ... or should someone struggle to help people running 10.04 or 8.04 or 6.06?
18.04, 20.04, and 21.04 are supported.
16.04 and 14.04 are under paid support options now, also called ESM.  [https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)

---

