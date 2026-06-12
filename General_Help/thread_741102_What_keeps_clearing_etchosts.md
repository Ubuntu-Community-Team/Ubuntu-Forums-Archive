---
title: "What keeps clearing /etc/hosts"
date: 2008-03-31
forum: General Help
---

### Post by oraknabo on 2008-03-31
I use /etc/hosts to block ads and some sites I don't want to have access to while I'm working, but occasionally, some process goes through and deletes every line that isn't a comment. It seems to happen around the time I run updates, but I'd expect the updater to overwrite the file, not clean mine up.

Currently, I just keep a backup in the folder and restore it whenever this happens, but I have to do it almost once a week.

Anyone know what's going on?

---

### Post by warp99 on 2008-03-31
I don't know what the process may be, but you can change the permission on the file to read only then nothing will overwrite the file except root:

```
sudo chmod 644 hosts
```

then the permissions look like this:

```
my@machine:/etc$ ls -l hosts
-rw-r--r-- 1 root root 396 2008-03-09 20:22 hosts
```

if that doesn't work use '444' instead of '644'. That would make the file read only including root, but if your wanted to edit the file you would need to enable the write permissions before doing so.

---

### Post by oraknabo on 2008-03-31
I've always used sudo to edit the hosts file. Root has been the only user ever allowed to edit it. That's why this issue is so confusing.
```
-rw-r--r--  1 root root      2496 2008-03-30 21:25 hosts
```
It's also another reason I'm thinking the update is the only thing I authorize with gksudo that would be able to edit the file.

I'd be curious to see if anyone else has this happen. to test it, add a few
```
127.0.0.1 whatever.com
``` 
lines to your hosts file, comment a few out with "#" just to see if those stay, and then the next time you run a system upgrade and see if there are any changes in the uncommented lines.

Whether it is happening during the upgrade or not, it happens about once a week. For all I know it could be happening on startup, but I'm not authorizing it to do anything at root level then.

---

### Post by warp99 on 2008-04-01
You could make the file 'read only' and after a week check the log files for errors. If it's from an upgrade it would be in /var/apt/term.log.

---

### Post by pointone on 2008-04-01
For blocking sites, you could try "hosts.deny".

---

### Post by kerry_s on 2008-04-01
you should use " 0.0.0.0 " instead of " 127.0.0.1 " and blocking won't slow down nothing.

---

### Post by oraknabo on 2008-04-02
I don't really see any slowdown, but I'll try that.

While I understand that there are alternatives to the way I'm doing this, I'm still curious about finding out what's clearing out the non-commented lines from the hosts file. I'm just curious whether it's something unique to my setup or a standard Ubuntu thing most people just never notice.

---

### Post by kerry_s on 2008-04-02
> **oraknabo said:**
> I don't really see any slowdown, but I'll try that.

While I understand that there are alternatives to the way I'm doing this, I'm still curious about finding out what's clearing out the non-commented lines from the hosts file. I'm just curious whether it's something unique to my setup or a standard Ubuntu thing most people just never notice.

well, mine don't do that, but then again i'm not using ubuntu, i'm using debian.

---

