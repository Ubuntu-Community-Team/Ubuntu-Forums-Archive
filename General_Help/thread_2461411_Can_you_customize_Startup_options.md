---
title: "Can you customize Startup options?"
date: 2021-04-29
forum: General Help
---

### Post by mike431 on 2021-04-29
Hello all. I am seeking help for an elderly person. I have installed Ubuntu alongside win10 for him but after power on he will have only 10 seconds to choose the windows side as the default is automatically set on booting to Ubuntu. Is there any way to increase that 10 seconds or have the default boot to windows instead of Ubuntu please? Thanks.

---

### Post by Xian on 2021-04-29
You can do what you requested with the grub-customizer application:
[https://packages.ubuntu.com/search?keywords=grub-customizer](https://packages.ubuntu.com/search?keywords=grub-customizer)

Instructions for use:
[https://itsfoss.com/grub-customizer-ubuntu/](https://itsfoss.com/grub-customizer-ubuntu/)

---

### Post by tea for one on 2021-04-30
Just to add a little caveat - Grub-customizer can bring extra complications to the boot process.

Please do a little investigation before deciding to use it.

Here is some info [https://easylinuxtipsproject.blogspot.com/p/grub-customizer.html](https://easylinuxtipsproject.blogspot.com/p/grub-customizer.html)

It would probably be easier to configure Grub2 to do what you want.

Here is mine, which gives a 10 second delay.

```
GRUB_DEFAULT=0 [COLOR="#0000FF"]Can be changed for a different default i.e. 1 or 2 or 3 etc[/COLOR]
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10 [COLOR="#0000FF"]Can be changed to 30 or 35 or 40 etc[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

You can only change the file with sudo privileges
```
sudo nano /etc/default/grub
```
After you have edited the file, please remember to update Grub with
```
sudo update-grub
```

---

### Post by mike431 on 2021-04-30
Thanks guys, I am not a programmer so I will need to see if I can do this. Meantime, is there a way to disable the timer to make things easier for the person please?

---

### Post by dragonfly41 on 2021-04-30
Another option is to create a customised Ubuntu ISO for installation via LiveUSB
using Cubic to customise functionality.

Incidentally, although rEFInd is not necessary to install in EFI partition (alongside grub)
I have found that you can then create your own custom GUI through configuring refind.conf.

Thus you could greet the elder at login with customised messages, even changing content (tips) daily.

You can disable all the technical links like memtest and firmware testing.

Just an option.

---

### Post by tea for one on 2021-04-30
> **mike431 said:**
> Thanks guys, I am not a programmer so I will need to see if I can do this. Meantime, is there a way to disable the timer to make things easier for the person please?

I assume that you want the grub menu to always appear and the user will then have unlimited time to decide which OS to use?
You will still have to edit **/etc/default/grub** with admin privileges.

```
GRUB_DEFAULT=0 
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=-1 [COLOR="#0000FF"]Change to -1 (i.e. minus 1)[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

---

### Post by oliverjames on 2021-05-21
> **tea for one said:**
> Just to add a little caveat - Grub-customizer can bring extra complications to the boot process.

Please do a little investigation before deciding to use it.

Here is some info [https://easylinuxtipsproject.blogspot.com/p/grub-customizer.html](https://easylinuxtipsproject.blogspot.com/p/grub-customizer.html)

It would probably be easier to configure Grub2 to do what you want.

Here is mine, which gives a 10 second delay.

```
GRUB_DEFAULT=0 [COLOR=#0000FF]Can be changed for a different default i.e. 1 or 2 or 3 etc[/COLOR]
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=10 [COLOR=#0000FF]Can be changed to 30 or 35 or 40 etc[/COLOR]
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

You can only change the file with sudo privileges
```
sudo nano /etc/default/grub
```
After you have edited the file, please remember to update Grub with
```
sudo update-grub
```

What do you think of the Boot-Repair application [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) ?

---

### Post by grahammechanical on 2021-05-21
There is something you can do that no one has yet mentioned. It is a very simple thing to do. Tell your friend to press the space key when the boot menu appears. Then the 10 second count down will stop. If he then wants to load Ubuntu he just presses Enter because Ubuntu will be at the top of the list. If he wants to load Windows he uses the down arrow key to move the selection down to the line that says Windows and then he presses Enter.

If you edit the Grub configuration file to put Windows at the top he will still have to follow the above method to stop the count down, load Windows or load Ubuntu.

I think that when we install Linux/Ubuntu on someone else's machine we take upon ourselves the responsibility of training the person to at least be able to keep the OS up to date. When he updates Windows he may find the he can no longer load Ubuntu. Do you know how to fix that? Does he know how to fix that?

Oh, by the way. I became 73 last month. I believe that the more I keep thinking, learning and studying the less likely it will be that I shall lose the ability to think and to learn. Help your friend to figuratively walk upright on his own two feet. Introduce him to this forum. Show him how he can get help to fix problems.

Regards

---

