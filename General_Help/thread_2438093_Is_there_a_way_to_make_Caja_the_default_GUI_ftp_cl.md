---
title: "Is there a way to make Caja the default GUI ftp client?"
date: 2020-03-05
forum: General Help
---

### Post by cbraxton on 2020-03-05
This is on Ubuntu Mate 16.04, and the question is precipitated by a workaround to another problem.

Recently I installed a newer router (Asus RT-AC66U_B1) to replace my aging Asus RT-N16. The older router was running "Easy Tomato" firmware and acting as a NAS. It had decent enough NAS performance considering the USB2 drive connection.

The new router is running DD-WRT and is an improvement in nearly all respects - much faster CPU, more memory, 5GHz wifi, and USB3. However, I'm finding that connecting to it via Ubuntu Mate 16.04 is unusably slow; so bad that everything crawls to the point where a reboot is needed to clear it. Windows systems connect with no problem, as does my Ubuntu 18.04 laptop.

So as a workaround I put in a Mate panel bookmark to make a server connection via FTP instead of Windows Share. The FTP connection is lightning fast. However, if the bookmark is accessed from Mate's top panel the ftp connection comes up in a web browser. To bring the connection up in file manager mode requires that it be accessed through Caja directly instead of the Mate panel. *Horrors, an additional click required!* :shock:

I'm figuring this must be due to the default web browser being assigned to FTP as well as HTTP/HTTPS connections. Is there a way to change this? (The only related setting I can find in Preferred Applications is for the system default web browser. There is no option to assign a program to each protocol.) Maybe a hidden setting somewhere?

---

### Post by Holger_Gehrke on 2020-03-06
I don't think you can change the default handler for a specific protocol. But instead of a bookmark to the address you can set up an additional application icon for caja with the URL as a parameter.

Holger

---

### Post by cbraxton on 2020-03-06
> **Holger_Gehrke said:**
> I don't think you can change the default handler for a specific protocol. But instead of a bookmark to the address you can set up an additional application icon for caja with the URL as a parameter.

Holger

Thanks, that's a good workaround if the ftp handler can't be specified. Might be a moot point though since newer versions of Ubuntu seem to work OK with DD-WRT's Samba and I'll probably upgrade to 20.04 sometime in the next year, before 16.04's support expires.

---

### Post by guiverc on 2020-03-06
FYI:  Ubuntu MATE 16.04 being a flavor, had only 3 years of support and has already ended.

Refer [https://ubuntu-mate.community/t/ubuntu-mate-16-04-lts-reaches-end-of-life/19425](https://ubuntu-mate.community/t/ubuntu-mate-16-04-lts-reaches-end-of-life/19425)

Ubuntu server 16.04 LTS, Ubuntu desktop 16.04 LTS (with Unity 7), and Kylin desktop have 5 years of support, all 16.04 flavors are now EOL which you can confirm via

 ```
ubuntu-support-status 

```

which will let you see from your installed packages on your actual system (ie your Ubuntu base is still supported, but GUI and many MATE elements are now EOL)

> [COLOR=#333333]Maintenance updates are provided for 5 years for Ubuntu Desktop, Ubuntu Server, Ubuntu Cloud, Ubuntu Base, and Ubuntu Kylin. All the remaining flavours are supported for 3 years.[/COLOR]

from  [http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/](http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/)

---

