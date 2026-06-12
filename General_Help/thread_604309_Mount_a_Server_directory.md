---
title: "Mount a Server directory"
date: 2007-11-06
forum: General Help
---

### Post by Mongo5000 on 2007-11-06
So I have a network file server and I want to mount it so my ubuntu box can access it.

I have used the "Connect to server" and it works, but applications can't see it.  I read the stuff on [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Mounting_Automatically](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Mounting_Automatically) but its a bit over my head.

How can I mount the server so my applications can access it?  Or at least where is it mounted?

---

### Post by Mongo5000 on 2007-11-07
anybody?

---

### Post by mahousaru on 2007-11-07
What protocol are u trying to mount it with?

If you use Places, Network to access the network share, then not all programs can see it, as it uses Gnome VFS.  For example Thunderbird and XMMS don't see network shares.  You can get around this problem by manually mounting your shares to a directory.

---

### Post by Mongo5000 on 2007-11-07
> **mahousaru said:**
> What protocol are u trying to mount it with?

If you use Places, Network to access the network share, then not all programs can see it, as it uses Gnome VFS.  For example Thunderbird and XMMS don't see network shares.  You can get around this problem by manually mounting your shares to a directory.

Yeah, thats exactly what im running into.

Basically I want to store my Thunderbird share, music, etc on my NAS.  But like you said, Thunderbird, Exaile, and other apps can't see it.

Its a mybook world edition 2 and it runs on linux.  I used the places selection but trying to figure out how to auto mount it.

Just can't figure it out.  Tried that guide but ran into more problems than I wish to tackle.  Mybook is at 192.168.1.104.

---

### Post by mahousaru on 2007-11-07
Hmm typical I had a look at a few reviews and not one said what protocol it uses to share.

You can get around your problem by either mounting it in fstab or mounting it with with a script.  Personally I use a script as my laptop goes to lots of different locations and I like a finer control over what I attempt to connect to, but either way is good and it is up to your personal preference.

Before you start can u browse to one of the shares, right click on it and go properties.

The type and location should give away what protocol it is using to share and then we can make up some fstab lines or a script to mount the share in a directory so the gnome unfriendly programs can deal with it.

Also you need to decide how much of it you wish to mount on the network.  For example you might want to mount your whole home directory, personally I just mount stuff under a directory under my home dir called network.  That way when i don't have access to my share I can still work normally (remember that I use a lappy).

---

### Post by Mongo5000 on 2007-11-07
Thanks for the help :)

So im trying to mount my directory with all my music in it.  The Location says "smb://mybookworld/PUBLIC" and the type is just a folde.

I tried mounting it in fstab but it just gave errors which led me to that link in my first post.  I do have a script that allows me to mount and unmount at will but would like it to auto mount at startup.

---

### Post by skathrein on 2007-11-07
Here&#8217;s how I&#8217;ve done it (as long as your network directory is sharing by using smb, then the following should work):

First, so I&#8217;m not confusing, I&#8217;ll refer to the folder that you want to share as your network server and your &#8220;ubuntu box&#8221; as your laptop.  I&#8217;ll assume you want to use the same &#8220;Public&#8221; name on your laptop.  

So first, you need to set a mount point on your laptop, so run the following command:
```
sudo mkdir /media/Public
```

Then edit fstab by adding the following line:
```
//mybookworld/PUBLIC	/media/Public	smbfs	defaults,users,dmask=777,fmask=777   0  0
```

After you have edited and saved fstab, reboot, or simply run the following:
```
sudo mount -a
```

I&#8217;m sure some will disagree with me about adding the dmask and fmask options, but this is how I do it and it works.  The problem that I next ran into was making sure I had full access (i.e. read, write, execute) to all the files on my server, but you may have already configured this through smb.conf.  If not, let me know.

---

### Post by Mongo5000 on 2007-11-08
> **skathrein said:**
> Here’s how I’ve done it (as long as your network directory is sharing by using smb, then the following should work):

First, so I’m not confusing, I’ll refer to the folder that you want to share as your network server and your “ubuntu box” as your laptop.  I’ll assume you want to use the same “Public” name on your laptop.  

So first, you need to set a mount point on your laptop, so run the following command:
```
sudo mkdir /media/Public
```

Then edit fstab by adding the following line:
```
//mybookworld/PUBLIC	/media/Public	smbfs	defaults,users,dmask=777,fmask=777   0  0
```

After you have edited and saved fstab, reboot, or simply run the following:
```
sudo mount -a
```

I’m sure some will disagree with me about adding the dmask and fmask options, but this is how I do it and it works.  The problem that I next ran into was making sure I had full access (i.e. read, write, execute) to all the files on my server, but you may have already configured this through smb.conf.  If not, let me know.

Thanks for the help but sadly, this didn't work.

mount: wrong fs type, bad option, bad superblock on //mybookworld/PUBLIC,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I already do have read/write access to it though

---

### Post by mahousaru on 2007-11-08
Check that you have smbfs installed

you can check with System, Administration, Symnaptic Package Manager

---

