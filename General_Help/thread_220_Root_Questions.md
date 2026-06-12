---
title: "Root Questions"
date: 2004-10-11
forum: General Help
---

### Post by jivens on 2004-10-11
First let me say...this is THE best distro I have yet tried (and Ive tried most). The first one that I had NO hardware issues of one kind or another; everything was detected and set up correctly.

A minor issue (for me) is working around not being able to login as root and make changes to the system. For example:

First: I wanted to edit my menu.lst file for GRUB and the only way I could find to do this was to chown the directory/file to myself to aquire write permissions. Not a big deal, but it seems that most any file Ive tried to edit belongs to root and I have to go through this process to aquire permissions; a bit tedious for a bad typist like me who relies mostly on point and click...I know, I'm terrible. :wink: Am I missing an easier way to do this? On other distros I would simply login as root to make my changes.

Second: When I try to run XSane as myself, it does not have access to my scanner, but if I *run as root*, it works perfectly. I'm really not sure how to solve this issue so any suggestions would be appreciated.

Lastly: I don't think this is a root issue but to avoid a second post... I have an external Maxtor 40GB USB Hardrive (FAT 32). Under Disks in the Computer menu I see an icon for te drive, but cannot access it, any ideas?

Other than that, I think I'm here to stay.

Thanks In Advance,
Jeff



[/list]

---

### Post by normnmiles on 2004-10-11
Jeff,  there are a couple of ways to answer your first question.  Probably the safest method would be to open a terminal and using the command "sudo" open your favorite editor and edit the file for example "sudo vim /boot/grub/menu.lst".  Using this method there is no need to change file permissions.

One theme of Ubuntu is to use the command "sudo" whenever doing system administration instead of logging in as root.

hth,
joseph

---

### Post by triad169 on 2004-10-11
> Second: When I try to run XSane as myself, it does not have access to my scanner, but if I run as root, it works perfectly. I'm really not sure how to solve this issue so any suggestions would be appreciated. 

Under Computer Menu Goto *System Configuration* and in there is *User and Groups*.  Open that.  Select your username from list.  Then click *Properties* Button.  *Settings for that User* windows will appear.  Click on the *Other Groups* tab.  Then add the Scanner Group to the User's group list.  Log off and log back in and you should be set to go.

Basically scanner priviledges are not enabled by default.

Hope this helps.  As for your root problems  I want to stress that running everything or conforming your system to run normally root options is a bad idea. Personally i think Ubuntu is a little to promiscuous with the sudo command as it is.  Yea for a single user desktop it's not bad security wise but for a multiuser desktop the Ubuntu system would really need to be tightened down some.  also not having a Root Password set as default scares me a little too.  A pretty good read on Linux security can be found here

[http://www.linuxselfhelp.com/howtos/Security/Security-HOWTO-4.html](http://www.linuxselfhelp.com/howtos/Security/Security-HOWTO-4.html)

Triad

---

### Post by FLeiXiuS on 2004-10-12
I would open a terminal ```
sudo -s
``` giving you root privledges, then aquire each file with your favorite text editor.

credits to normnmiles

This is perhaps the best way to go about doing it in my case.

---

### Post by jivens on 2004-10-12
Thanks everyone, I will try your suggestions. I knew it had to be something simple that I was overlooking.

Peace, Jeff

---

### Post by arctic on 2004-10-14
> Lastly: I don't think this is a root issue but to avoid a second post... I have an external Maxtor 40GB USB Hardrive (FAT 32). Under Disks in the Computer menu I see an icon for te drive, but cannot access it, any ideas? 
this seems to be a user-privileges problem once again. i think it can be solved by editing your /etc/fstab. add "user" to the usb-devices as additional group. that should fix it... i hope

---

