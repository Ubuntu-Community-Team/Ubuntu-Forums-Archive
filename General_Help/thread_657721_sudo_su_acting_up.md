---
title: "sudo su acting up"
date: 2008-01-03
forum: General Help
---

### Post by budducci on 2008-01-03
Hi, I'm using Ubuntu Server 7.1.  I'm pretty new to this so please bear with my noobery.

I've completed a fresh install with Samba installed as part of it.  When I first went into the system I was able to sudo su then perform admin functions such as modifying my smb.conf and executing shutdown. 

Now after a couple of days I sudo su, am prompted for my password, which is accepted.  At that point, though, the system still acts as if I am a simple user.  When I try to 'shutdown' I am informed that I need to be root to do this.  I also can not change the smb.conf anymore since it is read only to my user.

Thanks in advance for any suggestions.

---

### Post by Kzin on 2008-01-03
There is only one instance where I know that "sudo su" has been necessary, and that is for the uninstall of google earth.

In any other situation, you should do your administrative commands as "sudo commandToRunHere" instead of "sudo su" to become root.

---

### Post by budducci on 2008-01-03
I tried typing:

sudo shutown now

and was just returned to a prompt with no error message

---

### Post by RC Howe on 2008-01-03
```
sudo -i
``` is (in my mind) a better way to get to a root prompt.
You need a verb in the shutdown message. Try:```
sudo shutdown **-h** now
``` if you want to halt the system, or -r if you want to reboot.

---

### Post by budducci on 2008-01-04
I've tried both of your suggestsions (sudo -i and sudo shutdown -h now)  and I still don't have the ability to shutdown, or do other admin tasks.  This persists after a complete reinstall of the system as well.

---

### Post by astoltz on 2008-01-04
In a fresh install, the first user created should be a member of the admin group and therefore be able to use sudo.  Check if you are in admin by using the command "groups".  It should report all the groups that you are a member of...

---

### Post by budducci on 2008-01-06
The user I created at start up is 'adam'.  It is currently in the groups adam and users.  users is a group I created for use with samba, but it looks like it has probably replaced whatever admin group is supposed to be there, correct?

---

### Post by bodhi.zazen on 2008-01-06
Yea, it sounds like you need to add you user to the admin group.

Boot to recovery mode.

You can then either directly edit /etc/group (comma delineated at the end of the line)

Or with the command line :

adduser <user> <group>

You may want to add your user to cdrom, audio, video, plugdev

---

