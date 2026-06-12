---
title: "Ubuntu 12.10 - user=root?"
date: 2012-11-04
forum: General Help
---

### Post by felkar on 2012-11-04
By default, Ubuntu prevents users from activities that can destroy the OS; some operations that need "root" privileges automatically open an "authentication screen".  

What about the other operations? - e.g. "adding an entry in "/etc/fstab" so that I have the (user) option to mount other HD partitions into the "/mnt/directory" of my currently loaded OS?.

Not really an "Absolute Beginner's question"!  But I **am** an Absolute Beginner in **Ubuntu** and have to start somewhere.

felkar

---

### Post by duanedesign on 2012-11-04
Ubuntu by default has the root account locked. The root account does physically exist so it is possible to run programs with root level privileges. This is called Sudo in Ubuntu.

In the terminal use sudo for commands that requirre root privileges. Siimply prepend sudo to commands you would normally run as root. Ex.
```
gedit /etc/fstab 
```
You would run this as:
```
sudo /etc/fstab
```

I have been using Ubuntu for years and have never had any situation where I needed to enable the root account. Using sudo covers 99% of all use cases.

PLease read the following for more detailed info on sudo and how Ubuntu uses permissions. For an Ubuntu user this page is worth its weight in gold.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by DuckHook on 2012-11-04
Welcome to Ubuntu. This link

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

is a great introduction to *sudo* and *gksudo*. If you are coming from the Windows world, one of the best features of Ubunu/Linux is its better security, but such security is only effective if we do not seek to bypass it. Except for very rare circumstances that the average user is unlikely to encounter, it is a good idea to keep the root account inactive and use *sudo/gksudo* instead.

<edit> oops. forum staff beat me to the answer.

@duanedesign. You probably mean:

```
gksudo gedit /etc/fstab
```

---

### Post by Bucky Ball on 2012-11-04
> **duanedesign said:**
> You would run this as:
```
sudo /etc/fstab
```

No, you would run this:

```
gksudo gedit /etc/fstab
```If you wanted to use nano in a terminal rather than Gedit, you would use:

```
sudo nano /etc/fstab
```Be warned: Now you are root so anything you do will stick. Therefore, best to run this to copy the original file before you start:

```
sudo cp /etc/fstab /etc/fstab.bak
```Or whatever you'd like to call it. If things go pear-shaped:

```
sudo mv /etc/fstab.bak /etc/fstab
```Or you could just let Grub Customizer rewrite the fstab for you:

[http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183) :wink:

PS: sudo = super user do! So be careful with it.

---

### Post by felkar on 2012-11-05
My thanks to the three respondents, who took the time to send such a comprehensive reply.

Learning to invoke and use "sudo" will be a useful discipline.  My previous experience was with Debian - which was installed with the options to be either "user" or "root".

So, at least, I know the hazards of being "root".

felkar

---

### Post by Bucky Ball on 2012-11-05
This is the same. 'sudo' makes you root temporarily. Otherwise you're a user. You can log in as root but not wise. Ubuntu based on Debian.

---

### Post by felkar on 2012-11-05
> **Bucky Ball said:**
> This is the same. 'sudo' makes you root temporarily. Otherwise you're a user. You can log in as root but not wise. Ubuntu based on Debian.
The option to log in as "guest" is offered on the opening screen of Ubuntu 12.10.

"logging in" as "root" is not an obvious option for a "guest".  Which as probably a good thing!

Thank you for the advice

felkar

---

### Post by JKyleOKC on 2012-11-05
While it's possible to set Ubuntu up so that you can log in as root, it does require special preparation to do so -- and forum policy forbids any of us from telling you how to do it. However as others have said, there's really no need to do so since "sudo" and "gksudo" suffice for at least 99% of the needs for root. In my own experience, over the past five years with Xubuntu, the percentage has been 99.999999999% (and no, that infinitesimal probability that an occasion might rise where root is necessary is just to take care of Murphy's Law; I've never encountered such a situation and cannot envision one ever taking place).

---

### Post by drew3000 on 2013-03-02
i don't really think this solves it, sorry. I'm setting up a web development space on my system and it installs it in /var/www/ and if I want to make folders or edit files there it does say I need root access to do it, so I hae to log in as root just to make a folder or just to change a bit of code. Annoying. There must be some way to give my regular user account extra access to edit this area or I just need to be logged in as root.

> **JKyleOKC said:**
> While it's possible to set Ubuntu up so that you can log in as root, it does require special preparation to do so -- and forum policy forbids any of us from telling you how to do it. However as others have said, there's really no need to do so since "sudo" and "gksudo" suffice for at least 99% of the needs for root. In my own experience, over the past five years with Xubuntu, the percentage has been 99.999999999% (and no, that infinitesimal probability that an occasion might rise where root is necessary is just to take care of Murphy's Law; I've never encountered such a situation and cannot envision one ever taking place).

---

### Post by JKyleOKC on 2013-03-02
Your situation is exactly what the "group" permissions are intended to solve. You can use "sudo" to change the group permission for /var/www to be "rwx" (if it does not already have those permissions), and then use the "users and groups" utility (or a command line equivalent) to add yourself to the group that's listed for /var/www. Once you have done these two things, logged out, and logged back in, you will be able to modify that directory just logged in as yourself -- **without** having to expose the rest of the system to possible damage by logging in as root.

It's always better to use a system as it was designed to be used, rather than forcing it into an insecure imitation of a less versatile way of working...

---

