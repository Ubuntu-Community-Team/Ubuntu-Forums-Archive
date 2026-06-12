---
title: "Not able to write files on my hda..."
date: 2007-07-27
forum: General Help
---

### Post by nasov on 2007-07-27
My Ubuntu won't let me write files onto the File System!
I have checked wether I am the system admin in users and groups sttings window - I am but it still won't let me write to
example:
/usr/share/xmms/skins
when i try to download themes for xmms

or any other files in general

if anyone knows a simple solution to this problem please share...

cheers

---

### Post by moore.bryan on 2007-07-27
[I]/usr/share needs root... so if you save them to your home folder (/home/user_name) and then copy them to the /usr/share/xmms/skins dir:
```
sudo mv downloaded_file /usr/share/xmms/skins/
```
if you're using xmms, you might want to check-out audacious, the "next-generation" xmms.
[/I]

---

### Post by frodon on 2007-07-27
/usr/share/xmms/skins is in the root space so you need root rights to write in. Everything except your home directory require root rights in your ubuntu partition.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by nasov on 2007-07-27
hmmm okay...
that would make a lot of sense buuut...
why can't i write on a partiiton which is a designated windows partions (NTFS).
I can read from it... muisc and vids plus other files (providiing that ubuntu likes them - not dll or exe ;))

---

### Post by frodon on 2007-07-27
> **nasov said:**
> 
why can't i write on a partiiton which is a designated windows partions (NTFS).
I can read from it... muisc and vids plus other files (providiing that ubuntu likes them - not dll or exe ;))This is different, by default ubuntu only offer you read support for ntfs.

If you wish to enable and configure quickly NTFS write support install the "ntfs-config" package using synaptic then use it to enable your NTFS write support (should be in system tools).
This will make your system use the ntfs-3g drivers which offer write support.

---

### Post by nasov on 2007-07-27
okay... and as a ex-longtime-windows-abuser/user is there a need to restart after every package instalation via synaptic?

---

### Post by Espreon on 2007-07-27
NO. This benifet is one of many earned after switching from Winblows to Ubuntu. You don't hafta reinstall after a driver/software package install. But on occasion you do (only for the updates of certain things to kick in) but for video card drivers all ya hafta do is restart X by hitting CTRL-ALT-Backspace.

---

### Post by frodon on 2007-07-27
> **nasov said:**
> okay... and as a ex-longtime-windows-abuser/user is there a need to restart after every package instalation via synaptic?No, restarting after installing an apps is a windows concept i never understood :P

Except in in the case listed in the post above

---

