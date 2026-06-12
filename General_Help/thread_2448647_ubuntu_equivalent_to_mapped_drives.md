---
title: "ubuntu equivalent to mapped drives"
date: 2020-08-11
forum: General Help
---

### Post by Frank P on 2020-08-11
I have a 16.04lts server running Samba. From Windows pc i can map drives on a persistent basis and access them directly. Is there a Ubuntu equivalent?
I have tried searching Google but haven't found anything exactly matching

From Ubuntu I seem to have to login to the network before I open the editor. Then Sublime Text will work but not Brackets - it wants to use ftp

Am I missing something

Thanks

---

### Post by guiverc on 2020-08-11
FYI: Lubuntu 16.04 LTS being a flavor of Ubuntu had only 3 years of supported life ([https://lubuntu.me/xenial-5-released/](https://lubuntu.me/xenial-5-released/) [http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/](http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/)) which ended 2019-April.

Ubuntu 16.04 LTS Server (no desktop) or Desktop (Unity 7) have 5 years of supported life and are still supported. Refer release notes, or use `ubuntu-support-status` or your own system to confirm this is the case.

Myself I don't use SaMBa regularly (I rely on NFS), so I most run a script to cause my [SaMBa] mounts to occur, however in the past when I've wanted to have them *auto*-mount, they were described in the *file system table* (/etc/fstab) so were mounted on boot (the lines are commented out now).

---

### Post by Frank P on 2020-08-11
The file server with the files i want to edit is  running the server version of 16.04LTS. I'm just now in the process of setting up an 18.04lts desktop to replace my windows 10. I have mounted files on an ntfs system in the past but I find Samba a lot more convenient with Windows.
Would you mind sharing your script for automounting Samba shares
Thanks

---

### Post by gsahli on 2020-08-11
I'm not sure I can help, but do you mean you are on an Open Directory/Active Directory/LDAP network that you have to log into?

---

### Post by Frank P on 2020-08-11
it's a plain "out of the box" local area network
From Windows I can map a permanent connection by a one time creation of a desktop shortcut and

Select a drive letter
enter address e.g. \\192.168.1.89\samba share name
enter userid and password

Thanks

---

### Post by QIII on 2020-08-11
Hi!  This is not a direct answer to your question, but a bit of a read [here ]("https://help.ubuntu.com/community/Fstab")(confusing as it may be to you right now) might help you familiarize yourself with the bits and pieces.

Don't do anything immediately after reading.  You'll still have a lot of questions and we'll have a lot of (hopefully helpul) answers.

---

### Post by Frank P on 2020-08-11
I'm okay with fstab - I've done it before between 2 ubuntu servers. It's a lot messier than just mapping a network drive in Windows

But if that's what I have to do, then I will

Thanks

---

### Post by SeijiSensei on 2020-08-11
If you have a mixed network with Windows and Linux clients, you can run both Samba and NFS to share the same directories. I do that myself. Most of the time I'm running Linux and thus use NFS, but I run the occasional Windows session and connect to the Samba server.

You can set up a permanent NFS mount in /etc/fstab.

---

### Post by Frank P on 2020-08-11
okay, that's what I'll do

Thanks

---

