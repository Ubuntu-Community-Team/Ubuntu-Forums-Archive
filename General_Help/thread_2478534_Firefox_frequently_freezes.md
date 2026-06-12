---
title: "Firefox frequently freezes"
date: 2022-08-29
forum: General Help
---

### Post by aj34 on 2022-08-29
Over the past few weeks, Firefox has frozen, or become almost unresponsive, around twenty times. Today, I've even resorted to using Google Chrome.

I'm a novice (I stress, a complete novice) with Firefox and Ubuntu and really don't wish to go to great lengths to sort out this problem so my question is: what's the simplest way for a novice to get Firefox working properly again?

Thanks for your time.

---

### Post by mIk3_08 on 2022-08-30
Please run the command below in your terminal and paste the result here in thread. To access terminal in your desktop just press ctrl and alt + t or just find it in your Ubuntu installed app. Regards and cheers.
```
ls /var/lib/snapd/desktop/applications
```
or
```
type firefox
```

---

### Post by aj34 on 2022-08-30
Ran both commands in the Terminal as suggested and here are the results:

andy@home-pc:~$ type firefox
firefox is /usr/bin/firefox
andy@home-pc:~$ ls /var/lib/snapd/desktop/applications
mimeinfo.cache
snap-store_snap-store.desktop
snap-store_ubuntu-software.desktop
snap-store_ubuntu-software-local-file.desktop
vlc_vlc.desktop
zoom-client_zoom-client.desktop
andy@home-pc:~$ 

Hope this means something to someone! Cheers.

---

### Post by mIk3_08 on 2022-08-31
> **aj34 said:**
> Ran both commands in the Terminal as suggested and here are the results:

andy@home-pc:~$ type firefox
firefox is /usr/bin/firefox
andy@home-pc:~$ ls /var/lib/snapd/desktop/applications
mimeinfo.cache
snap-store_snap-store.desktop
snap-store_ubuntu-software.desktop
snap-store_ubuntu-software-local-file.desktop
vlc_vlc.desktop
zoom-client_zoom-client.desktop
andy@home-pc:~$ 

Hope this means something to someone! Cheers.
We have the same Firefox installed. Mine is running well/fine so far. I haven't encounter any errors. see image below: And please run the command command below and paste the result here in thread. 
```
hostnamectl status
```

---

### Post by aj34 on 2022-08-31
Just ran the command as suggested and here are the results:

andy@home-pc:~$ hostnamectl status
   Static hostname: home-pc
   Pretty hostname: Home PC
         Icon name: computer-desktop
           Chassis: desktop
        Machine ID: **Removed by me. I'm unsure about security aspects of displaying this info.**
           Boot ID: **Removed by me. I'm unsure about security aspects of displaying this info.**
  Operating System: Ubuntu 20.04.5 LTS
            Kernel: Linux 5.15.0-46-generic
      Architecture: x86-64

---

