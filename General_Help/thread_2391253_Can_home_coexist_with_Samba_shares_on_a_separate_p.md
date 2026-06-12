---
title: "Can /home coexist with Samba shares on a separate partition?"
date: 2018-05-07
forum: General Help
---

### Post by ebsf on 2018-05-07
I'm setting up a Samba file server with user-level security.  The initial thought is to edit fstab to mount an existing data partition to /srv/nwk-data and configure Samba to facilitate this.  Subdirectories there will be things like /music, /recipes, etc.  So far, so good.

The next question is whether and how /home and its user subdirectories can be put on the same partition as the Samba share.  Put otherwise, (a) can /home be a subdirectory in a partition mounted elsewhere (e.g., /srv/nwk-data/home); or (b) can a Samba share be a subdirectory of /home if a partition is mounted there (e.g., /home/nwk-data)?

I've been rooting around for several hours and haven't been able to find much of anything on-point, and any thoughts would be much appreciated.

---

### Post by TheFu on 2018-05-08
Not certain I understand.

Home directories need to have Unix permissions, which SAMBA/CIFS doesn't provide.  Certain subdirectories under HOME need Unix permissions too, but many can be CIFS file systems.

However, it isn't clear if you want 1 mount or 5?  Also it isn't clear if you want the CIFS storage to be per-user or shared by all users (or shared by a subset)?

To share /home across multiple Unix systems is best accomplished with nfs and autofs.  This is done all the time.  Startup files will need to handle any differences between the platforms.  In the 1990s, my HOME was shared across Solaris, SunOS, HP-UX, AIX, Linux, OSF/1 and a few other system types.  Had to create different binaries for compiled tools and had most scripts check the OS to decide which options to use for external programs.

You can share Home directories using samba with Windows, no problem.  There is a special [Homes] section just for this in the smb.conf.

Maybe a clear 'tree -d' listing for a few home directories would be helpful if some explanations for how each subdirectory should appear?  That would help me.

Have you considered using symbolic links?

---

### Post by SeijiSensei on 2018-05-08
A Samba (or "CIFS") filesystem does not support Unix primitives like user and group IDs and permission masks.  That's why it is preferable to export home directories using the NFS filesystem which is native to *nix.  

I have both a local /home partition on every machine.  I also have an NFS share on a central server that exports its /home and is mounted in a directory I created under /media on the client machine.  Projects that I'm working on reside in a "Documents" directory on the server.  I've replaced the default "Documents" folder in $HOME with a "symbolic link" to the one on the server.  My local /home directory thus ends up holding the configuration files for my desktop session (in places like $HOME/.config) and random files.  If I want to ensure access to a file across my various computers, I copy it to the server.

---

### Post by SeijiSensei on 2018-05-08
A Samba (or "CIFS") filesystem does not support Unix primitives like user and group IDs and permission masks.  That's why it is preferable to export home directories using the [NFS filesystem]("https://help.ubuntu.com/community/SettingUpNFSHowTo") which is native to *nix.  

I have a local /home partition on every machine.  I also have an NFS share on a central server that exports its /home. I mount that exported share to a directory on my local client machine I created under /media (similar to your use of /srv).  Projects that I'm working on reside in a "Documents" directory on the server.  I've replaced the default "Documents" folder in $HOME with a "symbolic link" to the one on the server.  My local /home directory thus ends up holding the configuration files for my desktop session (in places like $HOME/.config) and random files.  If I want to ensure access to a file across my various computers, I copy it to the server.

It's possible to run both Samba and NFS on the same server and distribute the same files both ways.  I do this so that Windows machines on my network can access the same files as Linux machines.

---

### Post by 1clue on 2018-05-08
Trying to avoid things already covered above, but forgive me if I reiterate something:
[LIST=1]
[*]You can boot a Linux system completely diskless using only your BIOS if the hardware and firmware allow it.
[*]You can keep a kernel local and boot everything else from the network.
[*]You can have any amount of your storage tree be across the network.
[*]You really don't want to use CIFS for directories which are in the standard tree. Meaning pretty much anything important.
[*]Most commercial file servers will share the same space using both CIFS and NFS. NFS is what you want for what you're asking.
[/LIST]

---

### Post by SeijiSensei on 2018-05-08
If all the client machines are running Linux, use NFS.  If some machines run Windows, you'll need a mix of NFS and CIFS.

---

### Post by ebsf on 2018-05-08
Thanks to all.  To respond:

One mount.

Windows clients, so NFS isn't available.  (Unless we upgrade the clients from Pro to Enterprise, which isn't happening.)

Since have figured out usermod can get the move done to /wherever.  Also need to edit the configuration files for adduser and useradd so new users' /homes end up in the right spot.  Samba to share things, easy, just need to know that the system can find /home in the first place.

Symbolic links actually may have some utility.  Windows offline files is a workhorse, though.

---

### Post by 1clue on 2018-05-08
I think my understanding of your situation is changing.

Generally speaking:
[LIST=1]
[*]If you have Windows clients, then your file server should provide a Windows file sharing mode which is native to Windows clients you use. 
[*]If you have Linux clients, then your file server should provide NFS, probably on top of the same directory structure. 
[*]If you have Apple clients, then NFS will work but there's also Apple's native file sharing mode which makes it easier for Apple users. Again, over probably the same directory structure. 
[*]These can be provided simultaneously over the same data. I don't know how, but I've used the result. 
[/LIST]

In other words, it's best for your file server to provide a service which is native for its clients rather than try to modify every client to use a single service mode.

IMO I would try to leave your server's authentication and /home directory out of the equation. Configure the authentication and file service such that it is an independent system and your file server's security is intact. Use a separate directory share for home directories, like /var/samba/homes or something.

***Edit:** I would also put your samba shares on an LVM filesystem. I would have a volume group for samba homes, and another for the rest. This way you can resize the filesystems on the fly, add or remove or replace disks as necessary without harming your Linux system and mostly without downtime.*

---

### Post by TheFu on 2018-05-08
+1 on using LVM (or ZFS).  ZFS has a CIFS server built-in, BTW.

I'd add, if the end-users don't need to login to the Linux system for any reason, except for storage access, then I'd use a different authentication method than local user accounts.  PAM supports using LDAP for external authentication. [https://help.ubuntu.com/lts/serverguide/samba-ldap.html](https://help.ubuntu.com/lts/serverguide/samba-ldap.html)  or AD [https://www.howtoforge.com/samba_active_directory](https://www.howtoforge.com/samba_active_directory)

I've used LDAP, but not AD.

I wouldn't use symbolic linking with samba and expect Windows to honor it.  There are specific options necessary to support it in samba, but those options have significant security problems which are best avoided.

But only you know the full problem to be solved.

---

