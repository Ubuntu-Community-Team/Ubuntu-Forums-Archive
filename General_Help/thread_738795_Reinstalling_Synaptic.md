---
title: "Reinstalling Synaptic"
date: 2008-03-29
forum: General Help
---

### Post by rectec794613 on 2008-03-29
As in my previous post about Synaptic, I have a problem with it.
I tried to move the root folder to the home folder in a stupid attempt to make root a user I can login to via the Login Screen. Don't ask why. All I can say is that it created a whole new problem.:( So now I have 202 IMPORTANT updates available and I cant install them because of my Synaptic issue. I get the following error when I try to run Synaptic:
> E: ERROR: could not create configuration directory /home/root/.synaptic - mkdir (2 No such file or directory) So can someone PLEASE help me with this?:( I'm not really up to reinstalling the whole system for like the 20th time. Just tell me how I can reinstall Synaptic or at least tell me where to get a download for an old version which I can update.


Thanks in Advance:grin:

---

### Post by kaboodle_fish on 2008-03-29
Does typing in the terminal "sudo apt-get install synaptic" not work?

---

### Post by mvan83 on 2008-03-29
> **rectec794613 said:**
> As in my previous post about Synaptic, I have a problem with it.
I tried to move the root folder to the home folder in a stupid attempt to make root a user I can login to via the Login Screen. Don't ask why. All I can say is that it created a whole new problem.:( So now I have 202 IMPORTANT updates available and I cant install them because of my Synaptic issue. I get the following error when I try to run Synaptic:
 So can someone PLEASE help me with this?:( I'm not really up to reinstalling the whole system for like the 20th time. Just tell me how I can reinstall Synaptic or at least tell me where to get a download for an old version which I can update.


Thanks in Advance:grin:

The home directory for the root user is /root not /home/root (like it would be for any other user). I think you're going about this the wrong way though. It's unnatural to force a root user onto an ubuntu system. Log in as a normal user and just run 
```
sudo apt-get upgrade
```

---

### Post by apollyon0810 on 2008-03-29
I'm getting the same problem as this guy.  Tho I didn't move any folders, I tried enabling the root user by setting a password with "Users and Groups"   Now I get this error whenever I try to install/remove software, or just open the Synaptic Package Manager.

---

### Post by rectec794613 on 2008-03-29
> **kaboodle_fish said:**
> Does typing in the terminal "sudo apt-get install synaptic" not work?
No, I've tried that: > robert@ubuntu:~$ sudo apt-get install synaptic
[sudo] password for robert:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
synaptic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 202 not upgraded.

---

### Post by pointone on 2008-03-29
```
sudo apt-get --reinstall install synaptic
```

---

### Post by rectec794613 on 2008-03-29
> **pointone said:**
> ```
sudo apt-get --reinstall install synaptic
```
Thanks, pointone. It reinstalled Synaptic.
But now I know its not an issue with Synaptic. But an issue with my Root Folder.
So how can I reinstall my system WITHOUT messing up anything or losing my saved docs?

---

### Post by pointone on 2008-03-29
Post the exact error message/explain why you believe it's a problem with your root, please.

---

### Post by rectec794613 on 2008-03-29
> **pointone said:**
> Post the exact error message/explain why you believe it's a problem with your root, please.
The exact error message: > E: ERROR: could not create configuration directory /home/root/.synaptic - mkdir (2 No such file or directory)

I know its a problem with my root. I cant move my root folder (from the home folder) back to the root folder in the directory: **_./_**
But the folder's *invisible*, so to speak.

---

### Post by defmomo on 2008-03-30
How did you move the root home to /home? Write the command down

---

### Post by rectec794613 on 2008-03-30
Screw it all. I'm just gonna reinstall the whole system.:icon_frown:

---

### Post by kellemes on 2008-03-30
```
sudo usermod -d /root root
```

---

### Post by rectec794613 on 2008-04-02
I'm DONE you guys. I reinstalled the *whole* system *AGAIN.*
So I dont need anymore help. Thanks anyway and I hope this ***NEVER*** happens again.:)

---

### Post by Crafty Kisses on 2008-04-02
> **rectec794613 said:**
> I'm DONE you guys. I reinstalled the *whole* system *AGAIN.*
So I dont need anymore help. Thanks anyway and I hope this ***NEVER*** happens again.:)

Hopefully not. :)

---

