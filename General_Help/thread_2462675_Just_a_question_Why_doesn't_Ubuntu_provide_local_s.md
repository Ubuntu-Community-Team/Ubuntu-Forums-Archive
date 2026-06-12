---
title: "Just a question: Why doesn't Ubuntu provide local synchronization of Google drive?"
date: 2021-05-25
forum: General Help
---

### Post by josefranw on 2021-05-25
I have (unsuccessfully) been looking for a way to locally synchronize my Google Drive folder to Ubuntu ever since I installed it a few months ago now.

I know I can "see" and "access" my files in google drive from nautilus but, they do not automatically get downloaded so that they can be accessed locally without Internet.

So, I just have this question: If Ubuntu already can access google drive, why can't it also download the archives and keep them in synch with the online folder?

Is it because they do not have google's permission to do so, would it be "ilegal" or something?

Or, any other reason?

I know there are some apps that "apparently" can do this, but they aren't working anymore (ODrive, for instance or VGrive which doesn't really download anything as all files aparently downloaded weight exactly the same)...

PD: If you do happen to know how to locally synchronize my google drive, please, feel free to tell me how to do it. Thanks.

---

### Post by TheFu on 2021-05-26
Why no Canonical integrations with Box, Nextcloud, Owncloud, SeaFile, Amazon Glacier, DropBox or any of 500 other cloudy storage providers?  Because most of those providers have a Unix/Linux solution already.

Google is a different company known for killing off loved projects. Why would Ubuntu bother to spend the expense to create software to sync when a few years later, they will just kill off the service?

I'd rather know why Ubuntu doesn't make centralized user/group management on a LAN trivial?  The User Manager should easily connect to or setup an LDAP DB on the network and allow any client computer to connect for login credentials. At install time, it would be nice to point a new Ubuntu Desktop at the LAN LDAP server and have the 20 users already configured there automatically connected and their HOME directories automatically mounted over NFS too.  None of these things is bleeding edge. They've all been possible for a few decades, if not longer. It is normal, Unix stuff.  THAT would be something completely self-contained and has been missing from Ubuntu for decades. In 21.04, they've handed over this capability to MS-AD. That's admitting defeat and requires people to spend $1000 for Windows Server and AD licenses and CALs.  Where's the all-Ubuntu solution?  Redhat had a project - FreeIPA - but it was only ported to Ubuntu for a few yrs and then became unsupported again.  FreeIPA is a mess of F/LOSS projects and basically wants a dedicated server, whereas LDAP for a network could be run from a Raspberry Pi Zero. It is extremely light, but the setup and user management is ugly.

---

### Post by CharlesA on 2021-05-26
> **josefranw said:**
> I have (unsuccessfully) been looking for a way to locally synchronize my Google Drive folder to Ubuntu ever since I installed it a few months ago now.

You can use rclone to do that, but I haven't used it myself. The configuration looks complicated as hell (IMO) too.

See here:
[http://manpages.ubuntu.com/manpages/focal/man1/rclone.1.html](http://manpages.ubuntu.com/manpages/focal/man1/rclone.1.html)
[https://rclone.org/drive/](https://rclone.org/drive/)

---

### Post by ActionParsnip on 2021-05-27
I found this but haven't used it
[https://www.omgubuntu.co.uk/2019/10/vgrive-google-drive-linux-client](https://www.omgubuntu.co.uk/2019/10/vgrive-google-drive-linux-client)

---

