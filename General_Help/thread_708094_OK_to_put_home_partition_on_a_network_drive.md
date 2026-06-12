---
title: "OK to put home partition on a network drive?"
date: 2008-02-26
forum: General Help
---

### Post by MountainX on 2008-02-26
I'm on a GigE LAN. Would I notice any performance issues if my home partition resides on another computer (a file server) on my LAN?

Are there any issues I need to be aware of? What choices do I have in terms of the OS running on the file server? The file server currently runs Windows 2003 R2. The hardware is really solid and very fast - RAID with 15k SCSI drives, for example. Is there a way to keep my home partition on this Windows server?

---

### Post by mbsullivan on 2008-02-26
Hi MountainX,

Sure, it's possible. I don't think you should notice a large performance hit on a gigabit network, especially since the home directory basically stores data, and all executables are held in /usr/bin (typically) or /opt. Perhaps on copying large files, but how many times does that matter?

Since you're going to use your home directory so often, I definitely would NOT try to make it a windows share (CIFS/SMBFS mount). If I were you, I would look into making the windows box a NFS (network file system) server.

Although I've never done it before, there are instructions available for a variety of Windows-based NFS servers. Some instructions from Microsoft can be found [here]("http://support.microsoft.com/kb/324086").

As to mounting the NFS folder, once the server is properly setup, it's much like mounting any other device/drive, only that the path contains an IP address. I'm not sure if there's a way to use WinBind addresses (i.e. Windows machine names), but you could look around. As an example, a mount command for an NFS folder that I used to use looked like the following:

```
sudo mount -o ro 130.202.97.200:/home/user/python/shared_mod_sys_files /home/user/shared_mod_sys_files

```

Of course, you can add more mounting options for added fanciness, but something similar to the above command should suffice. I'm not sure exactly how Windows NFS servers deal with pathnames... that's something you'll have to figure out from documentation. Once you get it working, you could add the mount command to your /etc/fstab file to make it automount on boot.

I know that this doesn't 100% tell you how to do it, but I hope that I've pointed you in some good directions. I'm no "network drive expert", but let me know if you have any questions.

Mike

---

### Post by MountainX on 2008-02-26
Mike - those are awesome tips. I will look into Windows Services for UNIX (NFS).

Does anyone know anything about the partitioning and file system issues when setting the Windows box up for NFS? Will the file system be NTFS or ext3 or something else? Will I have to create a new partition when installing/setting up Windows Services for UNIX?

This sounds like a perfect option for me.

---

### Post by MountainX on 2008-02-26
I found this article helpful:
[http://www.osnews.com/story/5751](http://www.osnews.com/story/5751)

Conclusion

"For those of you waiting for Microsoft Linux forget it. I doubt we will ever see it. But as the need for interoperability grows Microsoft will make good on that commitment. I dont think we will ever see a 100% no Microsoft world so this is where Services for UNIX fits in. Services for UNIX will not make a loyal Linux/UNIX user switch to MS Windows no more than we can change Diehard Mac or Windows fans but for people like me who have to deal with UNIX, Linux and Windows, Services for UNIX is a great tool for that arsenal without having to dual boot or hunt down an available system with the OS you need. My only hope is that people do not snub SFU just because it is an Microsoft product but rather embrace it and use it and support Microsoft for their efforts."

Author
Roberto J Dohnert

---

### Post by MountainX on 2008-02-26
> **mbsullivan said:**
> . If I were you, I would look into making the windows box a NFS (network file system) server.



It seems like I might already have this:

[http://www.microsoft.com/windowsserver2003/R2/unixcomponents/default.mspx](http://www.microsoft.com/windowsserver2003/R2/unixcomponents/default.mspx)

"Windows Server 2003 R2 ships with three UNIX interoperability components, namely, **Microsoft Services for Network File System (NFS)**, Subsystem for UNIX-based Applications, and Identity Management for UNIX. Microsoft Services for NFS requires no components other than those that ship in Windows Server 2003 R2. Subsystem for UNIX-based Applications and Identity Management for UNIX requires additional components to be installed on Windows Server 2003 R2 and on the UNIX servers/clients respectively. This page describes and links to these additional components."

I wonder why I never noticed this before? Again, great tip Mike. Thanks.

---

### Post by mbsullivan on 2008-02-27
Hi MountainX,

I hope it works out for you! Let me know if it's a slick solution... I've never done it before!

Mike

---

### Post by MountainX on 2008-03-28
I originally went with samba (smbfs) but when I upgraded to Hardy, smbfs + gedit no longer works. So now I'm back to considering NFS with my windows server using SFU (services for unix). I expect it to work because that's what it's designed for. My only concern is about security. Previously everyone told me to go with samba for security.

---

### Post by dcstar on 2008-03-28
> **MountainX said:**
> I originally went with samba (smbfs) but when I upgraded to Hardy, smbfs + gedit no longer works. So now I'm back to considering NFS with my windows server using SFU (services for unix). I expect it to work because that's what it's designed for. My only concern is about security. Previously everyone told me to go with samba for security.

What are you taking about? Samba is the method **your** machine uses to access the share - which is not a "Samba" box but according to you a MS box running the file access, are you somehow concerned about security on that box?, if so then you shouldn't be considering using it as an external /home device in the first place.

---

### Post by MountainX on 2008-03-29
> **dcstar said:**
> What are you taking about? Samba is the method **your** machine uses to access the share - which is not a "Samba" box but according to you a MS box running the file access, are you somehow concerned about security on that box?, if so then you shouldn't be considering using it as an external /home device in the first place.

I think I'm missing your point too.

---

### Post by Ramses de Norre on 2008-03-29
NFS is a lot more secure than samba, it uses default unix permissions on files where samba uses the awkward windows system. You don't need to worry about filesystems, each machine uses it's own. The client will sent requests to the server and the server will translate that to filesystem-specific commands itself, it doesn't matter to the client which actual filesystem that is. You should choose the best filesystem for the server (probably ntfs if it's a windows server) and set up NFS, it will look like a native filesystem to the client then.

---

### Post by MountainX on 2008-03-29
> **Ramses de Norre said:**
> NFS is a lot more secure than samba, it uses default unix permissions on files where samba uses the awkward windows system. You don't need to worry about filesystems, each machine uses it's own. The client will sent requests to the server and the server will translate that to filesystem-specific commands itself, it doesn't matter to the client which actual filesystem that is. You should choose the best filesystem for the server (probably ntfs if it's a windows server) and set up NFS, it will look like a native filesystem to the client then.

