---
title: "/etc/sudoers configuration"
date: 2012-11-27
forum: General Help
---

### Post by Ed54_3 on 2012-11-27
I'm attempting to set up sudo to do two things:  Allow all network admins root access, and allow anyone on the system to mount and unmount network shares.  The closest I've gotten to this working is here:

```

#Allow all users to mount filesystems
ALL ALL=NOPASSWD: /bin/mount, /sbin/mount.cifs, /bin/umount

#Allow all admins sudo access
%DOMAIN\\admin_group ALL=(ALL) ALL

```

The problem with this is that the previously listed line works, while the second doesn't.  This happens when I switch their order as well.  I need both parts working for linux to be usable in my workplace.

---

### Post by Lars Noodén on 2012-11-27
You need to put the actual name of your group after the %

```

%admin ALL=NOPASSWD: /bin/mount, /sbin/mount.cifs, /bin/umount

```

Or are you trying to make this work with LDAP?

---

### Post by Ed54_3 on 2012-11-27
Yeah, using LDAP.  I don't have access to the server however, and it would be a hassle to get someone to add sudo LDAP support on the server.

---

### Post by rnerwein on 2012-11-28
> **Ed54_3 said:**
> I'm attempting to set up sudo to do two things:  Allow all network admins root access, and allow anyone on the system to mount and unmount network shares.  The closest I've gotten to this working is here:

```

#Allow all users to mount filesystems
ALL ALL=NOPASSWD: /bin/mount, /sbin/mount.cifs, /bin/umount

#Allow all admins sudo access
%DOMAIN\\admin_group ALL=(ALL) ALL

```The problem with this is that the previously listed line works, while the second doesn't.  This happens when I switch their order as well.  I need both parts working for linux to be usable in my workplace.
by the side - in my opinion is 
ALL ALL=NOPASSWD: /bin/mount, /sbin/mount.cifs, /bin/umount

 audacious - precarious - hazardous

---

### Post by Ed54_3 on 2012-11-29
You are right, this is perhaps insecure.  Is there a better way of achieving the same result?  This would also solve my problem since I would only need one line in /etc/sudoers then.

---

### Post by Ed54_3 on 2012-12-28
I solved this issue by using an alias as follows:

```


#Cmnd alias specification
Cmnd_Alias MOUNT_COMMANDS = /bin/mount, /sbin/mount.cifs, /bin/umount


#Allow all network admins root access
%DOMAIN\\admin_domain_group ALL=(ALL) ALL

#Allow all non-privileged users permission to mount filesystems
ALL ALL=NOPASSWD:MOUNT_COMMANDS


```

I'm not entirely sure why this worked, and my previous attempt didn't, but my issue is resolved.

---

