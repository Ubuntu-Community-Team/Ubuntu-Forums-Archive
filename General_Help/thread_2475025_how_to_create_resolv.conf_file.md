---
title: "how to create resolv.conf file"
date: 2022-05-14
forum: General Help
---

### Post by chat-4432 on 2022-05-14
i just remove this resolv.conf file
```
rm resolv.conf
```
how can i create this file??

---

### Post by mhgsys on 2022-05-14
```
nano resolv.conf
```

however, I don't think that is exactly your goal... :)  

Take a look at this: [https://askubuntu.com/questions/134121/how-to-restore-recreate-etc-resolv-conf-files](https://askubuntu.com/questions/134121/how-to-restore-recreate-etc-resolv-conf-files)

---

### Post by The Cog on 2022-05-14
This command will open a simple editor:
```
sudo nano /etc/resolv.conf
```
Ctrl-X when finished - it will ask you if you want to save.

---

### Post by jeremy31 on 2022-05-14
The file /etc/resolve.conf should be a symlink to /run/systemd/resolve/stub-resolv.conf

---

### Post by TheFu on 2022-05-14
> **jeremy31 said:**
> The file /etc/resolve.conf should be a symlink to /run/systemd/resolve/stub-resolv.conf

That's the way that Ubuntu sets it up, but we don't need to use the systemd-resolved process or resolvconf tools, if we don't want them.  Sometimes they muck up DNS resolution, so the best option is to purge those from the system, delete any symlink that /etc/resolve.conf is, then create a new file and add 2 lines to /etc/resolv.conf like we did for 20 yrs before someone decided to make it "easier" ... and more complex than necessary.  There are issues doing this for portable devices, which need to use DHCP to get an IP and DNS settings, but for a desktop at home, all the complexities of systemd-resolved or resolvconf just isn't necessary.

To edit system files, use sudoedit. Get into this habit.  This tool is designed to be used for this.  Any editor can be used that you like. nano, jot, vim, gedit ... just set the *EDITOR* environment variable (in your ~/.bashrc) and it will be honored after you logout and login again. The way sudoedit works is safer than directly running **sudo nano** which isn't unsafe, but ... much safer than using any GUI editor with a sudo command.    So ....
```
$ sudoedit /etc/resolv.conf
```
is the command.  The contents of the file need be a primary and secondary DNS server.
```
nameserver 1.1.1.1
nameserver 1.0.0.1
```
Are typically good, fast, and respect our privacy, though our ISPs can see or intercept all that traffic without extra effort on our part to avoid it.  The /etc/resolv.conf should have these permissions:
```
-rw-r--r-- 1 root root 70 Jul  3  2021 /etc/resolv.conf
```

For a laptop or other system that needs to move, you'll probably want to figure out how to fix the DNS issue, if there is one.  systemd-resolved seems to be causing more problems than the prior solutions ever did. I don't have a good solution for that.  I can leave mine setup the same, since I always VPN when away from home back to my home LAN and use an internal DNS that I control running there.

If you are interested, you could setup an internal DNS filter and DNS server for your LAN using a Pi-Hole.  I run 2 (primary/secondary) on my LAN on different systems inside an LXD container. [Https://discourse.destinationlinux.network/t/pi-hole-in-canonical-lxd-container/1337](Https://discourse.destinationlinux.network/t/pi-hole-in-canonical-lxd-container/1337) explains how. That guide is for 18.04, but 20.04 should work. There's nothing specific to any release that I can imagine. I haven't tried it on 22.04. Hummm.

---

### Post by mhgsys on 2022-05-14
> **chat-4432 said:**
> i just remove this resolv.conf file.
how can i create this file??



Although the thread is marked as solved; for other users, it might be nice to know what you've ended up doing

---

### Post by cls42 on 2022-06-03
I installed Ubuntu Server 22.04  on a Raspberry Pi 3B+ and ran into this.    What is overwriting my /etc/resolv.conf file, and where did 127.0.0.53 come from???   ](*,)

Well that's how Ubuntu installs now.   And if you're running a desktop, your browser is probably faster with a local name cache.   systemd-resolved is good for that.   

But I already have two names caches on my LAN.  (bind9 named configured as a forwarder)   So a plain text  /etc/resolv.conf  file is good enough, and simpler. 

The right fix for me is remove the symlink, stop the service, make a static file:


e=/etc/resolv.conf    #   save some typing
ls -l $e
sudo  systemctl stop systemd-resolved.service
sudo  systemctl disable systemd-resolved.service
sudo  rm -v $e
sudo  echo -e nameserver 192.168.1.3 \\nnameserver 192.168.1.4 >  $e
sudo  chmod -v a+r,a-wx  $e     #   write protect
ping -c 3 kernel.org   #   test the network and name resolution 


You could use sudo nano or sudo vim to create the text file.  One nameserver per line.
nameserver 9.9.9.9
nameserver 4.2.2.1


BTW 64-bit Jammy Jellyfish Raspberry Pi 3B+ just works, yay!

---

