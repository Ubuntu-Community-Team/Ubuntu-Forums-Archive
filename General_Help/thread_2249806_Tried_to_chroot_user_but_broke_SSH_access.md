---
title: "Tried to chroot user but broke SSH access"
date: 2014-10-24
forum: General Help
---

### Post by lorenzone92 on 2014-10-24
I'd like to chroot user "a" to its homedir.

So I edited "sshd_config" and added these lines, right after "Subsystem sftp internal-sftp":

    Match Group agroup
        ChrootDirectory %h
        ForceCommand internal-sftp
        AllowTcpForwarding no

Of course, "agroup" is a group that has only "a" as member. I saved the file, run "service ssh restart" and boom, I couldn't SSH anymore even with "root" ("PermitRootLogin" is on yes). Why? When I try to access I get "No route to host".
From the already open ssh connection I managed to edit "sshd_config" again and comment the new lines.

What am I doing wrong?

---

### Post by lorenzone92 on 2014-10-25
No one? :)

---

