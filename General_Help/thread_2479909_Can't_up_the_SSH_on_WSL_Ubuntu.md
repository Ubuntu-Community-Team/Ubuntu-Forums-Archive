---
title: "Can't up the SSH on WSL Ubuntu"
date: 2022-10-12
forum: General Help
---

### Post by alex68md on 2022-10-12
I have windows 10 home w/o hypervisor and wsl ubuntu. on ubuntu was configured ssh server (sudo service ssh start).

After that I decided to install k9s from snap store. but ubuntu doesnt have snap store to resolve this I have used this steps
```

    sudo apt-get update && sudo apt-get install -yqq daemonize dbus-user-session fontconfig
    sudo daemonize /usr/bin/unshare --fork --pid --mount-proc /lib/systemd/systemd --system-unit=basic.target
    exec sudo nsenter -t $(pidof systemd) -a su - $LOGNAME
```

[https://github.com/microsoft/WSL/issues/5126#issuecomment-653715201](https://github.com/microsoft/WSL/issues/5126#issuecomment-653715201)
but unsuccessful  (some error about hypervisor)

but now when I try to run ssh server and I get error

    ```
Failed to start ssh.service: transport endpoint is not connected.
```
please help rollback ubuntu state

---

### Post by TheFu on 2022-10-12
In Linux, we have these things called "backups". That is how we rollback to a prior setup.  Backups need to be made BEFORE they are needed.  

There are some setups that will use specific file systems and create backups every hour or day or week or as requested, but I've never heard of those on WSL.  Back-in-time is one tool for this.

If you want the real Linux desktop experience, load a full Linux desktop into a virtual machine. 

Everything else in your post is extremely specific to WSL, not core Ubuntu stuff, so I cannot help. Sorry.  That installation command is nothing I would have connected with ssh and I've been using, installing, configuring and training people on ssh for over 2 decades.

Thanks for clearly saying WSL.  That information saved me and will likely save others lots of time.

---

### Post by alex68md on 2022-10-13
I know what is backup
I mean rollback settings in linux or make new setup

---

### Post by TheFu on 2022-10-13
> **alex68md said:**
> I know what is backup
I mean rollback settings in linux or make new setup

The method to rollback settings is to selectively restore from a backup ... unless you have previously used a volume manager and taken a "snapshot", which I doubt is possible on WSL.  [https://www.reddit.com/r/bashonubuntuonwindows/comments/qi0fv6/is_there_any_way_to_snapshot_a_wsl_instance/](https://www.reddit.com/r/bashonubuntuonwindows/comments/qi0fv6/is_there_any_way_to_snapshot_a_wsl_instance/) seems to confirm this, if we can believe redit "experts".

Some virtual machines have the ability to create a snapshot from the VM management tool, but that is dependent on the underlying storage model used by the VM manager.  For example qcow2 [https://www.admin-magazine.com/Archive/2014/20/Live-snapshots-with-Virtual-Machine-Manager](https://www.admin-magazine.com/Archive/2014/20/Live-snapshots-with-Virtual-Machine-Manager) supports snapshots, as does VMDK [https://kb.vmware.com/s/article/2007069](https://kb.vmware.com/s/article/2007069) and VDI [https://www.virtualbox.org/manual/ch01.html#snapshots](https://www.virtualbox.org/manual/ch01.html#snapshots) storage.  I use LVM storage for my VMs, which also supports snapshots.

If you want to make a new setup, that's called a fresh install.  Perhaps MSFT makes it easy?  IDK.  WSL isn't a normal Linux.  

Running Linux inside a virtual machine is like running it on real hardware for the most part. If you did that, there are all sorts of techniques.  

I did see that WSL has export and import tools.  Appears they use tar, which really shouldn't be used for backups since around 1999. There are so many better options.  However, the key, required, aspect for all backups on Unix systems is to retain not just the contents of the files, but the metadata tied to the files ... the owner, group, ACLs, permissions, and xattrs.  Without those, a restore will fail.  For most Linux backup tools, that means that storing system-level backups on NTFS is a failure.  For personal files, it is probably fine, except for ~/.ssh/ where permissions are absolutely critical or the ssh programs will refuse to work at all.

---

