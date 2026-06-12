---
title: "admin help"
date: 2007-02-01
forum: General Help
---

### Post by ronbrooks on 2007-02-01
I need help to get me back as admin.  I am using ubuntu 6.10 and my mistake I too my off the admin account with System/administration/group and now I am not on it and cant get back into it.  I want to add my account back could anyone help me with this.  When I got in to system/administration/   the group is not on the list any more.

---

### Post by taurus on 2007-02-01
So you can't use sudo anymore!  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
id
```

---

### Post by ronbrooks on 2007-02-01
this is the out put

ronbrooks@prodigy:~$ id
uid=1000(ronbrooks) gid=1000(ronbrooks) groups=0(root),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),100(users),101(dhcp),102(syslog),103(klog),104(ssl-cert),105(crontab),106(ssh),107(messagebus),108(avahi),109(lpadmin),110(haldaemon),112(slocate),113(gdm),115(ntp),1000(ronbrooks),1001(judybrooks)

---

### Post by taurus on 2007-02-01
You shouldn't belong to group 0 (root) and you need to be in group admin besides adm to use sudo/gksudo.  Therefore, boot your machine into recovery mode from GRUB menu and at the prompt, run

```
nano /etc/group
```
Now, remove **ronbrooks** from group root (at the top) and scroll down near the end and add **ronbrooks** to group admin.  Save it by holding <Ctrl> while pressing x.  Answer the question with Y and Return.  

Now, reboot with

```
shutdown -r now
```
and log in as ronbrooks and see if you can run this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo aptitude update
(use the same password that you log in with
```

---

### Post by ronbrooks on 2007-02-01
Thank you, Thank you. very much.  I guess that is what happens when you don't know what you are doing, but I did learn something.  

I do have one question and that is now root is not marked at a user of admin.  Should I go back and make it a user.  I am not sure and am a little gun shy at this point.  

Again thank you for your help and all the others on this forum.

---

### Post by taurus on 2007-02-01
> **ronbrooks said:**
>   
I do have one question and that is now root is not marked at a user of admin.  Should I go back and make it a user.  I am not sure and am a little gun shy at this point.  

Root doesn't have to belong to any group at all because it is a special account.  So, no need to add root to adm or admin in /etc/group or you could break your system again.  Just leave the group thing alone for now.  ;)

---

### Post by ronbrooks on 2007-02-01
I have one other question for you and that is I have a open office file named My_Story.odt and it belongs to root and group is plugdev.  I want to chage the group to me but when I use the command line to change it this is what I get

ronbrooks@prodigy:/$ sudo chgrp ronbrooks /media/hdb6/My_Story.odt
Password:
chgrp: changing group of `/media/hdb6/My_Story.odt': Operation not permitted

Why will it not let me change the group to me. 

One other thing is was a file that I greated and mover to my other hard drive so why does in not have me as owner and how can I change that. 

I know some of these are stupit questions but I am not up to seed on Linux yet.

---

