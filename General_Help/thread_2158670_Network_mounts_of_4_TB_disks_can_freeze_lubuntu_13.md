---
title: "Network mounts of 4 TB disks can freeze lubuntu 13.04"
date: 2013-06-30
forum: General Help
---

### Post by jimzz on 2013-06-30
I have a samba server which is sharing a 4 TB USB disk (the server is a tonidoplug2 running debian 6.0) .  I have 3 directories on the disk, all at the top level, which can be network mounted.  lets call them disk1/a, disk1/b, and disk1/c.  If I mount a single directory, say disk1/a (mount.cifs //tonidoplug2/disk1/a /mounta -o username=xxx,pass=yyy), on my lubuntu 13.04 desktop it succeeds and df -k reports a 4 TB mounted filesystem.  I have used this mount for a fair number of hours without errors.  However, if I then try to mount disk1/b, the mount command does not return and my lubuntu system develops odd behaviors.  For example, typing "df -k |grep mount" in another window also freezes that window.  I have had the entire OS freeze with loss of control, no cursor, etc., requiring a hard reboot.  And yes, I can mount any *one* of disk1/a, disk1/b, or disk1/c without problems.  Its when I do a second mount that the errors occur.  I believe this is completely replicable.

My guess is that having 2 or more 4 TB mount points is screwing up some system table, but I'm not current on linux internals.  I could work around this problem by adding a directory hierarchy (move my shares to disk1/d/a, disk1/d/b, disk1/d/c, and just mount disk1/d, so lubuntu needs only a single 4TB mount, but this would be awkward for my environment.  

I did a brief forum search - am not aware that this possible problem with multiple 4 TB mounts has been reported.  Given that I get system freezes, if this is truly an issue it likely deserves some attention.  Any help or insight is appreciated.

---

### Post by bab1 on 2013-06-30
> **jimzz said:**
> ...If I mount a single directory, say disk1/a (mount.cifs //tonidoplug2/disk1/a /mounta -o username=xxx,pass=yyy), on my lubuntu 13.04 desktop it succeeds and df -k reports a 4 TB mounted filesystem.  I have used this mount for a fair number of hours without errors.  However, if I then try to mount disk1/b, the mount command does not return and my lubuntu system develops odd behaviors.  For example, typing "df -k |grep mount" in another window also freezes that window.  I have had the entire OS freeze with loss of control, no cursor, etc., requiring a hard reboot.  And yes, I can mount any *one* of disk1/a, disk1/b, or disk1/c without problems.  Its when I do a second mount that the errors occur.  I believe this is completely replicable.

My guess is that having 2 or more 4 TB mount points is screwing up some system table, but I'm not current on linux internals.  I could work around this problem by adding a directory hierarchy (move my shares to disk1/d/a, disk1/d/b, disk1/d/c, and just mount disk1/d, so lubuntu needs only a single 4TB mount, but this would be awkward for my environment.  

What are the share names?  It does not like you are mounting the shares using the correct format or //SERVER_NAME/share_name.

Post the output of ```
smbtree -d3
```

---

### Post by jimzz on 2013-07-02
> **bab1 said:**
> What are the share names?  It does not like you are mounting the shares using the correct format or //SERVER_NAME/share_name.

Post the output of ```
smbtree -d3
```

thanks for the reply.  I don't see how I could have a problem with mount format or share names: note the symptom here is that I can mount any one of the 3 shares fine, but can't mount more than one without lubuntu freezing.  Also, I'm mounting these shares on several other computers, both linux and XP.

However, I'm going to suspend/retract my claim.  The other night I had my lubuntu system freeze 3 times in a row immediately when I tried to mount a second 4 TB share, so I was feeling pretty safe in posting: this morning, I was able to mount multiple shares without issue.  I'll try to get a better handle on what is going on here and will post a fresh thread if I can repeat the freezes and better isolate the issue.....

---

