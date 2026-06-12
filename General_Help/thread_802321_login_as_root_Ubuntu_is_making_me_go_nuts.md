---
title: "login as root Ubuntu is making me go nuts"
date: 2008-05-21
forum: General Help
---

### Post by foxofinfinety on 2008-05-21
I have a big problem every time I want to do some ting I always have to give the administrator password but I want to be able to access everything I want to on _**my**_ computer
in other words I don't want to give a password every time I want to do something I want to have the rights _as soon as I login_
it's my PC why should I give a password just to copy a a image file to use as a boot screen? I shouldn't!!

---

### Post by aroch1 on 2008-05-21
This kind of permission stuff is set up to make sure no normal users mess with the operating-system essential files.  If a malicious user were to gain access to your system as a regular user, it prevents them from doing much of anything to harm your overall system (your personal data is a different story) without the root password.

If you don't want to have to do this, take the following steps *AT YOUR OWN RISK*:

1. Give your root account a password;

```
sudo passwd root
```

2. Enable root login:

Settings->Administration->Login Window

Go to the "Security" tab, and select the "Allow local system administrator login" option.

3. Log out and log in as user "root" using the password you gave the root acount in step 1

4. Be VERY careful about anything you do outside of /home from now on, because a simple mistake (like rm -rf ...) can kill your entire system without asking you for confirmation.

---

### Post by foxofinfinety on 2008-05-21
> **aroch1 said:**
> This kind of permission stuff is set up to make sure no normal users mess with the operating-system essential files.  If a malicious user were to gain access to your system as a regular user, it prevents them from doing much of anything to harm your overall system (your personal data is a different story) without the root password.

If you don't want to have to do this, take the following steps *AT YOUR OWN RISK*:

1. Give your root account a password;

```
sudo passwd root
```

2. Enable root login:

Settings->Administration->Login Window

Go to the "Security" tab, and select the "Allow local system administrator login" option.

3. Log out and log in as user "root" using the password you gave the root acount in step 1

4. Be VERY careful about anything you do outside of /home from now on, because a simple mistake (like rm -rf ...) can kill your entire system without asking you for confirmation.
I don't want to login as root I want my account to have administrator rights

---

### Post by kerry_s on 2008-05-21
use windows if you want that kind of hole.

[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

---

### Post by lespaul_rentals on 2008-05-21
> **foxofinfinety said:**
> I don't want to login as root I want my account to have administrator rights

Please read up on what "root" and "administrator" means.  I don't think you understand the concepts behind it.  This isn't Windows.

This page will tell you all about it:

[http://en.wikipedia.org/wiki/Root_user](http://en.wikipedia.org/wiki/Root_user)

---

### Post by bingoUV on 2008-05-21
Read this. [http://www.ducea.com/2006/06/18/linux-tips-password-usage-in-sudo-passwd-nopasswd/](http://www.ducea.com/2006/06/18/linux-tips-password-usage-in-sudo-passwd-nopasswd/) Simple how-to. You will not log in as root, but sudo will not ask for a password. Of course, this is also unsupported and unrecommended.

---

### Post by xeth_delta on 2008-05-21
> **foxofinfinety said:**
> I don't want to login as root I want my account to have administrator rights

That is exactly one of the reasons why Linux systems are much safer than Windows systems, for example. It is based on a different administration model that seems to have proven more efficient and secure over time.

That said, it is **not recommended at all** to run every single application as root/administrator, only tasks that require administrative privileges. For example, if some malicious code is downloaded or executed by a regular user, it will affect at the most his/her own directory, leaving the rest of the system intact. I think that this is quote a good idea. The same goes for preventing a regular user from damaging the system, after all it is the administrator account owner who has to be able to do that. By theway, Mac OSX uses the same pricnciple as Ubuntu. 

If you want to run a GUI file manager as root, you could for example execute from a terminal:
```
gksudo nautilus
```
or any other file manager.

I hope that this has been clear enough, and if you have further questions feel free to ask.

---

### Post by foxofinfinety on 2008-05-21
I was actually looking for something simple and there are word there I don't even know (I'm dutch and still learning English)

I just want to paste 3 image's in a folder
and make 2 others
but I can't

---

### Post by drs305 on 2008-05-21
There is also a way to extend the timeout between password requests by editing the sudoers file. Security is reduced, but it might be what you are looking for. More details if you want them.

---

### Post by xeth_delta on 2008-05-21
> **foxofinfinety said:**
> I was actually looking for something simple and there are word there I don't even know (I'm dutch and still learning English)

I just want to paste 3 image's in a folder
and make 2 others
but I can't

The part of the file system that is normally reserved for users is **/home/user_name**, where user_name is your log-in user name. You can create without worries sub-directories/folders in there. Most of the rest of the file system is restricted for regular accounts, with the exception of /tmp and probably /var/tmp. There might probably be others, but I don't recall right now.

What exactly are you trying to do? Maybe we can help.

---

### Post by xArv3nx on 2008-05-21
> **foxofinfinety said:**
> I was actually looking for something simple and there are word there I don't even know (I'm dutch and still learning English)

