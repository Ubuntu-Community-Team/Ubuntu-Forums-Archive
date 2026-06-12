---
title: "gksudo vs. sudo"
date: 2007-01-02
forum: General Help
---

### Post by mluntz on 2007-01-02
I am new to ubuntu (Edgy), but have used Linux for a number of years and am confused about when to use gksudo over sudo. I have read that gksudo should be used to invoke graphical applications, and that sudo should be used for command line apps. What is the problem with just using sudo with graphical apps? Before I learned about gksudo I used sudo to edit (with emacs) a file owned by root and apparently nothing bad happened. Was I just lucky? What are the differences between these commands? What would happen if gksudo were used to run a non-graphical operation?

Another question that I have is that I looked at the file that controls sudo operation (sorry, I am not at a ubuntu machine but I think it is /etc/sudoers) and expected to see my username somewhere in the file as a user that had sudo privileges but couldn't find it. I don't remember exactly what was in the file and I am not yet savvy enough to understand the file format, but I got the impression that all users could invoke sudo. Could anyone point me to a good reference to the meaning of the entries in that file?

Thanks,
Mike

---

### Post by invalid on 2007-01-02
On sudo vs gksudo:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

On the sudoers file:
It includes groups as well as users. You belong to the admin group, and any users who belong to this group will get the group permission to use sudo.

---

### Post by aysiu on 2007-01-02
Users in the *admin* group are allowed to use *sudo* to temporarily gain root privileges. That is why you don't see your name in the /etc/sudoers file. The privilege is defined by group, not by specific username.

---

