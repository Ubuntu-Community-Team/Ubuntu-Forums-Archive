---
title: "ownCloud"
date: 2016-01-03
forum: General Help
---

### Post by gordon16 on 2016-01-03
I wanted to set-up my own cloud so I can easy access my personell files /home/xxx/ and some /mnt/hd/folder/ from a web browser at work or other locations.
I have installed ownCloud, but it`s look like ownCloud is not meant to work like that?
ownCloud set up it`s own user dir and storage area... 

My questions is is`t possible to add my /home/xxx/to my user in OwnCloud so I can access my files and upload / download by using ownCloud?

Summary it would be perfect for me if I could used exsisting /home/ structre and also exsisting username / password.

Maybe there are better cloud software for me to use?

---

### Post by Bucky Ball on 2016-01-03
How did you install owncloud? It has been removed from the official repositories for security reasons. This might give you some clues, from the Synaptics description:

> The ownCloud package has been removed from Ubuntu due to security issues that
can not easily be updated.

Alternative ways to install are: using the ownCloud packages on OBS:
 - [http://software.opensuse.org/download/package?project=isv:ownCloud:community&package=owncloud](http://software.opensuse.org/download/package?project=isv:ownCloud:community&package=owncloud)
Or the Juju ownCloud charm:
 - [https://jujucharms.com/precise/owncloud/](https://jujucharms.com/precise/owncloud/)

---

### Post by gordon16 on 2016-01-03
I was using, [https://www.howtoforge.com/how-to-install-owncloud-7-on-ubuntu-14.04](https://www.howtoforge.com/how-to-install-owncloud-7-on-ubuntu-14.04)
Thank you for feedback I will remove it now.

I have removed everyting now, How can I remove "sudo sh -c "echo 'deb  [http://download.opensuse.org/repositories/isv:/ownCloud:/community/xUbuntu_14.04/](http://download.opensuse.org/repositories/isv:/ownCloud:/community/xUbuntu_14.04/)  /' >> /etc/apt/sources.list.d/owncloud.list"
also ?

---

### Post by ajgreeny on 2016-01-03
> **gordon16 said:**
> I have removed everyting now, How can I remove "sudo sh -c "echo 'deb  [http://download.opensuse.org/repositories/isv:/ownCloud:/community/xUbuntu_14.04/](http://download.opensuse.org/repositories/isv:/ownCloud:/community/xUbuntu_14.04/)  /' >> /etc/apt/sources.list.d/owncloud.list"
also ?

You can do all that is necessary to disable or remove that repository from **Software-sources -> Other software** tab

---

### Post by deadflowr on 2016-01-03
> **ajgreeny said:**
> You can do all that is necessary to disable or remove that repository from **Software-sources -> Other software** tab
I guess software-sources depends upon which Ubuntu flavor is in use.
In Regular, Plain, Ubuntu it's **Software and Updates**.
But I'm never sure how other flavors call it.

However, a simple quick workaround would be to open a terminal and run
```
software-properties-gtk
```

Edit: to add, here a fun alternative if you want to try something interesting:
[https://insights.ubuntu.com/2015/08/10/ubuntu-one-file-syncing-code-open-sourced/](https://insights.ubuntu.com/2015/08/10/ubuntu-one-file-syncing-code-open-sourced/)

thought I'd throw that one out there, for the heck of it.

---

### Post by vcbranco on 2016-01-03
Hi,

See [http://ubuntuforums.org/showthread.php?t=2308461]("http://ubuntuforums.org/showthread.php?t=2308461")

---

