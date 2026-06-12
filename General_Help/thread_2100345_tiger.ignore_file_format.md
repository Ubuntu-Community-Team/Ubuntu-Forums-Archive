---
title: "tiger.ignore file format"
date: 2013-01-01
forum: General Help
---

### Post by NickD-NLUG on 2013-01-01
Hi,

I'm running tiger to check my system and I frequently receive these notifications:

Subject: Cron <root@war>    test -x /usr/sbin/tigercron && { [ -r "$DEFAULT" ] && . "$DEFAULT" ; nice -n$NICETIGER /usr/sbin/tigercron -q ; }   
                                                                                                                                                
--CONFIG-- [con010c] Filesystem 'cgroup' used by 'cgroup' is not recognised as a valid filesystem                                               
--CONFIG-- [con010c] Filesystem 'cgroup' used by 'cgroup' is not recognised as a valid filesystem                                               
--CONFIG-- [con010c] Filesystem 'cgroup' used by 'cgroup' is not recognised as a valid filesystem                                               
--CONFIG-- [con010c] Filesystem 'cgroup' used by 'cgroup' is not recognised as a valid filesystem                                               
--CONFIG-- [con010c] Filesystem 'cgroup' used by 'cgroup' is not recognised as a valid filesystem                                               
--CONFIG-- [con010c] Filesystem 'cgroup' used by 'cgroup' is not recognised as a valid filesystem                                               
--CONFIG-- [con010c] Filesystem 'cgroup' used by 'cgroup' is not recognised as a valid filesystem                                               
--CONFIG-- [con010c] Filesystem 'cgroup' used by 'cgroup' is not recognised as a valid filesystem                                               
--CONFIG-- [con010c] Filesystem 'fuse.vmware-vmblock' used by 'vmware-vmblock' is not recognised as a valid filesystem

I've tried including those lines, or variations thereof, in "/etc/tiger/tiger.ignore", but they haven't made a difference.

Does anyone have examples of successful entries in /etc/tiger/tiger.ignore, or have you seen a similar issue?

---

### Post by Nutster on 2013-03-31
This happens because Tiger does not know how to analyze these unknown file-system types.  So rather than telling tiger to ignore reporting these lines, instead we will tell it to not bother trying to work with file systems of this type, which should end up being faster anyway.

Go into /etc/tiger/tigerrc.

There should be a line that begins: **Tiger_FSScan_Local=''**.  If not, add it at the end.  The file system type you want Tiger to ignore goes inside the quotes.

The next time Tiger is run after you save the changes, Tiger should ignore this unknown file system type.

---

### Post by NickD-NLUG on 2013-03-31
Thank you, that actually pointed me to the line where I'd implemented a similar fix three years ago ( *blush* ).  Looks like it's worked, thanks again for taking the time to reply.

---

