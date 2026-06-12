---
title: "connect to ubuntu from windows"
date: 2007-05-09
forum: General Help
---

### Post by cybergalvez on 2007-05-09
Hi all I just installed ubuntu on a new test machine, and I was wondering how can I connect to it form my XP box.  What would like to do it connect to it something like an RDP client.  I thought ltsp would be the way to go, but I can't figure out what I need on the windows end to connect to it.  I also know that you can use ssh to connect to the server and then redirect X to the local machine.  But I can't find what I need to do that either.  If anyone knows of a good tutorial that might help I would appreciate it
Jose

---

### Post by strixy on 2007-05-09
> **cybergalvez said:**
>   If anyone knows of a good tutorial that might help I would appreciate it
Jose

Try this one to set up an SSH server on your Ubuntu box:

[https://help.ubuntu.com/community/SSHHowto?highlight=%28ssh%29%7C%28to%29%7C%28how%29](https://help.ubuntu.com/community/SSHHowto?highlight=%28ssh%29%7C%28to%29%7C%28how%29)

You'll need to install an SSH client on your windows box. I can't help you there though.

If it's just simply moving files / shared folders kind of stuff, look into Samba.

[https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29](https://help.ubuntu.com/community/SettingUpSamba?highlight=%28samba%29)

---

### Post by cybergalvez on 2007-05-09
Thanks for the r4eply.  I got ssh working on ubuntu, and I can connect using putty.  What I was hoping to be able to do was actually get to see my ubuntu desktop without having to use vnc
Jose

---

