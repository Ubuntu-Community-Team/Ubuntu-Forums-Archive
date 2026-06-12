---
title: "setting up Samba share"
date: 2013-01-12
forum: General Help
---

### Post by Nik2013 on 2013-01-12
I'm still very much an ubuntu newb and I really could use some help with setting up my samba share properly. The other computers in my house are all windows 7 btw. Could you guys look over the method im going to use to setup the share and tell me whether it will work as intended, and if there is anything else I have missed out?

First I'll do a full system reinstall with ubuntu desktop 12.04.1 LTS. I've got two hard drives, the first i'll split into a system partition. The second partition along with the second hard drive will both be for my media/data. Next install samba and storage device manager. Run storage device manager, name my shared drives and mount them (this should auto mount them at startup i think). Run nautilus with root permissions and go into the properties of the drive/partitions, check the tabs for 'share this folder' and 'allow others to create and delete files.' Lastly create 3 samba users and passwords.

As far as I know the above should work, what do you lot think? is there a better way of doing this that i should use instead? Also whats the terminal command to add samba users and passwords?

---

### Post by TheFu on 2013-01-12
> **Nik2013 said:**
> I'm still very much an ubuntu newb and I really could use some help with setting up my samba share properly. The other computers in my house are all windows 7 btw. Could you guys look over the method im going to use to setup the share and tell me whether it will work as intended, and if there is anything else I have missed out?

First I'll do a full system reinstall with ubuntu desktop 12.04.1 LTS. I've got two hard drives, the first i'll split into a system partition. The second partition along with the second hard drive will both be for my media/data. Next install samba and storage device manager. Run storage device manager, name my shared drives and mount them (this should auto mount them at startup i think). Run nautilus with root permissions and go into the properties of the drive/partitions, check the tabs for 'share this folder' and 'allow others to create and delete files.' Lastly create 3 samba users and passwords.

As far as I know the above should work, what do you lot think? is there a better way of doing this that i should use instead? Also whats the terminal command to add samba users and passwords?

We were all noobs at some point. ;)  Good idea to ask before you start too much.

I wouldn't bother "reinstalling" anything if samba is the only reason. It just isn't necessary. 
I would strongly suggest that you setup all the shares using CLI commands, not using a GUI.  You can save all the CLI commands to a file so later you know exactly what you did.  GUI tools are easy to use, but hard to explain what you did and next to impossible to document. CLI is easy to document, you'll have the exact commands.

You didn't mention anything about backups, RAID, authentication or firewalls. Do you have those covered?  Will you use LDAP to manage the users or are you going old-school and using the samba-built-in method?

Do you have a good understanding of file permissions and groups?  You'll need to create a group and put the users into it if you want to allow multiple people to edit the same files and directories.  It is a good idea to force the group in those file areas too - use the group-sticky bit.

[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba) should get you started.  If you get into trouble, check the man page for smb.conf with **man smb.conf**.  Everything is explained inside there.  If you really are having trouble, post your smb.conf file here (please remove all the comments 1st).

smbpasswd is the command to initially set samba passwords.  
**man smbpasswd** explains the use.

Did you want to share printers over the network? Samba + CUPS makes that relatively painless and will even support automatic driver installation for PCs running MS-Windows.

Good luck!

---

### Post by Morbius1 on 2013-01-12
> Run nautilus with root permissions and go into the properties of the  drive/partitions, check the tabs for 'share this folder' and 'allow  others to create and delete files.' Lastly create 3 samba users and  passwords.When you first create a share from nautilus in the way you described it above it will automatically install the correct samba package. When you are done you can run the following command to check your share definitions:
```
net usershare info --long
```BTW, not sure why you are using "gksu nautilus" to share these partitions unless you are setting these up as not being owned by you.

[COLOR=Blue]**EDIT**[/COLOR]: If you run into any problems posting the output of the following commands will tell people how you are set up:
```
testparm -s
net usershare info --long
smbtree
```

---

### Post by Nik2013 on 2013-01-12
Thanks for your reply TheFu. 

> **TheFu said:**
> You didn't mention anything about backups, RAID, authentication or firewalls. Do you have those covered?  Will you use LDAP to manage the users or are you going old-school and using the samba-built-in method?


