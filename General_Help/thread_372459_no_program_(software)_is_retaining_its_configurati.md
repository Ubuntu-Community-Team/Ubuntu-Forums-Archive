---
title: "no program (software) is retaining its configuration"
date: 2007-02-28
forum: General Help
---

### Post by kanha on 2007-02-28
last night my ubuntu desktop crashed
after that no program is retaining its configuration
like when i open firefox it open as it was default installed .... then i configure it ..... after one session open it again and buhuhu it is back to default setup

I don't know what to do?
please help me

---

### Post by louis_nichols on 2007-02-28
It sounds like permissions over folders and files in your home folder were somehow scrambled. These two commands should sort you out:

```
sudo chown -R *your-username-here* /home/*your-username-here*
sudo chmod -R 755 /home/*your-username-here* 
```

---

### Post by kanha on 2007-02-28
> **louis_nichols said:**
> It sounds like permissions over folders and files in your home folder were somehow scrambled. These two commands should sort you out:

```
sudo chown -R *your-username-here* /home/*your-username-here*
sudo chmod -R 755 /home/*your-username-here* 
```

oh my God louis_nichols!
I tried same as you told me and now i can't even login in my account,the old problem is as it is :( 
At login it says that user do not have permission on home and some error about 646 owner
please tell me what to do
writing this msg from other windows computer

---

### Post by louis_nichols on 2007-02-28
OK. Here's a safer approach. When the login screen appears, do not attempt to login yet. Instead, press CTRL+ALT+F1 to go to a console window and login there. Next, do this:

```
sudo chown -R `whoami` /home/`whoami`
sudo chmod -R 755 /home/`whoami`
```

Please be attentive to those characters, as they are not ' but `.

---

