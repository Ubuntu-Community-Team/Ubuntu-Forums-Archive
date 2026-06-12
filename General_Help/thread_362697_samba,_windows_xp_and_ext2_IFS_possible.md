---
title: "samba, windows xp and ext2 IFS possible?"
date: 2007-02-15
forum: General Help
---

### Post by harty83 on 2007-02-15
Is it possible to set up Samba to give access to an ext3 partition to windows then use the windows ext2 IFS driver to access the mounted network drive?

If so, has anyone done this?  I can't seem to get it to work.

I'm trying to get away from fat32 because of problems I'm having.

Thanks!

---

### Post by louis_nichols on 2007-02-16
I'm not sure if I got this right... So you have an ubuntu machine and a windows machine. You installed samba on Ubuntu and you have an ext2 partition that you want to share with windows and are wondering whether the ext2-IFS driver can help. Right?

The thing is that for such a setup you don't need any driver at all. Once you correctly set up samba to share a folder, that will be seen as a compatible netwrk drive by windows irrespective of the fs type. In other words, it just works.

---

### Post by predator on 2007-02-16
zactly.. SMB (samba/windows networking) is just a network protocol that sits on the underlying filesystem driver.. 

Therefore you can do that fine.

---

### Post by harty83 on 2007-02-16
Ah.  Gotcha!  Must be something wrong with my samba config then.  Thanks!

Alan

---

### Post by louis_nichols on 2007-02-16
Then post your problem here if you can't figure it out. There are many people that are able to help you.

Did you read the [wiki post about setting up samba]("https://help.ubuntu.com/community/SettingUpSamba") ? Also, you may try an app called gsambad that gives you a graphical interface to setting up samba. KDE has a module kdenetwork that will place a section in kcontrol to setup samba. So plenty of options there. ;)

EDIT: oh, and, of course, in the default installation, there is an option System>Administration>Shared folders that will let you share folders with samba. However, this leave a lot of things unknow, such as security settings, user access etc.

---