Thank you. That is interesting news and good news. In a security discussion somewhere else on these forums, I was advised to use samba for better security. However, samba is slower and now I am having other problems with samba so it would be great to use NFS. 

My choices are:
1. use Windows Services for Unix (SFU) on the file server.
2. install Ubuntu on the file server.

I tried #1 yesterday and I can't quite get it to work yet: [http://ubuntuforums.org/showthread.php?t=738821](http://ubuntuforums.org/showthread.php?t=738821)

I am reluctant to try #2 right now because my RAID controller (Areca) doesn't have email alert capability under Linux and because changing the OS would be a big disruption and a lot of work. However, since I do plan to eventually get rid of Windows on all machines, I would consider this option too.

But I am glad to hear that I misunderstood the security issues related to NFS. I wish I could find that prior discussion.

UPDATE:
In the first post of[ this thread]("http://ubuntuforums.org/showthread.php?t=730447") I said:
"From the replies in this thread below, my solution is to not use NFS. I used samba instead."
As mentioned, I thought this was the security advice I had gathered. I'll correct that post, but I need to better understand why the earlier advice was wrong. I was told something like "if a remote user gains root access, he has root permissions on NFS shared files..."

---

### Post by MountainX on 2008-03-29
I just found this link that says the same thing I was told before:
[http://books.google.com/books?id=E2m8h5giL9YC&pg=PA158&lpg=PA158&dq=ubuntu+OR+linux+root-access+NFS+security+OR+secure+smbfs+OR+samba&source=web&ots=7nZ5u2A1AJ&sig=4dOfvgD2jYs4pn57O1SRdhRhuow&hl=en](http://books.google.com/books?id=E2m8h5giL9YC&pg=PA158&lpg=PA158&dq=ubuntu+OR+linux+root-access+NFS+security+OR+secure+smbfs+OR+samba&source=web&ots=7nZ5u2A1AJ&sig=4dOfvgD2jYs4pn57O1SRdhRhuow&hl=en)

It says about NFS:
"...there have been numerous severe security problems, some of them unsolvable without incompatible protocol changes. Because of this, it is recommended that it not be used at all except on private secure networks..."

That is exactly why I previously went with samba, on advice of people in the forums more experienced than me.

(The file server is on a LAN, but there is wifi and broadband connectivity to the Internet.)

---

### Post by MountainX on 2008-04-01
Here is another good article on NFS networking:
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch29_:_Remote_Disk_Access_with_NFS](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch29_:_Remote_Disk_Access_with_NFS)

The article covers many aspects fo NFS. The security section confirms what I was told elsewhere:

NFS and rpcbind have had a number of known security deficiencies in the past. As a result, I don't recommended using NFS over insecure networks. NFS doesn't encrypt data and it is possible for root users on NFS clients to have root access the server's filesystems. You can exercise security-related caution with NFS by following a few guidelines:

    * Restrict its use to secure networks
    * Export only the most needed data
    * Consider using read-only exports whenever data updates aren't necessary.
    * Use the root_squash option in /etc/exports file (default) to reduce the risk of the possibility of a root user on the NFS client having root file permission access on the NFS server. This is normally an undesirable condition, especially if the NFS client and NFS server are being managed by different sets of administrators.
    * Make NFS run on predefined TCP and UDP ports as this makes the management of firewall rules much easier. This can be done by editing your /etc/sysconfig/nfs file. In this example we are using ports 4000 to 4003 for the lockd, mountd, statd and rquotad daemons that are a part of NFS. The other NFS components, rpcbind and nfs, always run on TCP/UDP ports 111 and 2049 respectively. 

----------

In spite of those issues, I am moving forward with nfs because it seems to be my only option (due in part of gedit/cifs "bug")

---

