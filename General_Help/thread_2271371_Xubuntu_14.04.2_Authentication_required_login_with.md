---
title: "Xubuntu 14.04.2 Authentication required login with USB Hard Drive attached"
date: 2015-03-29
forum: General Help
---

### Post by manuleka on 2015-03-29
Platform:
Xubuntu 14.04.2 
1TB USB 3.0 Hard Drive
USB Sticks
=====

I notice everytime i login from boot or ScreenSaver if i have a USB drive attached i get the "Authentication is required to mount -Device_Name- (/dev/sdxx)"
[IMG]http://manumonkey.com/pic/Screenshot-300315-09:22:20.png[/IMG]

This prompt doesn't seem to have any effect on me getting access to the drive though when i click on it it

I had a look at this thread
[http://askubuntu.com/questions/552503/stop-asking-for-authentication-to-mount-usb-stick](http://askubuntu.com/questions/552503/stop-asking-for-authentication-to-mount-usb-stick)
but the line under udisks2.filesystem-mount already has this
```

    <defaults>
      <allow_any>auth_admin</allow_any>
      <allow_inactive>auth_admin</allow_inactive>
      <allow_active>yes</allow_active>
    </defaults>

```

help please... cheers

---

### Post by egeezer on 2015-03-29
When you log in to your desktop, you log in to everything on it, which in this case includes the USB.  You can mount the USB based on the authentication for the main desktop. It asks because in principle you have the choice of mounting it separately from the desktop (not that I have any idea how you could do that!)

---

### Post by manuleka on 2015-03-29
ok thanks egeezer

---

