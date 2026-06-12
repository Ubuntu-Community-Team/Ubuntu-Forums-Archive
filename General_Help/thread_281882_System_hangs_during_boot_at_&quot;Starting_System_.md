---
title: "System hangs during boot at &quot;Starting System Log...&quot;"
date: 2006-10-21
forum: General Help
---

### Post by jeff_ on 2006-10-21
For some reason when I try and boot dapper 6.06 it stops at "Starting System Log...". After a little while it exits the graphical boot up and just waits in the text mode. Recovery mode works fine, but I don't know what to do there to fix the problem. Any ideas? I've seen the same problem posted on these forums, but no one ever responded. Thanks, Jeff

---

### Post by jeff_ on 2006-10-22
Is there a way I can reinstall the core operating system? Might that fix the problem?

---

### Post by asimonelli on 2008-03-31
I ended up with the same problem.  I was using Winbind and Samba on a Windows NT Domain.  The following is what I ended up doing to get it to work again:

In Recovery Mode, I removed sysklogd from start up
[INDENT]```
root#> update-rc.d -f sysklogd remove
```[/INDENT]
I also removed Apache2
[INDENT]```
root#> update-rc.d -f apache2 remove
```[/INDENT]
I removed the winbind entries I added to /etc/nsswitch.conf.

I also made sure that /etc/hostname was correct.

After these changes, I rebooted and everything started to work again.  I added the sysklogd and apache2  back to startup
[INDENT]```
sudo update-rc.d sysklogd defaults
```[/INDENT]
[INDENT]```
sudo update-rc.d apache2 defaults
```[/INDENT]

I think it had to do with my Linux server not being joined to the domain that caused the problems but I'm not really sure.  I can't explain exactly why it worked, except for the following post that helped me figure it out:

[http://ubuntuforums.org/showthread.php?t=140318]("http://ubuntuforums.org/showthread.php?t=140318")

especially the part about LDAP at the end.

---

