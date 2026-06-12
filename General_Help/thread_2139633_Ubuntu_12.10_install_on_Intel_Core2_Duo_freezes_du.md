---
title: "Ubuntu 12.10 install on Intel Core2 Duo freezes during install."
date: 2013-04-27
forum: General Help
---

### Post by rtischer8277 on 2013-04-27
I have Windows 8 installed. My processor is an Intel Core2 Duo. I bought an Ubuntu 12.10 CD from Amazon just to make the install easy and repeatable. But when I tried to install it booting up from the CD, it gave me options of installing from two different images, either UBUNTU-12.10-DESKTOP-I386.ISO or UBUNTU-12.10-DESKTOP-AMD64.ISO. The first is for a 32-bit installation and the second if I wanted a 64-bit installation. My processor is an Intell Core2 Duo which should take either one. First, I tried the 32 bit installation. Black screen freeze after an initial Ubuntu screen. I started completely over and tried the 64-bit installation. It too churned a bit, showed the Ubuntu screen, this time played the Ubuntu drumroll, then too showed the black screen of death. The title of the Ubuntu CD I purchased from Amazon is 'Ubuntu 12.10 Special Edition DVD - Includes both 32-bit and 64-bit Version'. In the comments it adds the words 'Quantal Quetzal' which have no meaning to me. BTW, the merchant SKU is I1-8SEA-5QWN. If no one can tell me what is going on, then I am going to have to give this Ubuntu merchant a very negative review and return the product.

---

### Post by dino99 on 2013-04-27
that dvd can have a quality issue; but before blaming it, some boot options can be tried : [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
and the ubuntu's iso can be downloaded freely and installed with a usb thumb ( via unetbootin) : [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)
note that the "netboot" iso is an easy way for installation when you have a fast internet link

[http://www.ubuntu.com/download/desktop/install-desktop-latest](http://www.ubuntu.com/download/desktop/install-desktop-latest)
[http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

---

### Post by oldfred on 2013-04-27
As dino99 says, you probably need boot options for the video. I have nVidia with CoreDuo Intel processors and run the 64 bit version without issue other than having to use nomodeset on every liveCD/DVD/Flash drive boot and on first boot after install.

       Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)
How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by rtischer8277 on 2013-04-27
Thank you for the replies, but it turns out that the problem is Windows 8. I had an older PC with Windows Vista on it and Ubuntu installed fine on it, so there is no problem with the CD. I did see some threads warning me about store-bought installations of Windows 8 and trying to install Ubuntu, I figured that I could go ahead and install Ubuntu, especially since I have had an earlier Ubuntu version running on it before. But no such luck. Ubuntu along side Windows 8 does not work. It will be interesting to see how the Linux community reacts to this act of war by Microsoft. Anyway, problem solved at least for me.

---

### Post by oldfred on 2013-04-27
A lot of users have installed Ubuntu with Windows 8 even the pre-installed versions with secure boot.

But the hibernation can be an issue. Windows 8 uses hibernation to make users think it boots faster.

 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

