---
title: "Default login with sudo -i"
date: 2007-09-14
forum: General Help
---

### Post by l_b on 2007-09-14
Hi all,

My default user can sudo -i to become "root". But I have this backupuser that should be default root when it logs in. How can I accomplish this? I looked at the /etc/sudoers file, but I don't know how I can make this happen.

Thanks in advance!

---

### Post by raijinsetsu on 2007-09-14
I think what you're saying is: you have a "backupuser" that you want to be synonymous with "root"?
If that's the case, it goes against the standard. If you need to access root (say you were locked out) then you just need to boot into recovery mode.
If you REALLY want to make backupuser and root synonymous (which can be very bad), then, I believe, all you have to do is add backupuser to the root group. "sudo gpasswd -a backupuser root"
I don't suggest this.

---

### Post by mcduck on 2007-09-14
If you want the user to be root, just use the root user instead of creating another user and trying to make it root.

Anyway, this far I haven't found a single thing that would require you to be root. Having a root user just makes your life harder than it should be.

---

### Post by l_b on 2007-09-14
I tried it with my own account:

```
root:x:0:leon
daemon:x:1:
bin:x:2:
sys:x:3:
adm:x:4:leon
```

But then:
```

$ ls -al /home/bbsdevries/cgi-bin/
ls: /home/bbsdevries/cgi-bin/: Permission denied

```

That doesn't work... I want a backupuser that can backup all the stuff on the server with a rsync command.

---

### Post by anaconda on 2007-09-14
yep, and to enable root just give root a password with:

sudo passwd root

and then to enable graphical root logins:
go to system>Administration>Login window and there under the security tab select the allow graphical root login.. or similar..

---

### Post by raijinsetsu on 2007-09-14
Giving a password to the root user goes against the standard ubuntu security model. It really should only be done by system administrators. Unless you're very familiar with Linux, you should never be "root". You definitely should never have a root GUI session.
But, it is your system, so do what you like.

As for running rsync, you just need to add a sudoers entry for running rsync as root for your backupuser.
I think there is a GUI sudoers editor... not sure though.

---

### Post by l_b on 2007-09-14
> **raijinsetsu said:**
> As for running rsync, you just need to add a sudoers entry for running rsync as root for your backupuser.
I think there is a GUI sudoers editor... not sure though.

Ah, thanks. And how would one do that? What should that entry look like?

To make things clearer:

I have one machine, let's call it backupmachine with backupuser on it. It rsyncs to "servermachine" to rsync all stuff of that server. So I have to edit the sudoers-file on servermachine.

---

### Post by raijinsetsu on 2007-09-14
"backupuser = (root) /usr/bin/rsync"
That should work. Also, the backupuser will only be able to run rsync as root.
Type "which rsync" to get the correct path for rsync.
Here's a link for a [sudoers manual]("http://www.gratisoft.us/sudo/man/sudoers.html#runas_spec")

---

