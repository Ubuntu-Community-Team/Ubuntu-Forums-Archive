---
title: "Cannot access Desktop from terminal"
date: 2006-11-29
forum: General Help
---

### Post by Donald99 on 2006-11-29
I just installed Ubuntu 6.06 on Vmware Workstation 5.5.2, and I am trying to install the VMware Tools but I can't access my Desktop in order to access the install file using  the cd command. I get 'no such file or directory' error code. I've checked permissions and I am the owner of the Desktop. I also made sure that I was typing using the proper case.

Does someone has any idea what could be wrong?

Thanks

I'm a newbie to Linux,

---

### Post by igknighted on 2006-11-29
linux is case sensitive.  You are most likely typing 'cd desktop', which doesn't exist.  You need to type 'cd Desktop' instead.  If this doesn't work, try 'cd /home/<username>/Desktop' as perhaps you are starting in a different folder.

---

### Post by Donald99 on 2006-11-29
Thanks a lot, it worked.
For some reason when I go in term mode, I do a ls command and I can see my Desktop but if I type cd /Desktop/ it won't work. I have to type the whole thing every time ie. cd /home/username/Desktop/

---

### Post by bobosity on 2006-11-29
'cd /Desktop/' is much different from 'cd Desktop/'.  If you're not sure where you're starting from use cd ~/Desktop

---

