---
title: "Network Folders do not show in Applications"
date: 2007-05-14
forum: General Help
---

### Post by rjmusto on 2007-05-14
I've tried putting a post for this under the network forum but got no replies....
Maybe I'm being really stupid - I don't know!

I'm running a small network with an external drive attached to a networked laptop (running Edgy actually) and use it as a central store for files.  It works just great with a Windows PC and two MACs.

I've dual installed Feisty on this machine and got it working ok on the network.

I can browse the shared folders no problem and have added a couple of 'connect to server' folders that show ok under Places. Great.

Why then do none of these network folders show up in the File/Open menus of any of the applications?

I can browse the folders and then launch them with right click and Open With .... mostly ok (Gimp refuses to open any picture files even though Viewer will)

I guess this is some kind of access/privileges issue but can't see where the problem is - user names, passwords, domain  names are all the same as on the other machines.

Help somebody!

---

### Post by MoLE on 2007-05-22
I agree this is a frustrating problem.  My understanding is that the issue is with the file open/save dialog boxes, which are separate to nautilus.  And so although you can access shares using nautilus windows, you can't through the application.  I gather the way around this is to mount the samba share using smbfs or via fstab at boot time.

There is a howto on doing this on the [doc.gwos.org]("http://doc.gwos.org/index.php/HowToMountsmbfsSharesPermanently") site, I believe, and on [ubuntuguide.org]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read").

HopeThisHelps.
;)

---

### Post by measekite on 2007-09-15
I am having a similar problem but not exactly the same.  I can access the network volumes and manipulate them with nautilus.

However I can also read and write to the network volumes using Open Office.  The mounted volumes appear in the Open dialog for Open Office.

I have also done some early testing with a few other applications like music players and image viewers and they are ok as well.

Gimp is a real problem.  Gimp cannot see the network at all.

---

### Post by peabody on 2007-09-15
This is a problem with gnome-vfs.  It was invented because mounting network shares via the kernel was a PITA, /etc/fstab, slow dows, lockups and problems when network shares would go down, etc, etc, so the decision was made to do the whole shebang from userspace via an interface everyone could use.

Problem is, only works with people who use it.  Gimp is a big time offender here.  Basically if a person hasn't written their application to use gnome-vfs, it won't.

---

### Post by measekite on 2007-09-15
I will give this a try.  I know about fstab as I used it to wrtie to an ntfs drive using ntfs-3g but I am not familiar with smbfs.  Would you shed some light on that.

But how does this explain that all of the Open Office applications, rhythmbox, banshee, gnumeric and others do not have the problem but Gimp, Abiword, Scribus, Project Manager and others do?

Does this happen only when you try to access a Windows Share on a Windows Server or does it happen with Linux servers as well?

---

### Post by peabody on 2007-09-15
> **measekite said:**
> 
But how does this explain that all of the Open Office applications, rhythmbox, banshee, gnumeric and others do not have the problem but Gimp, Abiword, Scribus, Project Manager and others do?


I explained this in my previous posting.  It's up to these application developers to make their apps work with gnome-vfs.  They're either lazy, or have chosen not to for whatever reason.

smbfs works for everything because it mounts the filesystem via the kernel into the system-wide vfs so everything can see it.

---

### Post by measekite on 2007-09-16
Using the links below (MoLE's post) I tried for quite some time to make this work.  I do not have Samba Server loaded since, at present, I do not intend to share Linux files.  I do have Samba-Common and friends loaded and believe that contains a Samba client that should allow me to access the Win2k network server.

The guide provides code to mount a network share in /media that should allow Gimp (and friends) to access and see the folders.  The code I tried is for manual but there other entries for boot up.

Here is an example but I could not make it work.

sudo mount //192.168.0.2/win2k-sharename  /media/sharename/ -o username=myusername,password=mypassword,dmask=777,fmask=777

Any help would be appreciated.

[http://ubuntuguide.org.]("http://ubuntuguide.org./")

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount.2Funmount_network_folders_manually.2C_and_allow_all_users_to_read)

---

### Post by oomingmak on 2007-09-16
Maybe I shouldn't be commenting on an issue as advanced as this (as I'm a total Linux noob) but can't you just use FUSE to work round this issue?

I was getting really wound up by the fact that File Roller would not even so much as open any archive files that were on a network location, so I installed FUSE and it then worked fine (as did all the GTK dialogs that I tried).

---

