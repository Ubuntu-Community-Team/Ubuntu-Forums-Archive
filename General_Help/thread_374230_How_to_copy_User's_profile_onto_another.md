---
title: "How to copy User's profile onto another"
date: 2007-03-02
forum: General Help
---

### Post by ghost1969 on 2007-03-02
Hi all, I am using Ubuntu Dapper since months now. 
For some reasons I've been using the box as 'root' user (I know I know...). Now it's time I switch definitely to a regular user for enjoying Linux's security features at most.

Point is that all my files, configs, and desktop aspect .. the 'profile' in general is empty on the other user I should restart the customization effort from scratch.

Any shortcut ? 

Major issue so far is the ownership of files, beloning to root root . And can't find where exactly Nautilus's customizations etc... are stored in.

I do thank you for any suggestion ,

Thank you,
ghost

---

### Post by sisco311 on 2007-03-02
to change the owner of a file open a terminal:
```
sudo chown OWNER:GROUP FILE
```
to operate on files and directories recursively:
```
sudo chown -R OWNER:GROUP FILE
```

---

### Post by ghost1969 on 2007-03-02
Thank you !

---

### Post by ghost1969 on 2007-03-02
Hi again, I've been too fast in answering... 
went to copy everything from /root to /home/user , then have chown'd /home/user so to assign user's files&group ownership.
ls -al /home/user shows it as I wanted : user user
 
So log'd in as 'user' instead of root. 

Paind started,  that system appears unstable and I am getting tons of errors, mainly related to password and root 'memories' errors.
Also links go searching /root/xxx instead of /home/user/xxx

I'd believe must touch something more at / level (i.e. /etc, /var )

Is there anybody there who tried to *seamless* move root content onto a regular user's ? With no side effect ?

Thanks,
Rgds,
G

---

