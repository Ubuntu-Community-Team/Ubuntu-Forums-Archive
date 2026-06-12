---
title: "Setting time automatically at boot(without network)"
date: 2006-09-24
forum: General Help
---

### Post by Jimmy_r on 2006-09-24
I have installed dapper on a PowerBook G3 for a friend.
The PRAM battery is apparently dead [https://help.ubuntu.com/community/UbuntuDateBug](https://help.ubuntu.com/community/UbuntuDateBug)
Which will prevent gnome from starting.
The solution is to enter a terminal and do something like this.```
sudo date -s "Fri Nov 11 19:11:32 GMT 2005"
```

Now i wonder if there is some way to set the time like that automatically in the boot process. It does not have to be correct, the above string would do just fine. I just dont want to say "Do a ctrl-alt-F2, write sudo date -s "Fri Nov 11 19:11:32 GMT 2005" write your root password, do a ctrl-alt-f7, repeat this everytime the power has been off." to a non-tech-savvy person.

She only has a dial-up connection so unfortunately it wont be possible to synchronize with internet servers at boot.

So, any suggestions? I am thinking that either some kind of startup script with root priviledges or some kind of fake timeserver on the system might do the trick, not really sure how to do it, though.

---

### Post by yopnono on 2006-09-24
Put it in the "/etc/rc.local" without the sudo, since the script run as root the sudo is not needed

EDIT:
If the cmd needs to run earlier then the "rc.local", then create you own script.

[http://wiki.linuxquestions.org/wiki/Update-rc.d](http://wiki.linuxquestions.org/wiki/Update-rc.d)

---

### Post by Jimmy_r on 2006-09-24
That did the trick! Thanks.

---

