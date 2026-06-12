---
title: "Adept trying to uninstall a lot of important packages and now crashing"
date: 2006-12-23
forum: General Help
---

### Post by finferflu on 2006-12-23
Hi all,

I'm having a problem with Adept. I'm on Kubuntu Edgy. I've recently installed IceWM, so after a couple of days I logged in in the KDE session, and it usually does the update check. This time I went to check the list of upgrades, and there were a lot of broken packages and packages to uninstall (including xorg-xserver), which scared me, so I quit Adept, but then I wanted to go back in order to take a screenshot or do something, but since then I've been unable to start it. It keeps crashing if I try to open it with sudo or kdesu, so I can't get access to that screen anymore. I tried to reboot, but adept_notifier crashed as soon as the session started, here is the backtrace:

```
(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1233077584 (LWP 4765)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xb7908c53 in strlen () from /lib/tls/i686/cmov/libc.so.6
#7  0xb7a8f186 in std::string::compare () from /usr/lib/libstdc++.so.6
#8  0xb7eeda27 in debPackagesIndex::FindInCache ()
   from /usr/lib/libapt-pkg-libc6.4-6.so.3.51
#9  0xbff2223c in ?? ()
#10 0x00000000 in ?? ()

```

I tried to install Picasa through Automatix2, but apt-get had a segmentation-fault, so I was unable to install it. 

Without apt I'm really stuck, I appreciate any help!

Thanks!

---

### Post by finferflu on 2006-12-23
Well, I also want to add that I tried rebooting again, and I had the same crash. So I tried to update aptitude and this is what I get:

```
$ sudo aptitude update
Password:
Segmentation faultsts... 0%
```


Thanks for your time.

---

### Post by finferflu on 2006-12-23
Well, this is a nice monologue, but I've just solved my problem!!

I followed [this thread]("http://ubuntuforums.org/showthread.php?t=76332&highlight=Segmentation+faultsts...+0%25") and did this:

```
$ sudo rm /var/cache/apt/*.bin
```

Did the update, and this time I had only one package upgradable, instead of a list of broken packages and important packages to remove. 

Thanks for reading anyway, and I hope it will help whoever gets in such a trouble :)

---

