---
title: "How To Stop Dualbooting"
date: 2016-01-27
forum: General Help
---

### Post by Darth4212 on 2016-01-27
I am done with dualbooting and would like to uninstall Ubuntu but keep grub2. How would I do this? I don't have a flashdrive or whatever so don't say that.

---

### Post by Nuno_Abreu on 2016-01-27
The best way you can do this is to touch the /boot/grub/grub.cfg file and delete the Ubuntu menuentry, which doesn't seem so hard. Just don't forget to have Windows as the first entry in the configuration file!
Then, please post the output of this command.
```
sudo update-grub
```

If you have any issues, feel free to ask.

---

### Post by Darth4212 on 2016-01-27
Okay I will try this when I get home. By the way would I be able to install Kali Linux over Ubuntu?

---

### Post by Nuno_Abreu on 2016-01-27
Yes, of course! Just format the Ubuntu partition and install there.
Now, if you have already deleted the Ubuntu partition, make a new one with Gparted - it's not that hard!

---

### Post by Darth4212 on 2016-01-27
also I have a question I was not using Ubuntu for a while and was using Windows 10 when I started up Ubuntu yesterday no mater what desktop environment I used I didn't have a desktop.

---

### Post by grahammechanical on 2016-01-27
Here is the situation. The Grub boot loader will look to the partition that Ubuntu is installed in and it will look into /boot/grub/ for its configuration files. Delete the Ubuntu partition and you will still keep Grub but it will be broken. The configuration files will be gone. And you will not be able to load any other OS that you used Grub to load into.

We can install another Linux distribution into the Ubuntu partition. That will remove Ubuntu and the new Linux distribution should install its version of Grub over the Ubuntu version of Grub. See, the documentation for the relevant Linux distribution.

> when I started up Ubuntu yesterday no matter what desktop environment I used I didn't have a desktop.

As you are going to remove Ubuntu that problem is a distraction.

If you are not going to replace Ubuntu with another Linux distribution but only remove Ubuntu you should restore the Windows boot loader before deleting Ubuntu. Otherwise, you will not be able to load Windows.

---

### Post by Nuno_Abreu on 2016-01-28
The MBR is what matters anyway - it won't have a problem because it will directly boot into Windows.
But if there is a problem, there's always the option of using EasyBCD on Windows.

---

### Post by mastablasta on 2016-01-28
> **Darth4212 said:**
> Okay I will try this when I get home. By the way would I be able to install Kali Linux over Ubuntu?

a bit offtopic, but I wonder what Kali (Debian based) has to offer over Backbox (Ubuntu based) Linux?

I think Kali went to some kind of rolling release, but I wonder if there is any other bigger difference that would make Kali better than Backbox (both aimed at same public)?

---

### Post by Darth4212 on 2016-01-28
I wanted to try to install Kali because of the white-hat hacking capabilities I didn't want to say this due to the forums rules.

---

### Post by Darth4212 on 2016-01-28
I know that my 2 different threads may be confusing I want to keep both open due to the fact that it will allow me to keep both options open to myself.

---

### Post by yancek on 2016-01-28
It would probably save you a lot of potential grief if you installed Kali to a flash drive.  Detailed instructions on their site.  Although it is obviously possible to install on a hard drive, it is designed more to run from a DVD or flash drive which of course also makes it portable.

[http://docs.kali.org/downloading/kali-linux-live-usb-install](http://docs.kali.org/downloading/kali-linux-live-usb-install)

---

