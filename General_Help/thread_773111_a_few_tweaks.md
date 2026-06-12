---
title: "a few tweaks"
date: 2008-04-28
forum: General Help
---

### Post by Wangberg on 2008-04-28
just have a few issues.  Help on any would go much appreciated!  

1.  How do you take away the graphic ubuntu logo when booting / shutting down?  
2.  My wireless does not authenticate with the dhcp until after i log in.  how do i initialize this during startup, prior to login interface?  
3.  I'm having problems with my fstab file also.  Trying to mount another drive, but utbuntu won't read fstab.  
4.  how do I create a root user and have su - ability?  
5.  how do I configure sudo to not require a password?...EVER.    

Thanks Again!
Wangberg

---

### Post by seamuso on 2008-04-28
> **Wangberg said:**
> just have a few issues.  Help on any would go much appreciated!  

1.  How do you take away the graphic ubuntu logo when booting / shutting down?  
2.  My wireless does not authenticate with the dhcp until after i log in.  how do i initialize this during startup, prior to login interface?  
3.  I'm having problems with my fstab file also.  Trying to mount another drive, but utbuntu won't read fstab.  
4.  how do I create a root user and have su - ability?  
5.  how do I configure sudo to not require a password?...EVER.    

Thanks Again!
Wangberg

1 - disable usplash
2 - I don't use wireless
3 - fstab should work .. try using the drives UUID ```
sudo vol_id /dev/sd?
```
4 - sudo passwd root
5 - sudo nano sudoers

---

### Post by Wangberg on 2008-05-04
> **seamuso said:**
> 1 - disable usplash
2 - I don't use wireless
3 - fstab should work .. try using the drives UUID ```
sudo vol_id /dev/sd?
```
4 - sudo passwd root
5 - sudo nano sudoers

This is exactly what i was looking for!!!

1. i didn't disable usplash, but just removed "splash" from the menu.lst (/boot/grub/menu.lst) kernel line.  

i got fstab working...bad parameters on my side.

i now have root and got sudo working without a pass.  

actually there is a line in the /etc/sudoers file that you can uncomment giving all users with sudo non-password access.  

THANKS!

I do have another though:

1. how do i prevent all icons in the notification area of my panel from launching with a single click.  I want double click to open items, not single.  

I'm sure there will be more to come!!! 

Thanks a TON for everything thus far!

---

