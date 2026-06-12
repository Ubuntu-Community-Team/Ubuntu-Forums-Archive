---
title: "removed python3 boot and DNS server problems"
date: 2019-04-04
forum: General Help
---

### Post by sophia.bobby on 2019-04-04
Hi All,
[COLOR=#1A1A1B][FONT=&quot]I unfortunately ran sudo apt purge lib-python3 on Ubuntu 18.04 and now it reboots in terminal [/FONT][/COLOR][COLOR=#1A1A1B][FONT=&quot]Ubuntu 18.04 LTS ubuntu tty1 (Sophia should not be messing with her computer! [/FONT][/COLOR];)[COLOR=#1A1A1B][FONT=&quot])
I read many suggestions that involve installing via sudo apt-get install python3-all etc. but ultimately I get the message 'Could not resolve 'us.archive.ubuntu.com'.

reading /etc/resolv.conf

nameserver 127.0.0.53
options edns0

My questions:
1. Do I have a DNS server problem and how to I correct the network connection
2. Is this correctable from the terminal, say by reinstalling python3, etc.
3. How do I backup my hard drive from terminal, say using an external hard drive (I don't have one, but I will go get one)

thanks!
Sophia[/FONT][/COLOR]

---

### Post by oldfred on 2019-04-04
You do not uninstall any python. If you want other versions, it often is possible just to add them.
But major parts of Ubuntu run on python, and it has been upgraded to use python3, but some apps may still need python2.

It used to be the only solution was a total reinstall & restore from your backups. And since most users uninstalling python had no backups, it was just start all over again.
And older versions all networking relied on python to work. But newer versions should still work.

Now if you can get to a command line with networking from recovery mode,the full reinstall of the desktop may resolve the issues. If not you may have to chroot into system.
sudo apt install ubuntu-desktop      
This package depends on all of the packages in the Ubuntu desktop system

        chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)
UEFI chroot
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

---

### Post by rbmorse on 2019-04-04
Sophia should most definitely be messing with her computer! It's how humans lean about their world.  

Sophia should, however, make backups, first. 

We don't have to get into a backup discussion here. If you're interested, the search tool works well, or open a new thread.

---

