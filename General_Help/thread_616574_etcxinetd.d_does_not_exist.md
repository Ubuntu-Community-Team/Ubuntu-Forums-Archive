---
title: "/etc/xinetd.d does not exist"
date: 2007-11-18
forum: General Help
---

### Post by ubuser2008 on 2007-11-18
HEllo I am a new ubuntu user. I am trying to install VNC server so I can access from XP. THe install seems to go fine (following directions from  [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC))
When I go down to the XDM/GDM section. I get stuck on STEP 2 "Create the following file /etc/xinetd.d/vnc"
I have etc but not xinetd.d. So I get directory not found error. 

HELP PLEASE

---

### Post by prince_niceguy on 2007-11-19
here is what i do normally to acess remote desktop of ubuntu.

under preferences menu you should have a remote desktop. just set that up by giving the password.

Now, in win pc install ultravnc. a free app. run vncviewer and connect to your ubuntu comp. there is no need for vnc server as vino (gnome's remote desktop) is already installed by default..

---

### Post by jocko on 2007-11-19
> **ubuser2008 said:**
> HEllo I am a new ubuntu user. I am trying to install VNC server so I can access from XP. THe install seems to go fine (following directions from  [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC))
When I go down to the XDM/GDM section. I get stuck on STEP 2 "Create the following file /etc/xinetd.d/vnc"
I have etc but not xinetd.d. So I get directory not found error. 

HELP PLEASE

You'll probably need to install a package named xinetd:```

sudo apt-get install xinetd
```

---

