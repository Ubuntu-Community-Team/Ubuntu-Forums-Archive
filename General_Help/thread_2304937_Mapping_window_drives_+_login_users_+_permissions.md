---
title: "Mapping window drives + login users + permissions"
date: 2015-12-01
forum: General Help
---

### Post by pag2 on 2015-12-01
Dear All,

The task is as follows:

- enable users to log in via Ubuntu Mate machine using their username and password to windows domain
- after they log in they should have access to mapped drives they have permission to access

There are three types of users; A users that have access to A: drive and P: public drive, B users that have access to B: drive and P: public drive and C users that have access to drives A:, B: and P:.

So far users can log in to domain via Ubuntu Mate machine but they do not see the drives by logging in. 
As user with "admin rights" I can map/mount drives using .smbcredentials and modifying fstab but in the same way for all users (permissions etc. are not applied).

I imagine that solution could be reached if I could make something along the following lines:
- User logs in
- drives are mapped/mounted through modified fstab file where it says what to map/mount and what credentials to read
- in his home folder there is .smbcredential file with his username and password
- user has those drives mapped that he has written in his fstab

What I don't know is whether fstab file is only one on machine or there can be one for each user. Same for .smbcredentials.

Thank you for your help!

---

### Post by bab1 on 2015-12-01
> **pag2 said:**
> Dear All,

The task is as follows:

- enable users to log in via Ubuntu Mate machine using their username and password to windows domain
- after they log in they should have access to mapped drives they have permission to access

There are three types of users; A users that have access to A: drive and P: public drive, B users that have access to B: drive and P: public drive and C users that have access to drives A:, B: and P:.

So far users can log in to domain via Ubuntu Mate machine but they do not see the drives by logging in. 
As user with "admin rights" I can map/mount drives using .smbcredentials and modifying fstab but in the same way for all users (permissions etc. are not applied).

I imagine that solution could be reached if I could make something along the following lines:
- User logs in
- drives are mapped/mounted through modified fstab file where it says what to map/mount and what credentials to read
- in his home folder there is .smbcredential file with his username and password
- user has those drives mapped that he has written in his fstab

What I don't know is whether fstab file is only one on machine or there can be one for each user. Same for .smbcredentials.

Thank you for your help! 
Is the "Windows Domain" and shared directories hosted by a Windows server?  Why do you feel you need to use the fstab file to "map drives"?    The typical method to mount shares is to use the GUI gvfs system using a Linux GUI desktop.  A step further would be to use autofs with the GUI.  Mounting a SMB/CIFS share via fstab is a bad thing.  It causes all kinds of shutdown problems.  In addition, the mount of a share vis fstab is done at boot time.  This is before any user logs in.  The mount is for all users.

Certainly you can configure private, semi-private and public shares.  The answer as to how really depends on whether you are using a Windows server and Linux clients or a Linux server and either Windows of Linux clients.

---

### Post by pag2 on 2015-12-01
Thank you for your answer.

Yes.

I don't feel. This approach is the one that the most often pops up when you type: "map drives ubuntu windows" in google.

Your description of the typical method is difficult for me to follow because my knowledge is two weeks old and based on the answers I find online.

I am using Windows server and mainly windows clients. We are trying to use Ubuntu to keep alive some older machines that have XP installed.

It would be nice to have a step by step guide how to make Ubuntu machine capable of handling existing users as described above.

---

### Post by bab1 on 2015-12-01
> **pag2 said:**
> Thank you for your answer.

Yes.

I don't feel. This approach is the one that the most often pops up when you type: "map drives ubuntu windows" in google.

Your description of the typical method is difficult for me to follow because my knowledge is two weeks old and based on the answers I find online.

So what you're saying is that you found all this non-vetted information on the Internet that you believe is correct.  But you don't really know because you don't have enough experience using Samba.

