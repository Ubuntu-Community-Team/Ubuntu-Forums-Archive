---
title: "Boots to command line"
date: 2024-02-25
forum: General Help
---

### Post by Hvidemose on 2024-02-25
My ubuntu started to boot in to command line interface. It seems like the bootloader is setup correctly - so I tried some different commands. 
Fx I tried "sudo apt-get install --reinstall xorg" and got the response : "e: unmet dependencies. Try "apt --fix-broken install" without packages (or solutions)"

I have some important documents on there, so I need to get in.

Can any one help me in the right direction?

---

### Post by oldfred on 2024-02-25
Did you run the "apt --fix-broken install"?

First thing is to use Ubuntu live installer, mount partition with data you really want to keep & back it up NOW.
Your data is not important unless you have good backups. 
Most often a user makes an error & erases data, but hardware is not guaranteed to last forever. I find hardware always fails the day before I plan a backup.

Simple manual rsync & rdiff theFu
[https://ubuntuforums.org/showthread.php?t=2471454&p=14078689#post14078689](https://ubuntuforums.org/showthread.php?t=2471454&p=14078689#post14078689)

---

### Post by Hvidemose on 2024-02-25
Thanks for the response &#128077;
Yes I tried "apt --fix-broken install", but get good pile of errors (image of screen: [https://we.tl/t-KMXwAfwTEf](https://we.tl/t-KMXwAfwTEf)).

Regarding the backup, then I have almost everything backed up - but since the partition is encrypted, and im in a bit of a hurry, I'll take a chance with that.

---

### Post by oldfred on 2024-02-25
You can attach screen shots directly here. Most of us will not go to unknown sites.
 If you use the Forum's Go advanced editor, you can use the paperclip icon to attach screenshots or other info. Post #4 , also no larger than1024x768 if photo
[https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

I do not use encryption except for one small partition on laptop. My desktops, are almost always on, so encryption does no add anything.
Some with encryption, recommend really good backups and then if it takes more than an hour to fix, just reinstall & restore data.

chroot & troubleshooting Full system encryption
[https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting](https://help.ubuntu.com/community/ManualFullSystemEncryption/Troubleshooting)

Recover files on encrypted drive
[https://ubuntuforums.org/showthread.php?t=2382995](https://ubuntuforums.org/showthread.php?t=2382995) & 
[https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line](https://askubuntu.com/questions/63594/mount-encrypted-volumes-from-command-line)

---

### Post by Hvidemose on 2024-02-26
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293436&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293437&stc=1[/IMG]
No worries :-) So I got this results. One is using "sudo apt --fix-broken install" and the other from "[COLOR=#000000][FONT=&quot]sudo apt-get install xserver-xorg"[/FONT][/COLOR]

---

### Post by oldfred on 2024-02-26
Please do not post in line. Just add the attachments.
Not everyone has high speed Internet.

Is Internet working?
All those errors might be that it cannot connect.
And fix needs to work or be resolved before you try to install anything else.

---

