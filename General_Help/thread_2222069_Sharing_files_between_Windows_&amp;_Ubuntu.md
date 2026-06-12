---
title: "Sharing files between Windows &amp; Ubuntu"
date: 2014-05-05
forum: General Help
---

### Post by Shadius on 2014-05-05
Hey everybody,

I need help on how to set up file sharing between Windows & Ubuntu and possibly Mac.  My main priority is to be able to access files that are on my Ubuntu machine from my Windows machine and vice versa.  For right now, I'd prefer the easiest way then I'll start playing around with more advanced options if there are various ways of doing this.  

Thanks in advance.

---

### Post by MikeCyber on 2014-05-05
Well you can read from OSX as root. I've copied yesterday having two root nautilus windows open. On osx you can read ntfs so I do write on ntfs from Ubuntu myself and am fine. Probably you could mount rw ntfs on osx but I haven't bothered about that so far.

---

### Post by HermanAB on 2014-05-05
The easiest way is using FTP with FileZilla on Windows and Linux.  install the server on Linux and the client on Windows and Bob's your uncle.

---

### Post by Shadius on 2014-05-05
Is there a way of doing this through the network?  What I mean is, I thought this could be done by going to "Network" and I would see the computer there and I'd be able to open up that shared folder?

---

### Post by deadflowr on 2014-05-05
> **Shadius said:**
> Is there a way of doing this through the network?  What I mean is, I thought this could be done by going to "Network" and I would see the computer there and I'd be able to open up that shared folder?

Samba?

---

### Post by Shadius on 2014-05-06
I don't know if that's the equivalent to how Windows shares file, but how would I set it up?  What are my options here?

---

### Post by Shadius on 2014-05-06
> **HermanAB said:**
> The easiest way is using FTP with FileZilla on Windows and Linux.  install the server on Linux and the client on Windows and Bob's your uncle.

Downloaded FileZilla on Ubuntu and I'm totally lost on how to set it up. A little help?

---

### Post by christian23 on 2014-05-06
imho the best way is to set up samba on your Linux-Client, you can access the files through the network with \\LINUX-PC-NAME\SHARE, where share is a variable which you can change to your own needs.

---

### Post by Shadius on 2014-05-10
So I installed SAMBA on my Ubuntu 12.04 machine and it works great with my Windows Vista laptop.  I can share files between both computers.  

I tried setting SAMBA up on Ubuntu 14.04 to be able to share files over the network that is mostly Windows 7, but it doesn't work.  It keeps asking me for a password to the workgroup.  Help please!

---

### Post by Shadius on 2014-05-14
Sometimes I get this message **Unable to mount location.  Failed to retrieve share list from server**. Why am I getting this?

---

### Post by HiImTye on 2014-05-14
windows 7 disables SMB with servers who use keys of lesser strength. you need to [enable](http://www.dummies.com/how-to/content/changing-file-encryption-settings-on-a-windows-7-h.pageCd-storyboard,pageNum-5.html) the use of lesser strength keys.

---

### Post by dragonfly41 on 2014-05-31
My suggestion is to try opening a free account (up to 2GB) with spideroak. Then create a shared room.

[https://spideroak.com/](https://spideroak.com/)

---

### Post by SuperFreak on 2014-05-31
> **Shadius said:**
> So I installed SAMBA on my Ubuntu 12.04 machine and it works great with my Windows Vista laptop.  I can share files between both computers.  

I tried setting SAMBA up on Ubuntu 14.04 to be able to share files over the network that is mostly Windows 7, but it doesn't work.  It keeps asking me for a password to the workgroup.  Help please!

It should give the option of "remember password forever" or something like that  when you enter your password

---

### Post by Shadius on 2014-05-31
But there is no password for the workgroup.

---

### Post by SuperFreak on 2014-05-31
I am sorry if this not a very definite response, but try either your host computer's password, your client's password or your SAMBA password. I am not sure which it is but one will work. You did configure SAMBA and set up a password right?

---

### Post by Morbius1 on 2014-05-31
I really do try to keep out the samba part of this forum these days but .....

It's not clear from your posts who's doing what to who.
> I tried setting SAMBA up on Ubuntu 14.04 to be able to share files over  the network that is mostly Windows 7, but it doesn't work.  It keeps  asking me for a password to the workgroup.
You install the samba package to create a Samba server on the Linux box to share files to others on the lan. Has nothing to do with accessing some other machines shares. That subset of the samba suite is installed by default in Ubuntu. So who is getting the request for a password? The Windows machine when you access the Linux box? Or the Linux box when you access the Windows machine?

Oh and btw, does samba/smb itself work? Not this browsing stuff but samba itself:

From the Windows box open Run and see if you can access the linux samba server by ip address. For example:
```
\\192.168.0.100
```
From the Linux box access the Windows machine by ip address:
```
nautilus smb://192.168.0.101
```
If Windows won't display it's shares  it's likely because it has no idea who the hell your are. So pass a user name - not just any user name but one that exists on the Windows box - when you do the command. Something like this:
```
nautilus smb://morbius@192.168.0.101
```
Where morbius is an actual login user on the Windows box.

---

### Post by jdeca57 on 2014-05-31
Perhaps less obvious in setup, but very platform independent since it uses https is Owncloud. I use an Owncloud server and accessing it from Windows is either like Dropbox or via a browser. It's platform independent and Mac or Android is supported. And one avoids a proprietary and legacy protocol. Ok, it's a bit more work to get it started - mysql, apache, https - but once that's done it has a lot of advantages. (One of them being that that the password is clearly defined)

---

### Post by Morbius1 on 2014-05-31
Can't say enough good things about a good old fashion http server especially for large file transfers which choke just about every other protocol.

Never used OwnCloud but I use a temporary http server often by invoking the python module so there's no configuration and then copy stuff via a browser on the client. Easy peasy.

---

