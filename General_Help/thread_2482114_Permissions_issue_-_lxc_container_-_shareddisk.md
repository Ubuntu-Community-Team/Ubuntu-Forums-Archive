---
title: "Permissions issue - lxc container - shareddisk"
date: 2022-12-20
forum: General Help
---

### Post by veedub67 on 2022-12-20
Hello,

I'm using Ubuntu Jammy.

I have been using an LXC container to host a Borg repository without issue for some months.

However, recently the access to the repository broke (I don't know what happened / changed to cause this); but now the permissions to some of the files in the repository is broken.

The repository resides in a shared directory in
```
[COLOR=#434343][FONT=Consolas]/media/zen/REAR-000/Repository[/FONT][/COLOR]
```

For some reason the Borg config file is no longer accessible

I have tried the following commands to resolve (from the container)
```
[COLOR=#434343][FONT=Consolas]sudo [/FONT][/COLOR][FONT=Consolas]chmod[/FONT][COLOR=#434343][FONT=Consolas] -R 755 /media/zen/REAR-000/Repository/
[/FONT][/COLOR][COLOR=#434343][FONT=Consolas]chmod: changing permissions of [/FONT][/COLOR][FONT=Consolas]'/media/zen/REAR-000/Repository/nonce'[/FONT][COLOR=#434343][FONT=Consolas]: Operation not permitted[/FONT] 
[/COLOR][FONT=Consolas]chmod[/FONT][COLOR=#434343][FONT=Consolas]: changing permissions of [/FONT][/COLOR][FONT=Consolas]'/media/zen/REAR-000/Repository/config'[/FONT][COLOR=#434343][FONT=Consolas]: Operation not permitted[/FONT][/COLOR][COLOR=#434343][FONT=Consolas]
[/FONT][/COLOR]
```

I then tried
```
[COLOR=#434343][FONT=Consolas]sudo [/FONT][/COLOR][FONT=Consolas]chown $USER[/FONT][COLOR=#434343][FONT=Consolas]: /media/zen/REAR-000/Repository/config
[/FONT][/COLOR][FONT=Consolas]chown[/FONT][COLOR=#434343][FONT=Consolas]: changing ownership of [/FONT][/COLOR][FONT=Consolas]'/media/zen/REAR-000/Repository/config'[/FONT][COLOR=#434343][FONT=Consolas]: Operation not permitted[/FONT][/COLOR]
```

Thanks
VW

---

### Post by TheFu on 2022-12-20
The target file system doesn't appear to be a native Linux file system.  Foreign file systems don't support permissions and Linux provides mount options to fake it, but the owner, group and permissions will all be the same for all files there.

I don't know how Borg stores backups and retains owner, group, permissions, ACLs, xattrs, but without all of those, a backup is next to useless.

---

### Post by veedub67 on 2022-12-21
> **TheFu said:**
> The target file system doesn't appear to be a native Linux file system.  Foreign file systems don't support permissions and Linux provides mount options to fake it, but the owner, group and permissions will all be the same for all files there.

I don't know how Borg stores backups and retains owner, group, permissions, ACLs, xattrs, but without all of those, a backup is next to useless.

@TheFu

The target file system is ext3.

This has been working for sometime, but recently something happened, and I need to resolve the access to the files that are affected if I'm going to be able to continue to use this repository.

---

### Post by veedub67 on 2022-12-21
I think there might be an issue with the UID/GID mapping.

---

### Post by TheFu on 2022-12-21
> **veedub67 said:**
> I think there might be an issue with the UID/GID mapping.

And what data might be useful to determine that?  My LXD containers are all self-contained, so there aren't any external mappings.  I.e. I don't map in host storage. 

I did as a test, months ago, to see how it worked should I need a container to be a backup server. This was after I'd setup NFS for the same purpose. NFS had some ugly requirements that drastically reduced container security, so that didn't last long.   I can probably find some notes about what I did to make that happen.
```

# =============== LXD Storage Devices =============
Https://askubuntu.com/questions/691039/adding-a-shared-host-directory-to-an-lxc-lxd-container
 Mount the host folder /var/www as /var/test in the container.
 $ lxc config device add mycontainer vartest disk source=/var/www path=/var/test
# back-2004 example:
$ lxc config device add back-2004 backup_rom disk \
        source=/Data/1.5T/Backups  \
        path=/Backups
# it not only presents the file system directly, but it is mounted
# without any /etc/fstab changes. However, if root permissions are necessary, 
# running in a privileged (real root) container is required. (see below)
# Without privileged, root is mapped to 'nobody:nobody', as expected.

```
Most backup tools don't work well without root, so that's sorta a problem if the container is supposed to be secure.  This is why NFS and firewalls also don't work well in Linux containers.  Best to use a full VM instead.

Hope that is helpful, but I doubt it actually is.

I'd also check the HDD for SMART errors. That could really make for a bad week.

---

