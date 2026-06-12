---
title: "Lost splash"
date: 2008-05-01
forum: General Help
---

### Post by MangasColoradas on 2008-05-01
```
stone@ubuntu:~$ sudo update-alternatives --config usplash-artwork.so

There are 3 alternatives which provide `usplash-artwork.so'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/usplash/usplash-theme-ubuntu.so
 +        2    /usr/local/lib/usplash/chrome-theme.so
          3    /usr/local/lib/usplash/Black_Metal-Ubuntu.so

Press enter to keep the default[*], or type selection number: 1
Using '/usr/lib/usplash/usplash-theme-ubuntu.so' to provide 'usplash-artwork.so'.
stone@ubuntu:~$ sudo dpkg-reconfigure linux-image-$(uname -r)
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.24-16.30 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.24-16.30 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
**Searching for splash image ... none found, skipping ...**
Found kernel: /boot/vmlinuz-2.6.24-16-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done
```



I followed this guide [https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto) from 3-6 and installed two usplash splash screens I downloaded, neither of which worked for some reason, just got a black screen.

Now when I select the pre-installed Ubuntu theme I am still getting a black screen.

---

### Post by MangasColoradas on 2008-05-01
Somehow my /etc/usplash.conf had lost its parameters so I added 

```
# Usplash configuration file
xres=1280
yres=1024
```

to it and now it works again, plus by altering my grub with vga=791 I now have a decent splash whereas preciously it was too big.
I can prolly get the others working now too.

---

