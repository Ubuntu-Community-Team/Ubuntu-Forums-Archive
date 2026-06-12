---
title: "NIS Client Installation still cannot log in"
date: 2015-10-20
forum: General Help
---

### Post by coleen-phillimore on 2015-10-20
I installed Ubuntu on one of our work machines and followed the instructions for connecting to a client here:

[https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo)

I copied nsswitch.conf and yp.conf from machines that I set up that work for this NIS server.

I can log in from the sudo user I created on this machine from other machines fine.

I can see my global LDAP username when I do "ypcat passwd | grep myself"  but when I log in (or other users log in), it won't accept my password.

some awesome working machine% rlogin newmachine -l myself
myself@newmachine's password: 
Permission denied, please try again.
myself@newmachine's password: 
Permission denied, please try again.
myself@newmachine's password: 
Permission denied (publickey,password).

/etc/defaultdomain is correct.  I even edited the password, shadow and group file (in the directions above) even though I think that's unnecessary.  And removed .ssh/known_hosts.  I've run out of ideas.

Thanks,
Coleen

---

### Post by coleen-phillimore on 2015-10-24
So, I was missing csh installed on this machine.  Now /home isn't mounted but at least I can log in.

---

### Post by coleen-phillimore on 2015-10-26
[http://unix.stackexchange.com/questions/38678/nis-and-autofs-manual-restart-after-a-reboot](http://unix.stackexchange.com/questions/38678/nis-and-autofs-manual-restart-after-a-reboot)

Fixing this made autofs run on reboot and mount /home.

---

