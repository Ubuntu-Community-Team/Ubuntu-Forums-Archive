---
title: "Problem with the 'for' command / Shutting down vmware guests"
date: 2007-10-30
forum: General Help
---

### Post by bryhhh on 2007-10-30
I'm having a problem trying to shutdown all the running vmware guests on my Ubuntu 7.10 server.

I'm using the following shell script

```
for vm in `vmware-cmd -l`;
do
vmware-cmd $vm stop soft;
done

```

This would work fine, if the paths of the virtual machines didn't contain spaces, unfortunately, they do.

```
root@somebox# vmware-cmd -l
/var/lib/vmware/Virtual Machines/Boogaloo/Windows Server 2003 Standard Edition.vmx

```

(Yeah, I know there is only one virtual machine at the moment, but this will increase in the near future)

I've tried wrapping $vm in quotes, but found that it doesn't make any difference, because the for command is treating spaces as delimiters, so the vmware-cmd is being run six times

i.e.
vmware-cmd /var/lib/vmware/Virtual stop soft
vmware-cmd Machines/Boogaloo/Windows stop soft
vmware-cmd Server stop soft
vmware-cmd 2003 stop soft
vmware-cmd Standard stop soft
vmware-cmd Edition.vmx stop soft

Does anyone know a clever way of getting round this problem (preferably one that doesn't involve having to remove the spaces from the path names :))

---

### Post by bryhhh on 2007-10-30
I've worked it out, so I'll post the answer here for the benefit of others that find this by searching the forum

```
vmware-cmd -l | xargs -i vmware-cmd {} stop soft
```

Easy! :)

---