I ran the same search and came up with just as many sites that don't even mention fstab at all.   Two interesting links would be:
  [**[http://mixeduperic.com/linux/how-to-map-windows-nework-drive-in-linux-gnome-2-gnome-3-and-unity.html#gnome3](http://mixeduperic.com/linux/how-to-map-windows-nework-drive-in-linux-gnome-2-gnome-3-and-unity.html#gnome3)**]("http://mixeduperic.com/linux/how-to-map-windows-nework-drive-in-linux-gnome-2-gnome-3-and-unity.html#gnome3")

  [**[http://superuser.com/questions/145191/how-do-i-map-a-drive-network-share-using-the-linux-terminal](http://superuser.com/questions/145191/how-do-i-map-a-drive-network-share-using-the-linux-terminal)**]("http://superuser.com/questions/145191/how-do-i-map-a-drive-network-share-using-the-linux-terminal")

Be careful.  Linux is constantly being upgraded with no backwards compatability.  These links provide the basics, but are not current (less than 6 months old).  Things change a lot so you have to stay current to understand the changes.  For example the old _smbfs_ package is now_ cifs-utils_.

The bottom line is that you can mount the share using fstab, but you will have to deal with the problems shutting down.  The system will hang as the SMB share will not gracefully unmount.  It wasn't designed to unmount that way.  The routine to gracefully unmount is part of the GNOME Virtual File System (gvfs) used by most Linux GUI Linux Desktops.
> 
I am using Windows server and mainly windows clients. We are trying to use Ubuntu to keep alive some older machines that have XP installed.

It would be nice to have a step by step guide how to make Ubuntu machine capable of handling existing users as described above.
There is no guide to set up an Ubuntu or Debian machine for a Windows AD-DC environment.  There are guides for integrating Ubuntu workstations into an AD-DC network.  You indicated that you are already using AD to authenticate the Ubuntu logins.  Is this so?  How do you know that Ubuntu is not using local user logins (/etc/passwd). What I'm saying here is that there are multiple areas of system administration that you need to know to put this all together so there is no one tutorial for what you want to do.

The mounting of shares I described in the last post and the above links can be implemented by **browsing for a share** (see my first link) **and opening it **.  You can bookmark it if you wish, but that is not important.  I don't bookmark my shares.  I just browse for them when I need to mount them to the local file system (map a drive) by clicking on the shared folder.

If you can't see the shares when browsing the network then the Windows Server needs to have NetBIOS over TCP activated.  The Latest Windows Servers use Active Directory (AD) instead of NetBIOS.  As far as I know the Samba (SMB/CIFS) client does not use AD to resolve NetBIOS names.

All of this boils down to using fstab plus the direct IP address to locate the share and mount it (/IP_Address/SHARE) or GUI browsing for the share which you have to set up.  After 20+ years of doing this kind of thing, I find the users prefer to browse for the shares they need.

---

### Post by pag2 on 2015-12-03
> So what you're saying is that you found all this non-vetted information  on the Internet that you believe is correct.  But you don't really know  because you don't have enough experience using Samba.

Yes.

> How do you know that Ubuntu is not using local user logins (/etc/passwd).

When I look in users on machine in question there are no "defined" users other than user who installed the system. Yet, everyone can log-in with credentials normally used on windows machines. We do not login locally to computers. Our data is on server and we need this to be seamless. 

> All of this boils down to using fstab plus the direct IP address to  locate the share and mount it (/IP_Address/SHARE) or GUI browsing for  the share which you have to set up.  After 20+ years of doing this kind  of thing, I find the users prefer to browse for the shares they need.

I see your point with browsing for shares, but this is not how we want to work. If there is a way to log-in and have your usual drives mapped, that would be acceptable. When I think about what computer systems are capable of today and what kind of advanced knowledge is available it is almost unbelievable that a simple business case like this one doesn't have a simple applicable solution.

Is there a way to set this up using fstab?

---

### Post by bab1 on 2015-12-03
> **pag2 said:**
> When I think about what computer systems are capable of today and what kind of advanced knowledge is available it is almost unbelievable that a simple business case like this one doesn't have a simple applicable solution.

Welcome to the world of Free and Open-Source Software ([**FOSS**]("https://en.wikipedia.org/wiki/Free_and_open-source_software")).  Most of the emphasis is on server or back end applications and cutting edge development.  All the work is done by volunteers.   There is no centralized management of software development like there is at Microsoft or Apple. The desktop does not generally have a strong interest with Linux developers  as there is with Apple or Microsoft.  The only FOSS development incorporating SMB/CIFS is the Gnome project,.

Most distros that integrate SMB/CIFS into the desktop use GNOME libraries (GIO or the later gvfs) with whatever GUI interface that is used.  For example Ubuntu Mint is really Ubuntu using Gnome2 (GTK2) for a desktop rather than Gnome 3 (GTK3).  All of this means you will be using gvfs to mount (and unmount) any Windows share the user needs access to.
> 
I see your point with browsing for shares, but this is not how we want to work. If there is a way to log-in and have your usual drives mapped, that would be acceptable.  Is there a way to set this up using fstab?
The /etc/fstab file is really just the configuration file for the **mount ** command.  The mount command is always used to mount all file systems to the root file system (/).  This can be a local file system (local to the host on a separate partition or device) or a remote file system on a separate host (e.g. your Windows server)  The bottom line is that you will always need to invoke the mount commad with what you want to do.

The most convenient method (for both you and the user) is to use the available gvfs libraries to mount (make available) and map (activate) the Windows shares available.  

If you want, this can be scripted.  This also does not use a line in fstab.  The terminal command to mount a share via gvfs is this```

gvfs-mount smb:/<server>/<share>

```...where <server> is your server's IP address and the <share> is the share name.  The command is the same as using the GUI to map the share.  The   script is executed last, so the host will not hang booting up if the server is unavailable or hang when shutting the host down.  The rub is; you get to create the script and integrate it into the boot up sequence for each machine.  You could also activate the script via a clickable link.  But why do that, might as well just use what is already available on your desktop (Browse Network).  Why reinvent the wheel?

You can install a desktop application named ***[gigilo]("http://www.ubuntugeek.com/gigolo-frontend-to-manage-connections-to-remote-filesystems-using-giogvfs.html")*** which gives you the same functionality as what is already available with MATE but in a separate package.  It also has the ability to save mapped drive settings with a bookmarking system.   This is not as invisible as a script but it achieves the same end result.

It is also possible to mount the SMB/CIFS share using direct mount commands in the terminal (or a script) that does not use fstab.  For example```

sudo mount -t cifs //server/share  /path/tomount_point  -o <mount options
```  This is useful if you have applications that need special considerations.  For example Libre Office needs to have the **nobrl** (no byte range lock) set.  I have a share that uses this so I have a script to mount that share.  The user needs to click on the icon to mount the share and unmount the share in this case.

You can mount the Windows shares via fstab, but you will quickly find that you will need to script the mount and dismount of the shares to wrap the basic insufficiencies that are inherent with using fstab to configure the mount command.  I can't see why you would want to go to all that trouble given that Gnome has already supplied the libraries to do exactly that (mount and unmount the share gracefully).  

So there you have it.  five methods you can use to map Windows shares.  The method you use is up to you.  What works for you may not work for others.  This is the Linux way.

---

### Post by pag2 on 2015-12-04
Dear bab1 thank you very much. 

As the poet sings: "It was clear as mud, but it covered the ground, and the confusion made me brain go 'round".

I will study this further.

---

### Post by bab1 on 2015-12-04
> **pag2 said:**
> Dear bab1 thank you very much. 

As the poet sings: "It was clear as mud, but it covered the ground, and the confusion made me brain go 'round".

I will study this further.
Please ask questions.  Anything that isn't clear we can talk about.  That's how we all learn.

---

### Post by pag2 on 2015-12-04
OK... I have looked into it.

Gigolo with bookmarks is something I can use. I mapped 4 drives for one user, put it into startup so it starts after boot (delay is not working but I can live with this)

How do I make a script or something else that will connect drives, create bookmark for every drive when a new user logs in to a computer?

---

### Post by bab1 on 2015-12-04
> **pag2 said:**
> ... Gigolo with bookmarks is something I can use. I mapped 4 drives for one user, put it into startup so it starts after boot (delay is not working but I can live with this).
> This may end up what you finally use.  Did you try and mount the drives using Nautilus (file manager) and bookmarking them directly?  Why is Gigolo preferable considering both do exactly the same thing in exactly the same way?  
How do I make a script or something else that will connect drives, create bookmark for every drive when a new user logs in to a computer?
I have played with various scripts to mount the shares.  None of them will do the bookmarking function.  It turns out that there are changes to the Gnome that create problems scripting transparent mounting of any shares.  Unfortunately the only way to suppress gvfs-mount from asking for a password is to load the password in the Gnome keyring.  In addition the script is useless until the user logs in.  The script needs to know who the user is (the variable $USER).

Given that the use will always have to interact with the system (via clicking on icons and possibly using a password), the Gigolo app or directly using Nautilus to bookmark the share is really the best method.

The script I have used has no error trapping but will work from the command line.  It really is only 1 line plus the header```

#! /bin/bash

gvfs-mount smb://<server>/<share>
```

Sorry this did not work out.  I had hoped to use the script myself as it automagically mounts the share with the correct user permissions without having to explicitly declare that user.  Even with the share configured with guest access I still get a dialog box interrupting the script. 

You might take a look at the [**Gnome2 admin guide**]("https://help.gnome.org/admin/system-admin-guide/2.32/").

---

