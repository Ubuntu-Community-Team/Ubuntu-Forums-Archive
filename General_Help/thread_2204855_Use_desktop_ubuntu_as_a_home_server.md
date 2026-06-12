---
title: "Use desktop ubuntu as a home server?"
date: 2014-02-10
forum: General Help
---

### Post by marrjam on 2014-02-10
Greetings,

I'm using Windows 8 as a home server on an ssd with 4 separate HDDs (extended) and can access this machine from 3 other Win/Mac machines.  I'm not a network person, just figured out how to do the "share" thing in windows.

I'd like to try this with Ubuntu.  Can I install Ubunbtu on the ssd and "share" the 4 ntfs hard drives?  Do I have to format them to ext4?

Hope this makes sense.

Thanks, Mark

---

### Post by tfrue on 2014-02-10
You can do that in Ubuntu without formatting them as ext4, though I recommend using Ubuntu Server since you can install Samba during installation.

With Samba, you define share and set options, like authentication and permissions, and share your defined shares on your LAN.

But I will go over a generic install, first we will need to install Samba, then edit the config file, then restart the Samba services and we should be good!

First, type:
```
sudo apt-get install samba
```
Let it finish installing and then we will need to edit the config file, so type:
```
sudo nano /etc/samba/smb.conf
```
Scroll all the way to the bottom and type:
Don't type the text in the parenthesis.
```

[NewShare]
comment= My New Share
path= /path/to/directory (Can be any path, ex. /home/chris/share)
browseable= yes
writeable= yes
guest ok= yes
read only= no
```

Press "ctrl+x", and possibly type "yes" if it ask, to save the file.

That will make an open share that anyone can access and put/take anything from it. We can lock it down and make it more secure if you want, just let me know and I will show you how to do that.

Now we need to restart the samba service, type:
```
sudo service smbd restart

and

sudo service nmbd restart
```

That should get you up and running with a Samba defined share that anyone can access when they connect to your LAN, let me know if you have any troubles and I will help!

Good luck,
Chris

---

### Post by marrjam on 2014-02-11
Wow, that is pretty clear, at least for now, I'll come back when I actually start doing it for details.

Is Ubuntu Server gui or command line?  Too complicatied for a non-network person like me?

Many thanks, Mark

---

### Post by tfrue on 2014-02-11
There is a GUI version, but I've never used it since I'm more comfortable with the CLI. The nice thing about the CLI is that it's straight forward, what you type is what you get.

The reason it seems complicated is because there is a plethora of things you can do with the CLI, not only with Samba, but many other applications that you configure to suit your needs.

---

### Post by ant2 on 2014-02-11
I have a Ubuntu box that has a NTFS HDD that contains all my media files. It has a samba share for the NTFS HDD that can be connected to by my Mac, a Lubuntu laptop and a Windows box. As the Ubuntu box is also the main family computer it has the regular Ubuntu Desktop version installed.

---

### Post by deadflowr on 2014-02-11
> **marrjam said:**
> 
Is Ubuntu Server gui or command line?  Too complicatied for a non-network person like me?

Many thanks, Mark

The server edition is command line.
You have to DIY a gui.


But beside that, you probably are going to want to have those ntfs partitions mounted at startup.
Here are two links to help get you understanding in how to do that
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

Otherwise you would have to mount them whenever the machine boots up, or else the shares wouldn't be available through samba.
None of this is overly complex, and once it's setup you'll probably never have to touch it again.

---

### Post by tfrue on 2014-02-11
> **ant2 said:**
> I have a Ubuntu box that has a NTFS HDD that contains all my media files. It has a samba share for the NTFS HDD that can be connected to by my Mac, a Lubuntu laptop and a Windows box. As the Ubuntu box is also the main family computer it has the regular Ubuntu Desktop version installed.

It's not server specific, it's easier to install Samba with the server version since you can install it during installation rather than having to use a package manager to download the software.

Here is documentation on Samba v3, I believe:
[http://www.samba.org/samba/docs/using_samba/toc.html](http://www.samba.org/samba/docs/using_samba/toc.html)

---

### Post by ant2 on 2014-02-11
> **tfrue said:**
> It's not server specific, it's easier to install Samba with the server version since you can install it during installation rather than having to use a package manager to download the software.

Here is documentation on Samba v3, I believe:
[http://www.samba.org/samba/docs/using_samba/toc.html](http://www.samba.org/samba/docs/using_samba/toc.html)

Yes I realise that. It's just that the Ubuntu box was, and still is, being used as a family PC before I started sharing the media drive with other computers on the Local Network. So, I agree if the Ubuntu box was being set up solely to be a home server then the server version is best.

---

### Post by tfrue on 2014-02-12
Ant 2, I see.

Also, I agree with deadflower about mounting the drives at boot since they will not automatically mount at boot. Another help page is:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

I go back to this page as it's straight to the point about setting up the /etc/fstab file.

Chris

---

### Post by mastablasta on 2014-02-12
there is also GUI server interface. a couple of them actually. zentyal, webmin or storage server OS called Openmediavault (debian based).

no need to format NTFS, but you will probably have to set automount. i too use NTFS os rapsbery pi as it has external disk so if needed i can just move the drive to windows mashcine and copy files via USB :-)

---

### Post by 3rdalbum on 2014-02-12
It's actually easy on Ubuntu Desktop.

Install the system-config-samba package. It includes a GUI configuration utility named simply Samba, and also pulls in the Samba server packages as a dependency. Run the Samba program and set up your network share(s) using that. Easy, no command line needed!

---

