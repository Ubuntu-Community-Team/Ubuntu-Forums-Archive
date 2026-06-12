---
title: "tranmission + fstab autmount drive + permissions do not work but crontab -e works"
date: 2019-11-06
forum: General Help
---

### Post by MariosFFX on 2019-11-06
Hello.
I have configured my machine to auto mount a drive at @reboot with:
```
 crontab -e 
@reboot sleep 5 && sudo mount /dev/sda1 /home/user/FTP
```

and transmission has umask 18 and it downloads at:
/home/user/FTP/Downloads
and it's working fine.

However if auto mount my drive with:
```
/etc/fstab
UUID=DC22AE7922AE5872       /home/user/FTP     ntfs-3g   defaults,nls=utf8,umask=000,dmask=027,fmask=137,uid=1000,gid=1000,windows_names 0 0

```

When I mount a drive with fstab, transmission isn't working, I have even tried chown Downloads folder to debian-transmission:debian-transmission also chmod files/folders and even adding my username to usergroup debian-transmission

---

### Post by uRock on 2019-11-06
Are you using Ubuntu or Debian? Which release?

---

### Post by TheFu on 2019-11-06
NTFS doesn't support chmod or chown.  All the permissions are set at mount time.  Check the umask=000,dmask=027,fmask=137, options.  Something looks wrong there.  Is umask even a valid option?  While you are at it, probably want some options to help performance.
```
windows_names,nosuid,noatime,async,big_writes
```

I don't know anything about transmission and I hope you aren't running a plain FTP server.  sftp replaced plain FTP around 2002.

A umask of 18 isn't valid, BTW.

To be clear, automount and using the fstab are completely different methods.  Check out **autofs** (which handles mounting outside fstab file configs), if you really want to use automounter.

---

