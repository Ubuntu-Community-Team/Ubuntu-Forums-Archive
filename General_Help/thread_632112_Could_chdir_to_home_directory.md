---
title: "Could chdir to home directory????"
date: 2007-12-05
forum: General Help
---

### Post by ajeetraina on 2007-12-05
Two weeks back I was working with the LDAP Server but the project work is over.Now I made all the settign back to work.But eventually I lost something.When I am now trying to login asone of the user its throwing an error:


Could not chdir to home directory /home/vjs: No such file or directory
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

Any idea abt the solution???

---

### Post by pointone on 2007-12-05
```
sudo mkdir /home/vjs
sudo cp /etc/skel/* /home/vjs
sudo chown -R vjs:vjs /home/vjs
```

... and try logging back in again.

---

