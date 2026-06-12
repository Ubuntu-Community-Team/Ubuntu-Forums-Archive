---
title: "Local machine file permissions"
date: 2014-04-13
forum: General Help
---

### Post by yXmNpV8z on 2014-04-13
Hi All,

I use Ubuntu for all my desktops and am planning to set up a remote office for my business. It will use LDAP authentication and a VPN but details of that are irrelevant. 

My question is this:
Can I set ALL of the files on the file system to chmod 740? This will ensure nobody can even look at the system files let alone play with them, or would doing this just screw the entire system? You see I'm not sure if any system user other than root needs the system files??

Regards,

Gavin.

---

### Post by TheFu on 2014-04-13
You "can" set any file permissions you like, if you are the owner or root.  If someone else is root or has root privileges, they could see those files too. Also, without encryption, file permissions mean nothing on any platform. Someone can just boot a liveCD/flash boot and do whatever they like, if they have physical access.

And ... if you set all file permissions for system files like that, you will break things - badly.  For your own "data" files, it probably doesn't matter, but when config files and programs are concerned, incorrect permissions matter.

Perhaps learning more about the file/directory permissions is required? They are central to UNIX security, after all, and UNIX/Linux is a multi-user OS from the ground up. That means different users must have different access - sometimes "other" needs access to files for things to work too.

So - I wouldn't do what you are thinking .... except on my personal data files - plus having execute on data files is poor form and confusing.

---

