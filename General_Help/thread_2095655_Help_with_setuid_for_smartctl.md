---
title: "Help with setuid for smartctl"
date: 2012-12-17
forum: General Help
---

### Post by MadsRC on 2012-12-17
I recently tried to fix a problem with phpsysinfo, but it failed to work. The fix was to run chmod 4775 /usr/sbin/smartctl which would allow smartctl to be run as normal user. As it didn't fix the problem with phpsysinfo I'd like to change it back to the default (as in, it needs root).

What is the command to reset itback to default setuid? I'd rather not reinstall smartmontools...

I must admit, the setuid is some of the things I haven't read up on much.

---

### Post by sisco311 on 2012-12-17
The file is owned by the user root and the group root and has read/write/execute for the owner, read/execute for the group and others, the SUID, SGID and the sticky bits aren't set:

```

chown root:root /usr/sbin/smartctl
chmod 0755 /usr/sbin/smartctl

```

You can read more about Unix/Linux file permissions here: [http://content.hccfl.edu/pollock/aunix1/filepermissions.htm](http://content.hccfl.edu/pollock/aunix1/filepermissions.htm)

---

### Post by MadsRC on 2012-12-17
Thank you, will try.

I am aware of basic file permissions like owner and group, it was just the setuid bit that ad me confused... Had a feeling 0755 would do it, but wasn't clear that it was the default.

Edit: chmod 0755 did the trick! Thanks!

---

