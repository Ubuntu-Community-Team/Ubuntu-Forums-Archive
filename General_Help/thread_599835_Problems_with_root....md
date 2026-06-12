---
title: "Problems with root..."
date: 2007-11-01
forum: General Help
---

### Post by Death Rider on 2007-11-01
I think I need to log on as root :D Read on, I'll explain why :)
When I tried entering root name and password during log on I got rejected: It said that this account doesn't exist or the pass is incorrect. I know the pass is good because I use it in sudo successfully (I'm an absolute beginner with Linux, but I know what sudo means when I copy and paste commands from guides). In one of the "Here are the similar threads we found:" threads I found a phrase "do you have a root account enabled". I guess it must be disabled... How do I change that? :P


Now, the first question was sort of a warm-up. I guess the answer will be simple (to enable root do this, that and that). The reason why I need to log in as root is that I have Linux and Windows on separate HDDs. Linux's hdd is usually in a drawer, because it needs a lot of time, which I usually don't have, so I use windows (been using it for 11 years and am not ready to move to Linux). My windows crashed and I decided to use Linux to try and fix this and if am not able to fix it- just to make backups and overwrite a fresh copy of windows. At first I thought that Linux can't "see" the other NTFS windows hdd, but I was wrong. I used "sudo lshw -C disk" and saw the other hdd :) About a half-hour ago I installed GParted. I saw the windows partitions, tried mounting them and then accessing them, but I got rejected and the msg said that I didn't have sufficient permissions... Tried System>Administration>Users and Groups>My user, but the user privileges tab didn't contain what I needed. Actually it had a very short list of privileges... Is that natural? I though it should have about a hundred different check boxes to control various aspects of Ubuntu (Almost everything was selected on that short list)... I thought if I was to log on as root, it couldn't tell me that I didn't have enough privileges, cause as I understand root is like a god of your copy of Ubuntu :P (Yeah, yeah... I know I shouldn't use root, but as I said I'm an absolute beginner, so I try what I think that might work).
So basically the problem is with mounting :) Please help :/

I suggest you visit this link, because It is the same, but I didn't yet know about permissions and GParted and the question there is fairly the same but in other words:
[http://ubuntuforums.org/showthread.php?p=3686654](http://ubuntuforums.org/showthread.php?p=3686654)

---

### Post by TheWizzard on 2007-11-01
read this:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by oldos2er on 2007-11-01
You need only to run gparted as root. Type "gksudo gparted" in a terminal.
 The 'gksudo' part of the command tells Gnome to run the GUI program 'gparted' as root.

---

### Post by Death Rider on 2007-11-02
Hm... I read the text about sudo and now the problem still stands:
how do I use sudo with cd? for example I need to do:" cd /media/Pirmas" but I can't do that because I have insufficient privileges... How do I add sudo to this? :)

P.S. GParted doesn't need sudo to be able to mount the windows partitions :)

---

### Post by TheWizzard on 2007-11-02
> **Death Rider said:**
> 
how do I use sudo with cd? for example I need to do:" cd /media/Pirmas" but I can't do that because I have insufficient privileges... How do I add sudo to this? :)


```
sudo cd /media/Pirmas
```

---

### Post by Death Rider on 2007-11-02
Hehehe, I'm not that dumb :D Here's what you get with "sudo cd /media/Pirmas":
sudo: cd: command not found
:)

Open for more ideas :)

---

### Post by kingpoiuy on 2007-11-02
wow, i've never run across a directory that you cant even 'cd' to without sudo.  That's new to me.  Can you do this: 
```
ls -lh /media
```

That will tell us the permissions on that directory.

[edit]Oh, and root can be enabled in the 'users and groups' area usually found in system>administration. But I DON'T recommend it. Everything here can be fixed with sudo.

---

### Post by Death Rider on 2007-11-02
Hehehe, the same- ls: /media/Pirmas: Permission denied :)
The link given by TheWizzard has this: "Redirecting the output of commands run with sudo requires a different approach. For instance consider sudo ls > /root/somefile will not work since it is the shell that tries to write to that file. You can use ls | sudo tee -a /root/somefile to append, or ls | sudo tee /root/somefile to overwrite contents. You could also pass the whole command to a shell process run under sudo to have the file written to with root permissions, such as sudo bash -c "ls > /root/somefile"."
I don't really know if this is what I need and even if it is, how do I make the same with cd? :)

btw, how do you enable root through User Settings? :) Check all the User Privileges? Change user ID from 0 to smth? :)

---

### Post by TheWizzard on 2007-11-03
> **Death Rider said:**
> 
btw, how do you enable root through User Settings? :) Check all the User Privileges? Change user ID from 0 to smth? :)

use```
 sudo -i
```

---

