---
title: "Dual Boot- Win10 won't boot after it's selected in GRUB"
date: 2021-07-03
forum: General Help
---

### Post by hello-there on 2021-07-03
Help me I'm seriously lost and I don't know where to start. 
I started yesterday dual booting kubuntu/win10

**Things I've tried:**
- I tried using grub-repair but it says **"GRUB is still present.    Please try again."**  
- Copy pasting the commands given in grub-repair.

**Things I did after I dual booted**

(This was yesteday when everything worked fine)
- I restarted to boot into win10 and it was successfull
- Then I shutdown to go to sleep but I waited... then I realized that it's actually not letting me shut down 
- So I turned off fast-startup and done... computer shutdown. I sleep 
- When I waked up, I no longer can open it. 

**Screenshots:**
[https://i.stack.imgur.com/ub7UZ.jpg](https://i.stack.imgur.com/ub7UZ.jpg)
It unusually shows 2 windows(Don't mind the one
   /dev/sda2 version). These was probably created when I troubleshooted
   alone.
   
[https://i.stack.imgur.com/RiEyg.jpg](https://i.stack.imgur.com/RiEyg.jpg)
   The image after I choose Windows 10 (on /dev/sda1)

**Before the dual boot setup:**

Whenever I turned on laptop, It always shows these.

[https://i.stack.imgur.com/JhAtP.jpg](https://i.stack.imgur.com/JhAtP.jpg)   In recovery Mode everytime I turn on laptop from full shutdown/restart

I managed to get away from this by pressing F8 twice. What it does is disables the "early launch anti-malware protection". *Why do I have these error?* you might ask... Probably because I uninstalled windows defender and malwarebytes on my win10. 

**More Info**
- I still can access my linux
- The grub can still be accessed
- I can access my win10 files so the data there isn't corrupted.

---

### Post by zircon_34 on 2021-07-04
The information lacking in your post is how did you partition and install your system in the first place? 

https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/

Perhaps post your partition table to check that this is ok. 

https://www.google.com/amp/s/vitux.com/4-ways-to-view-the-partition-table-in-linux/amp/

And what ubuntu version are you running?

---

### Post by yancek on 2021-07-04
>   I tried using grub-repair 

Did you mean 'boot repair' at the site below?  I am not aware of 'grub-repair.  If you used boot repair, use the option to Create BootInfo Summary which when finished will give you a link which you can post here with information on your boot files.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you just did this yesterday, do you mean you had an install of windows and then installed Kubuntu?  Is your machine UEFI?  I expect it would be if windows was preinstalled.  You can verify this in the BIOS firmware.  After installing Kubuntu, were you ever able to boot windows from Grub? If not, Kubuntu may be installed in Legacy mode rather than UEFI and Grub won't boot windows UEFI.    If your machine is UEFI, you should be able to bypass Grub by going to the BIOS firmware Boot Options and select windows.  Does that work? 

Use boot repiar and answer the questions above to get help.  If you can boot Kubuntu from Grub but now windows, it may be Kubuntu and windows are not installed in the same mode (UEFI/Legacy) or there is a problem with your windows boot files.

---

