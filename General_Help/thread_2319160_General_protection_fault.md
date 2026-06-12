---
title: "General protection fault"
date: 2016-04-01
forum: General Help
---

### Post by tigerjack89 on 2016-04-01
Since yesterday I was receiving General Protection Faults errors (2 IIRC) like this

[IMG]http://i.stack.imgur.com/Rm2vU.jpg[/IMG]

I don't know if it's related, but yesterday, just an hour or so before the first crash, I've installed the following packages through a system dist-upgrade

```

    $>zgrep "^2016-03-31.*\ installed\ " /var/log/dpkg.log*
    /var/log/dpkg.log.1:2016-03-31 16:21:32 status installed mime-support:all 3.54ubuntu1.1
    /var/log/dpkg.log.1:2016-03-31 16:21:33 status installed bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
    /var/log/dpkg.log.1:2016-03-31 16:21:33 status installed desktop-file-utils:amd64 0.22-1ubuntu1
    /var/log/dpkg.log.1:2016-03-31 16:21:33 status installed gnome-menus:amd64 3.10.1-0ubuntu2
    /var/log/dpkg.log.1:2016-03-31 16:21:39 status installed shared-mime-info:amd64 1.2-0ubuntu3
    /var/log/dpkg.log.1:2016-03-31 16:21:39 status installed man-db:amd64 2.6.7.1-1ubuntu1
    /var/log/dpkg.log.1:2016-03-31 16:21:40 status installed menu:amd64 2.1.46ubuntu1
    /var/log/dpkg.log.1:2016-03-31 16:22:01 status installed oracle-java8-installer:all 8u77+8u77arm-1~webupd8~4
    /var/log/dpkg.log.1:2016-03-31 16:22:01 status installed xserver-xorg-video-openchrome:amd64 1:0.3.3-1ubuntu0.1
    /var/log/dpkg.log.1:2016-03-31 16:22:15 status installed spotify-client:amd64 1:1.0.25.127.g58007b4c-22
    /var/log/dpkg.log.1:2016-03-31 16:22:16 status installed libc-bin:amd64 2.19-0ubuntu6.7
    /var/log/dpkg.log.1:2016-03-31 16:22:16 status installed menu:amd64 2.1.46ubuntu1

```


The OS is **Ubuntu 14.04.4 LTS** with kernel **3.13.0-83-generic**.


Do you have any idea on how to solve the problem?

---

### Post by ajgreeny on 2016-04-01
From what I can see in your image this seems to be a virtual installation in VirtualBox, so I have moved this thread to the Virtualisation forum where you should get better answers.

---

### Post by tigerjack89 on 2016-04-01
> **ajgreeny said:**
> From what I can see in your image this seems to be a virtual installation in VirtualBox, so I have moved this thread to the Virtualisation forum where you should get better answers.
Thanks for your help.
Why do you think it's related to this? At the beginning I came to the same conclusions because of the first few modules of the [COLOR=#111111][FONT=Ubuntu]"Modules linked in" section, but I didn't know if it was right. So, this section is related to the cause of the problem? If so, what about the other modules listed?
EDIT: Also, if it might help, when the fault appears on my screen, I just press ESC to return to the normal screen; and VirtualBox was already running without any evident problem.[/FONT][/COLOR]

---

### Post by tigerjack89 on 2016-04-02
> **ajgreeny said:**
> From what I can see in your image this seems to be a virtual installation in VirtualBox, so I have moved this thread to the Virtualisation forum where you should get better answers.
After further investigation, the problem seems to be related to the RAM, so please move this thread to a more appropriate section.

---

### Post by ajgreeny on 2016-04-02
OK, I've moved it back to General Help forum.

Sorry I can't help you more.

Good luck.

---

### Post by bashiergui on 2016-04-02
> **tigerjack89 said:**
> After further investigation, the problem seems to be related to the RAM, so please move this thread to a more appropriate section.
If you're having RAM issues with a VM then give it more RAM. 

How have you configured the VM- list processors, ram, disk size, etc

---

### Post by ajgreeny on 2016-04-03
Just a quick thought following on from bashiergui's comment.

What is your ratio of host RAM to guest RAM as I know I always see an error in the settings GUI if I enable more than half my host's total RAM in my guests, even though I have not seen it stop the guest running properly; it just reports "Invalid settings detected".

---

