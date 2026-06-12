---
title: "sudo: no valid sudoers sources found, quitting"
date: 2017-09-21
forum: General Help
---

### Post by raleigh3 on 2017-09-21
I added a few lines to my sudoers file using gedit.

It looks it broke some things. :-(

gksudo and sudo no longer work.

```
andy@7:~$ sudo caja
>>> /etc/sudoers: syntax error near line 14 <<<
sudo: parse error in /etc/sudoers near line 14
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin
```

---

### Post by deadflowr on 2017-09-22
> I added a few lines to my sudoers file using gedit.
Yep.
All wrong. Never do that
sudoers has it's own safe editing utility: [visudo]("https://linux.die.net/man/8/visudo"). There for this very reason.
Best you can hope for is that you can remove the entries you made using the Ubuntu recovery mode at boot.

---

### Post by raleigh3 on 2017-09-23
Thanks.

I used a pen drive installation to do the repair.

---

### Post by efflandt on 2017-09-23
Change the file back like it was from recovery or live/install system and maybe read the README (and of course **man sudoers**). /etc/sudoers might be changed by updates. You are supposed to put any alterations in files in /etc/sudoers.d/ directory. Then if you trip up, hopefully the file in error would be ignored:```
~$ ls /etc/sudo*
/etc/sudoers

/etc/sudoers.d:
README
```

---

### Post by raleigh3 on 2017-09-24
Thanks.

---