I just want to paste 3 image's in a folder
and make 2 others
but I can't
Type in a terminal "sudo nautilus" and do what you must. BE EXTREMELY CAREFUL.

---

### Post by cdtech on 2008-05-21
type "sudo -u" for temporary user as root until you exit terminal. You'll be able to do what ever you need in terminal. You could add your user to the root group "sudo useradd -G root user", this is what I did.

---

### Post by EndPerform on 2008-05-21
> **foxofinfinety said:**
> I was actually looking for something simple and there are word there I don't even know (I'm dutch and still learning English)

I just want to paste 3 image's in a folder
and make 2 others
but I can't

Where are you trying to put the images, and where are you trying to make folders?  You should be able to do those things just fine in your home directory.

---

### Post by xeth_delta on 2008-05-21
> **xArv3nx said:**
> Type in a terminal "sudo nautilus" and do what you must. BE EXTREMELY CAREFUL.

+1 Be extremely careful, as you could end up damaging your OS setup if you do something wrong. Ask in the forums if in doubt.

---

### Post by yogo on 2008-05-21
> **foxofinfinety said:**
> I was actually looking for something simple and there are word there I don't even know (I'm dutch and still learning English)

I just want to paste 3 image's in a folder
and make 2 others
but I can't


it is an extra step, but I do not think for what you are wanting to do, is that much.

Just use the gksu nautilus and copy those three images to where you want them. it will take you a few extra seconds but then you will have your boot images.

---

### Post by Exsecrabilus on 2008-05-21
> **foxofinfinety said:**
> I have a big problem every time I want to do some ting I always have to give the administrator password but I want to be able to access everything I want to on _**my**_ computer
in other words I don't want to give a password every time I want to do something I want to have the rights _as soon as I login_
it's my PC why should I give a password just to copy a a image file to use as a boot screen? I shouldn't!!
You might as well just switch back to Windows than complain about one of Linux's best security features.

---

### Post by foxofinfinety on 2008-05-21
> **xeth_delta said:**
> The part of the file system that is normally reserved for users is **/home/user_name**, where user_name is your log-in user name. You can create without worries sub-directories/folders in there. Most of the rest of the file system is restricted for regular accounts, with the exception of /tmp and probably /var/tmp. There might probably be others, but I don't recall right now.

What exactly are you trying to do? Maybe we can help.

I found information on how to make Ubuntu look like Mac OS X ( see [http://sourceforge.net/projects/mac4lin](http://sourceforge.net/projects/mac4lin) )
only I have to paste files in a directory I can't paste in

---

### Post by justin whitaker on 2008-05-21
> **foxofinfinety said:**
> I don't want to login as root I want my account to have administrator rights

No, you don't. What you want to do is extend the timeout on admin privileges...giving your account full root access is just asking for trouble.

---

### Post by kellemes on 2008-05-21
> **foxofinfinety said:**
> I found information on how to make Ubuntu look like Mac OS X
only I have to paste files in a directory I can't paste in

```
gksudo nautilus
``` to open your filemanager (nautilus) with root privileges, now you can drag/drop as much as you want.

---

### Post by aysiu on 2008-05-21
This thread is making me go nuts.

Read the sticky:
[Forum policy on log-in-as-root tutorials](http://ubuntuforums.org/showthread.php?t=765414)

---