Do you have a good understanding of file permissions and groups?  You'll need to create a group and put the users into it if you want to allow multiple people to edit the same files and directories.  It is a good idea to force the group in those file areas too - use the group-sticky bit. 

I haven't yet looked into doing backups with samba, probably do that further down the line. Ubuntu doesn't have it's firewall enabled after installation right? What ports would I need to forward for samba? Don't know what LDAP is (See I'm a newb), could you fill me in on it?

I think I understand permissions ok. For something like this I guess I should disable all guest rights and the 'group' should have read, write and execute permissions on the shares? 

> **TheFu said:**
> 
Did you want to share printers over the network? Samba + CUPS makes that relatively painless and will even support automatic driver installation for PCs running MS-Windows.

Good luck!

I'd like to try sharing printers, but I'll need to read up on it since I've only covered settup up shares and not printers so far. Thanks for the encouragement and the link you provided. This is probably going to me a good while to read up on =P


EDIT:

> **Morbius1 said:**
> 
BTW, not sure why you are using "gksu nautilus" to share these  partitions unless you are setting these up as not being owned by you.

I was using that command because it was the command used in the article I read on creating the shares with nautilus. I've only been using Ubuntu for a week, so I don't know most of the commands properly yet. Thanks for supplying those commands Morbius, might be super useful when I need to come back to the forums because things don't work.

---

### Post by Morbius1 on 2013-01-12
> **Nik2013 said:**
> I was using that command because it was the command used in the article I read on creating the shares with nautilus. 
If there are problems with this you might also want to post a link to the HowTo you are using because usershares was designed to allow a user to create shares of anything he owns without becoming root: 
From man smb.conf:
> Starting with Samba version 3.0.23 the capability for non-root users to add, modify, and delete     their own share definitions has been added. This capability is called *usershares* and     is controlled by a set of parameters in the [global] section of the smb.conf

---

### Post by Nik2013 on 2013-01-12
> **Morbius1 said:**
> If there are problems with this you might also want to post a link to the HowTo you are using because usershares was designed to allow a user to create shares of anything he owns without becoming root: 
From man smb.conf:

I originally started off with this guide:-

[http://linuxhomeserverguide.com/](http://linuxhomeserverguide.com/)

I was only aiming to make a media server so Ignored sections on web server and game server.I also wasn't able to use lvm partitions because I went with desktop os and had to go with ext4. Once I reached the section on configuring samba I encountered so major problems I couldn't get around. So instead I looked for another guide and found this:-

[http://lifehacker.com/5919558/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-ubuntu](http://lifehacker.com/5919558/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-ubuntu)

My current Ubuntu install is now a serious mess so I'll just start over once I can get all the info for setting up samba properly.

---

### Post by Morbius1 on 2013-01-12
> I originally started off with this guide:-

[http://linuxhomeserverguide.com/](http://linuxhomeserverguide.com/)

... Once I reached the  section on configuring samba I encountered so major problems I couldn't  get around
I only looked at the samba section of that guide. I suspect that everyone who followed it ended up in exactly your predicament so don't feel bad.
> another guide and found this:-

[http://lifehacker.com/5919558/turn-a...ne-with-ubuntu]("http://lifehacker.com/5919558/turn-an-old-computer-into-a-networked-backup-streaming-or-torrenting-machine-with-ubuntu")

This is better. He never has you taking ownership of these partitions ( which he keeps calling drives for some reason ) so you have no choice but to use gksu with nautilus. The samba part of that guide looks like it will work.

---

### Post by Nik2013 on 2013-01-12
> **Morbius1 said:**
> This is better. He never has you taking ownership of these partitions ( which he keeps calling drives for some reason ) so you have no choice but to use gksu with nautilus. The samba part of that guide looks like it will work.

[https://help.ubuntu.com/community/Samba/SambaServerGuide#File_Sharing_.28Basics.29](https://help.ubuntu.com/community/Samba/SambaServerGuide#File_Sharing_.28Basics.29)

well the samba page instructions say to right click a directory you want to share and check the 'share' tab, just like the guide said as well. Though when I tried it I couldn't do it without root permission.

If your sharing partitions other then the system partition then they would need to be setup to auto mount at startup right?


EDIT: I was wrong. The samba guide clearly states to share a directory you need permission to access it.

---

