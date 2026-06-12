---
title: "How do i access my root/superuser?"
date: 2008-06-06
forum: General Help
---

### Post by raylistic87 on 2008-06-06
How do i access to my root or superuser account in the terminal?

---

### Post by lisati on 2008-06-06
It depends on what you want to do. The "root" account is usually disabled in Ubuntu as protection against accidents and other stuff which could hurt your system.

---

### Post by lisati on 2008-06-06
> **lisati said:**
> It depends on what you want to do. The "root" account is usually disabled in Ubuntu as protection against accidents and other stuff which could hurt your system.

Have a read of [[COLOR="Navy"]_this_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=765421")

---

### Post by NilsE on 2008-06-06
start the first command with sudo and it will prompt you for your password.  Use your login password.

example:

sudo fdisk -l 

If you want to run a gui application like gedit or nautilus start it with gksudo

Example:

gksudo nautilus

---

### Post by amingv on 2008-06-06
For most task the recommended method is:
```
sudo <command that must run as root>
```

But if by any reason you need a root console you can use:
```
sudo su
```
or
```
sudo -i
```

---

### Post by drs305 on 2008-06-06
> **raylistic87 said:**
> How do i access to my root or superuser account in the terminal?

Probably what you want is to gain access to administrator priviledges. To do that, preceed the command you want to run with "sudo" or with "gksudo" for graphical applications like gedit, nautilus, etc.

So if you want to install applications with apt-get, the command would be:
```
sudo apt-get **appname**
```

When you try to use sudo, it will ask for your password and when you type it in you won't see it but it is being registered. Hit enter after you have completed the password. By the way, only those with administrator priviledges can do this - normally if you are the first registered user on the computer you can use sudo.

---

### Post by raylistic87 on 2008-06-06
well, i would like to convert some .rpm files to .deb . How can i do that? 
And I face problems installing adobe reader now. It says i am using the wrong architecture but i am using the correct version i386. Any ideas:popcorn:?

---

### Post by drs305 on 2008-06-06
> **raylistic87 said:**
> well, i would like to convert some .rpm files to .deb . How can i do that? 
And I face problems installing adobe reader now. It says i am using the wrong architecture but i am using the correct version i386. Any ideas:popcorn:?

Install an app named **alien**

Then, to convert .rpm to .deb: 
```
sudo alien -k /path/name-of-rpm-file
```

---

### Post by raylistic87 on 2008-06-06
I keep having this error when i want to install packages. 

Error : wrong architecture 'i386'

Is there a bug somewhere? Cause i seriously think mine is the i386. 

I am trying to install adobe reader and skype for ubuntu.

---

### Post by Gripp on 2008-06-06
i think that warrants its own post. 

better to attract those people who know.

---

### Post by drs305 on 2008-06-06
> **raylistic87 said:**
> I keep having this error when i want to install packages. 

Error : wrong architecture 'i386'

Is there a bug somewhere? Cause i seriously think mine is the i386. 

I am trying to install adobe reader and skype for ubuntu.

```
uname -m
```

If it returns "**x86_64**" you are running a 64-bit system. There is a separate conference for that.

As was mentioned, it is probably time for a new thread about this issue.

---

### Post by xebian on 2008-06-06
> **raylistic87 said:**
> I keep having this error when i want to install packages. 

Error : wrong architecture 'i386'

Is there a bug somewhere? Cause i seriously think mine is the i386. 

I am trying to install adobe reader and skype for ubuntu.

Can you post the results of thi command

```

uname -a 

```

---

### Post by raylistic87 on 2008-06-06
Linux raylistic-desktop 2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008 x86_64 GNU/Linux

---

### Post by drs305 on 2008-06-06
> **raylistic87 said:**
> Linux raylistic-desktop 2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008 x86_64 GNU/Linux

You are trying to install a 32-bit app (i386) on a 64-bit system. It can be done but there are probably better options. Again, this is better addressed in the [64-bit Forum]("http://ubuntuforums.org/forumdisplay.php?f=343").

---

### Post by raylistic87 on 2008-06-06
thanks, i did not know that.

---

### Post by xebian on 2008-06-07
> **raylistic87 said:**
> Linux raylistic-desktop 2.6.24-18-generic #1 SMP Wed May 28 19:28:38 UTC 2008 x86_64 GNU/Linux

You should get the 64bit version - usually has x86_64 on their name, of the rpm file.  

Then with alien command option -i ( will install directly)

```

sudo alien -i app_name.rpm

```

If you don't have the 64 bit, it can be forced. However, you need 32bit supporting libs.  IF you installed flashplugin-nonfree from the repo, then you should be ok.

First create a deb file. 
```

sudo alien app_name.rpm  ##<-- will create a deb file

#install the deb file
dpkg -i --force-architecture app_name.deb


```

---

### Post by raylistic87 on 2008-06-09
You mean i can force all the 32 bit softwares onto the 64 bit Ubuntu?

---

### Post by N J Krishnan on 2008-06-10
Help!!

I am a new user of Ubuntu and I find that while I can log in and work on any function within th OS I am unable to do any administration function - the password  used at login is not being accepted. How do i get through?

regards

Krishnan

---

### Post by raylistic87 on 2008-06-10
type sudo in the terminal
and they will prompt for your password.
After which you will become the superuser which u can do admin stuff.

---

### Post by xebian on 2008-06-10
> **raylistic87 said:**
> You mean i can force all the 32 bit softwares onto the 64 bit Ubuntu?

Absolutely.  But only when there's no 64-bit version.

---

