---
title: "Samba user sharing in fresh 15.10 install issues"
date: 2015-11-15
forum: General Help
---

### Post by MistaED on 2015-11-15
Hello,

I'm a fairly experienced Linux/Ubuntu user. From what I remember on a fresh install to get basic file sharing via samba is to do the following:

- Install Samba
- Setup a share in nautilus/dolphin/system-config-samba
- Do a sudo smbpasswd -a <username> & set the password
- PROFIT! (or do a bunch of sudo service smbd/nmbd restarts until it works)

I can get anonymous shares to work fine that's no problem for 15.10, just not user accounts. I've done this exact thing in 14.04 and other Ubuntu versions and I've got something to work with user login. However, in 15.10 I've done all these steps and it simply will not let me log in with my user and correct password made in smbpasswd!

I can post my smb.conf or whatever, but I'm not modifying it by hand I'm using its defaults with the gui tools to do any mods (if any), and just specifying a user share from my home directory which only allows that one user to access it with read/write. I really don't want to modify stuff by hand if I don't have to.

Surely other people are running into this as well? I'm using Kubuntu 15.10 if that matters, and purged/reinstalled the samba package a few times using dolphin/nautilus/system-config-samba to make a user-created share. And to mention the shares do work in anonymous mode, so this is solely a user logging in issue. It uses tdbsam, also my user is part of sambashare group.

Cheers!

Edit:
SOLVED! Turns out netbios name if it's longer than 15 characters (like in my case) you need to explicitly set it to a 15 char name in smb.conf otherwise it doesn't detect the authentication! Whew!
[https://bugzilla.samba.org/show_bug.cgi?id=11008](https://bugzilla.samba.org/show_bug.cgi?id=11008)
Good to know for others who get tripped up on this bug!

---

