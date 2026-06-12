---
title: "Samba issues un 18.04"
date: 2018-11-08
forum: General Help
---

### Post by alexisantonakis on 2018-11-08
Hi,

I realise that Samba has changed between 17.10 and 18.04, and after some messing about I finally managed to share my directories on Ubuntu with WinXP.
I then upgraded my HDD and re-installed Ubuntu 18.04. Now I cannot for the life of me get WinXp to find the UBuntu shared folders.  It is finding the Ubuntu Share, just not the folders themselves.

For the life of me I cannot remember what I did to get this to work, and I have even been back through my browsing history, but no joy either.

Is anyone able to help out or put me onto a thread which explains all of this.

Thanks
Alexis

---

### Post by mitesh.agrwl on 2018-11-09
Hi,

Please check this link [https://ubuntuforums.org/showthread.php?t=2384959](https://ubuntuforums.org/showthread.php?t=2384959)

Regards,
Mitesh

---

### Post by alexisantonakis on 2018-11-09
Thanks but I have already followed this thread and still no joy. All it did was to let windows recognise the Ubuntu 'workgroup' but still does not display any of the shared folders on Ubuntu

---

### Post by mitesh.agrwl on 2018-11-09
Hi,

Asking as i am curious, why to use WinXP? Is it not too old, without any updates and support, a lot of recent features are unavailable. Is it some kind of mandatory testing platform?

Regards,
Mitesh

---

### Post by HermanAB on 2018-11-10
If XP finds the share then everything network related is working.  Your issue is probably only permissions of the folders and their contents.  

Try making the whole share ‘777’ world read write:
$ sudo chmod 777 /wherever/whatever

BTW, an anonymous FTP server can be much less hassle for a small home user LAN.  It is all hopelessly insecure anyway... &#128514;

---

### Post by alexisantonakis on 2018-11-10
multiple reasons, and it is not too old, it does what I need just perfectly, well as perfectly as any MicroS@#t product does :)

---

### Post by alexisantonakis on 2018-11-11
sorted it out..turned out I had enabled a firewall when I made the new install...duh!!!

---

### Post by alexisantonakis on 2018-11-11
Thanks very much for the info...you were quite right about permissions, just not with the folders...it was with the entire computer...I had the firewall turned on by mistake...duh!!! :)

---

### Post by lisati on 2018-11-11
Threads merged.

Please do not start multiple threads for the same support requests, it dilutes the community's ability to help and can get confusing when there are replies in both threads.

---

