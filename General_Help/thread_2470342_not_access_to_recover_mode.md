---
title: "not access to recover mode"
date: 2021-12-27
forum: General Help
---

### Post by sk84life on 2021-12-27
Hello Team,

I have the ubuntu 18.04 and I need to get in recover mode but I'm not able to do that. After booting server with iso which I downloaded from "https://releases.ubuntu.com/18.04/" , I just have options in grub 2 install Ubuntu - OEM Install - Check disk - Boot and install with the HWE kernel . I miss out any point ? Can you please share your experience?

Thanks.

---

### Post by deadflowr on 2021-12-27
The image shows the server installer image's grub menu. 
Perhaps your boot sequence is set to boot from the usb/dvd/other first and not the hard drive.
Try booting from the hard drive, assuming you have an install already on the hard drive.

---

### Post by ajgreeny on 2021-12-27
Maybe recovery mode is disabled in /etc/default/grub which has a number of options that will affect what shows in the grub menu.

However, it seems that the grub menu you are seeing is from the USB you are booting from, not your installed system, so I'm not sure how that will help you.

---

### Post by sk84life on 2021-12-27
Thanks for sharing your comments. Actually let me share the situation which I'm in. Server is'not able to boot to OS. So I try to login recover mod. I want to check efibootmgr and disk partitions. I do it same thing is redhat and I'm able to access to recover mode via booting server with live iso I miss any steps on ubuntu?

---

### Post by deadflowr on 2021-12-27
Not sure the live server version has a recovery mode,
but you can get into a shell from the Help menu. then follow the livecd recovery page here to reset things:[https://help.ubuntu.com/community/LiveCdRecovery]("https://help.ubuntu.com/community/LiveCdRecovery")
To get to the Help menu select install server 
(don't worry you only need to get the installer started, as when it does the Help option will appear) 
simply press F1 to enter help and then scroll down the option to the enter shell option.)
Reference for this here: [https://ubuntu.com/server/docs/install/general#:~:text=You%20can%20switch%20to%20a,keys%20move%20between%20virtual%20terminals).]("https://ubuntu.com/server/docs/install/general#:~:text=You%20can%20switch%20to%20a,keys%20move%20between%20virtual%20terminals).")

I think you can also still get a shell by using the ctrl+alt+F1-6 key combos.
If for some reason help doesn't work.

Optionally another way to go about it is, you can grab the alternative server installer from here: [http://old-releases.ubuntu.com/releases/bionic](http://old-releases.ubuntu.com/releases/bionic)
Scroll to the bottom and choose the ubuntu-18.04.5-server-amd64.iso
that version should have a rescue option in the boot menu.

---

### Post by sk84life on 2021-12-29
Thank you very much for all details.

---

