---
title: "About root passwd"
date: 2024-03-17
forum: General Help
---

### Post by satimis on 2024-03-17
Hi all,

I forgot root password

On Terminal I couldn't enter root running```

$ su -

```

Can I create a new root passwd on Terminal again running```

sudo passwd root

```

Thanks

Regards

---

### Post by yancek on 2024-03-17
The root user is locked by default in Ubuntu and the command you posted will ask for the password for the primary user you set up when you installed.  Do did you actually enable the root user account or is it the primary user password you lost?

---

### Post by ajgreeny on 2024-03-17
There is a wiki about **root-sudo** which you can get to from my signature below.
As you will see it does need some updating but the majority of its content is still relevant and certainly worth reading.

As you have been here and using Ubuntu since 2006 I am amazed that you even have to ask this question. How have you managed to use the OS and carry out all the activities that need root permissions, ie **sudo command** without knowing already that there is no root account in Ubuntu.
Actually, there is a root account but there is no reason to use it so Ubuntu developers decided many years ago to disable it and use sudo in its place.

---

### Post by satimis on 2024-03-18
> **ajgreeny said:**
> There is a wiki about **root-sudo** which you can get to from my signature below.
As you will see it does need some updating but the majority of its content is still relevant and certainly worth reading.

As you have been here and using Ubuntu since 2006 I am amazed that you even have to ask this question. How have you managed to use the OS and carry out all the activities that need root permissions, ie **sudo command** without knowing already that there is no root account in Ubuntu.
Actually, there is a root account but there is no reason to use it so Ubuntu developers decided many years ago to disable it and use sudo in its place.
Thanks for your advice.

All times I ran "sudo" for management without problem.

It is just a curiosity on reading online threads that all advices running as root # NOT sudo.  I try to follow but unfortunately I forgot the root password. That is the complete story.  I recall that there is a way changing root password.  I haven't used it for prolonged time.  I suppose it can be found on searching.

Regard

---

### Post by Rubi1200 on 2024-03-18
Are you able to use **sudo **without any issues, meaning for system maintenance, updates, installing or removing software?

We don't know what threads you are referring to but one thing to bear in mind is that many times an article or thread might say you need root privileges to do something but what they actually mean is sudo.

On the other hand, if those articles/threads actually refer to the root account I would suggest avoiding such things.

As **ajgreeny **pointed out, the root account is disabled by default on Ubuntu and there are very good reasons for this...

---

### Post by satimis on 2024-03-18
> **Rubi1200 said:**
> Are you able to use **sudo **without any issues, meaning for system maintenance, updates, installing or removing software?
- snip -
Yes.  I run "sudo" to do all jobs without any problem.

It is ONLY a curiosity

Regards

---

### Post by yancek on 2024-03-18
>  
It is just a curiosity on reading online threads that all advices running as root # NOT sudo.

The concept of 'sudo' has been around since the beginning of Linux and long before Ubuntu existed.  The original purpose of it was to allow users other than the primary root user some escalated privileges, to run certain commands or perform certain tasks but not have full privileges.  This can easily be done by editing the /etc/sudoers file as root or on Ubuntu with the primary (sudo) user.

The link below is to the Ubuntu site discussing the pros and cons of using sudo.  As you can see, the first few are pretty silly and seem to pander to the lazy and semi-literate.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by grahammechanical on 2024-03-18
Linux is designed to require a root or administrator account with password and separate additional user accounts with limited privileges. Ubuntu developers have chosen to do things differently because their purpose is that Ubuntu be for humans. And humans mess things up. 

But because Ubuntu sits on Linux it is possible to set up a root account. It is not recommended. Break the OS and you get to keep the pieces. Experiment by all means but do not do it on your working OS.

As for your question about setting a new root password I suggest that you try it. It may be better if you set up a new user (with password) as root and if that works you can then delete the original root user whose password is forgotten.

The Debian distribution of Linux does require the setting up of both a root/administrator account and a standard user account.

Forum policy is to not give out dangerous information. This is why we are not so open about discussing this subject. In fact I am almost totally ignorant of these commands.

Regards

P.S.  This might help

[https://wiki.debian.org/Root](https://wiki.debian.org/Root)

And this

[https://www.debian.org/doc/manuals/debian-reference/ch04.en.html#_securing_the_root_password](https://www.debian.org/doc/manuals/debian-reference/ch04.en.html#_securing_the_root_password)

---

### Post by donald187 on 2024-03-18
> **grahammechanical said:**
> 
The Debian distribution of Linux does require the setting up of both a root/administrator account and a standard user account.

...

P.S.  This might help

[https://wiki.debian.org/Root](https://wiki.debian.org/Root)

And this

[https://www.debian.org/doc/manuals/debian-reference/ch04.en.html#_securing_the_root_password](https://www.debian.org/doc/manuals/debian-reference/ch04.en.html#_securing_the_root_password)

My understanding is that Debian does support no root account and the first user given root privileges via sudo like Ubuntu.  You just don't choose a root password in the network installer.  Your first link states this under "Password".

> 
**Password**

 At installation time, you are asked whether you want to use the root account or not. 

[LIST]
[*]If you want to *(the default)*, you'll be asked to provide a **complex** password for root. *Use a strong one!* 
[*]If not, no root account is enabled and the password of the first user created will be used for administration tasks.
[*]If you forgot your root password, you first need to [reset the password]("https://www.debian.org/doc/manuals/debian-reference/ch04.en.html#_securing_the_root_password"), then log as root (now accessible without password) and run passwd to set a new password. 
[/LIST]


---

### Post by ajgreeny on 2024-03-18
A first user in Debian is not automatically a member of the sudo group so can not do anything which needs root permissions. However that user can be added to that group, just as he or she is in Ubuntu though to make that change in Debian you have to use the root account, not the first user account.

Once the first Debian user is added to the sudo group the whole system can be used exactly as it if using Ubuntu and from that point on everything can be done using sudo but with the user password not the root password which you have to set when installing. I have done this myself in a trial KVM/QEMU installation of Debian-Unstable (sid).

If you wish to do so you can even use the same password for root and user though whether that is an advisable thing to do I have no idea, nor whether you can then disable the root account, though if Ubuntu users decide to enable the root account it can certainly be disabled very easily with a terminal command. I have not done either in Ubuntu an never had a need to do so.

I like the way this is all done in Ubuntu and see no reason to make any change to that system which has worked perfectly for me for 20 years.

EDIT:
I've just seen the post above by donald187 and was not aware that you could install without setting a root password in Debian; I must have missed that but will certainly try it next time I install it which I do fairly often.

---

