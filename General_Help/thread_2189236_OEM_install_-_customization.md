---
title: "OEM install - customization?"
date: 2013-11-21
forum: General Help
---

### Post by ajay4 on 2013-11-21
Hello,
I'm having trouble with an OEM install.
I've spent 2 weeks customizing the Ubuntu for two of my friends as per this manual.
[http://askubuntu.com/questions/36671/how-do-i-pre-install-ubuntu-for-someone-oem-install](http://askubuntu.com/questions/36671/how-do-i-pre-install-ubuntu-for-someone-oem-install)
When I select "Prepare for shipping to end-user" icon the machine reboots and asks for a new user/pass, timezone etc correctly for the new user.

The problem is all of my customization is gone!
Its simply like a fresh install of Ubuntu as none of the programs nor changes I made exists!

I have several stages of backups so I don't need to redo everything again.

But how do I get the end user to receive my customization?

Please help
Ubuntu 12.04 LTS

---

### Post by sudodus on 2013-11-21
Welcome to the Ubuntu Forums :-)

If you customize only the OEM user's desktop environment, it will not be ported to the client's desktop environment. ***What kind of customisations have you done?***

I have used OEM installs several times, but I'm not an expert of this field. I'm asking you to tell us details [COLOR=#ff0000]so that people with more experience can see what you want[/COLOR]. That makes it easier for them to give good advice.

An example: Instead of editing [FONT=courier new]**~/.bashrc**[/FONT], you can  edit **[FONT=courier new]/etc/bash.bashrc[/FONT]**

---

### Post by ajay4 on 2013-11-21
> **sudodus said:**
> 
If you customize only the OEM user's desktop environment, it will not be ported to the client's desktop environment. ***What kind of customisations have you done?***

I've added/installed:
VLC media player
7zip
edited firefox
a desktop background image
placed several files and folders within the home folder

Ubuntu updates:
For the first few weeks I did 'important security' and 'recommended updates'
In the past week I've only installed 'important security' updates

Thanks for your help

---

### Post by sudodus on 2013-11-21
I can at least answer a few of the questions:

> **ajay4 said:**
> I've added/installed:
VLC media player
7zip

If you have installed them in the normal way (from the repositories), they should be available for all users (they are system-wide).
> 
edited firefox
a desktop background image
placed several files and folders within the home folder

I think these are tweaks, that are stored in hidden files '.files' in the home directory of each user. But you can change the default picture for everybody, and it would also be the background of the end user until [s]he changes it. I don't know a general way how to solve these problems.
> 
Ubuntu updates:
For the first few weeks I did 'important security' and 'recommended updates'
In the past week I've only installed 'important security' updates

Thanks for your help

Updates/upgrades should also be available for all users with administration alias superuser alias root privileges (they are system-wide). The first end user gets root privileges and can run ***sudo*** and ***gksudo*** tasks, that need password, for example system updates/upgrades. Otherwise something is wrong.

The system should be set to offer updates/upgrades as soon as there are security updates. I usually install all of them, also the recommended ones.

---

