---
title: "ubuntu 12.04 weird pixelated screen after login"
date: 2014-01-06
forum: General Help
---

### Post by stanleyhunk on 2014-01-06
hi all,

After I do a re-installation due to i've mess up the system previously on some trial and error, i got a weird pixelated screen after my login but before the desktop appear. Other than that is no problem, i can do all my thing such as watching movie, playing steam games, etc.. I really hope to fix this so i can convince my friend to try switch to linux :)

I've upload the image of the screen as attachment.
- attachment 001, the boot screen, no problem.
- attachment 002, the login screen, no problem.
- attachment 003-01, after i've type in my password and log in, the pixelated screen problem appear every time if i shutdown my laptop on the previous session.
-attachment 003-02, this pixelated screen problem appear if i restart my laptop on the previous session.
-attachment 004, after the pixelated screen, the desktop appear, no problem. 

I've search the fix on ubuntu forum, ask ubuntu and google as well, can't get any relevant problem as mine (maybe i've over looked them due to i'm not an expert user on linux). I only get those weird checker box, or when doing installation process, or deform text.

My laptop specification:
- Asus A45V Series, Intel Core i7
- Single OS, Ubuntu 12.04LTS only
- nvidia geforce GT 645M

My lspci result:
```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 IDE interface: Intel Corporation 7 Series Chipset Family 4-port SATA Controller [IDE mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
00:1f.5 IDE interface: Intel Corporation 7 Series Chipset Family 2-port SATA Controller [IDE mode] (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 645M] (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)
03:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
```

any help about this? thanks in advance

---

### Post by carl4926 on 2014-01-06
So it's hybrid graphics?

---

### Post by stanleyhunk on 2014-01-06
> **carl4926 said:**
> So it's hybrid graphics?

yes it is

---

### Post by carl4926 on 2014-01-06
Is that using the nvidia prime then?

---

### Post by stanleyhunk on 2014-01-06
> **carl4926 said:**
> Is that using the nvidia prime then?

using nvidia_331 in additional drivers

---

### Post by stanleyhunk on 2014-01-08
hmm... no fix on this yet? lol

---

### Post by carl4926 on 2014-01-09
> **stanleyhunk said:**
> hmm... no fix on this yet? lol
I can't really help you
I don't have hybrid graphics and personally wouldn't entertain them.

But if I understand it correctly, this is just an aesthetic issue during the boot/login process?
Otherwise your system is fine?

---

### Post by MrMichaelHill on 2014-01-09
Have you altered the login screen background at all?

---

### Post by stanleyhunk on 2014-01-09
hi all,

thanks to **carl4926 **and** MrMichaelHill **for  the reply, i suspect this is something to do with nvidia and xorg  server, so i do some searching and tried something describe [here]("http://askubuntu.com/questions/325037/installing-nvidia-drivers-on-ubuntu-12-04") and [here]("http://ubuntuforums.org/showthread.php?t=1150319"), the problem solve now.

_The basic theory is to remove nvidia and xorg completely then install them back, here is what i've done:_

01.) Reboot my laptop to recovery mode by keep the Shift key pressing down after the laptop manufacturer logo appear and release it after Grub menu fully loaded, then choose the 'Recovery Mode'.

02.) Choose 'Boot Normally' when a menu appear.

03.) Open up terminal by hitting Ctrl+Alt+T.

04.) Remove the xorg.conf by typing:
```
sudo rm /etc/X11/xorg.conf
```

05.) Remove all nvidia package by typing:
```
sudo apt-get remove --purge nvidia*
```

06.) Remove xorg by typing:
```
sudo apt-get remove --purge xserver-xorg
```

07.) Reinstall xorg by typing:
```
sudo apt-get install xserver-xorg
```

08.)Reboot the system by typing:
```
sudo reboot
```

09.) After successfully reboot, the pixelated screen is gone~ (yay~!!)

10.) I open up 'Additional Drivers', i got 2 nvidia driver, version 319 and 331 (to get to know the version of both by reading the extra information provided below them) which is not activated, so i activated version 319 and then reboot. (because i got problem with 331 previously)

11.) Then I run a program which need 3D support, in this case i run Steam game, but Steam detected there is a newer version of nvidia and ask me to update it, so i close Steam, go back to the 'Additional Drivers', choose the 331 version and activate it, then restart my laptop, and the pixelated screen is still gone~~ (double yay~!!)

In the process of trial and error, maybe i've miss out some step or done something wrong and i met some problem such as low graphic mode, looping in login screen, if you meet one of them, or maybe both...

_To solve the low graphic mode:_

01.) Reboot into Recovery mode again.

02.) Choose 'Boot Normally' when a menu appear.

03.) Open up terminal by hitting Ctrl+Alt+T.

04.) Remove all nvidia package by typing:
```
sudo apt-get remove --purge nvidia*
```

05.) Install the more stable/tested version:
```
sudo apt-get install nvidia-current
```

06.) Install the more up-to-date version:
```
sudo apt-get install nvidia-current-updates
```

07.) Reboot. 

_To solve the looping in Login screen:_

01.) At the login screen, press Crtl+Alt+F1 to boot into shell environment.

02.) Type your username and password to login.

03.) Change the working directory to your home directory:
```
cd /home/***user***
``` 
or 
```
cd ~
```

04.)  Rename a hidden file:
```
sudo mv .Xauthority .XauthorityBak
```

05.) Reboot.

This should fix the problem, but if you started to get a 'System Problem Detected' when you would login from a locked desktop, try to change the .Xauthority ownership in your home directory by typing the following command in terminal: 
```
sudo chown 777 .Xauthority 
```
and that seemed to have cleared up the problem. I am not sure if this causes a security issue.

This is how i do to fix my problem, i'm actually not an I.T guy at all, and i don't have in-dept skills and knowledge and very fresh in Linux platform switched from Windows, i maybe uses a long and exhausted and time consuming way to do it, but i'm very interested to learn more about Linux and keep on learning as much as i can, if any pro out there have a better way to solve this, please share, thanks :p

---

### Post by carl4926 on 2014-01-10
Sounds good
Well done

---

### Post by MrMichaelHill on 2014-01-10
Thanks for taking the time to give an extensive write up! Much appreciated for future reference!

I had the same issue once, but mine solved because I had used Ubuntu Tweak to select a log in screen background that was on an external drive. 
Obviously the drive wasn't mounted at boot up so I just had a plain wallpaper at log in but when I would log in I got the same thing as you!
Solved it by changing it back again.

:P

---

### Post by stanleyhunk on 2014-01-11
oh i see, but my problem is definitely not cause by the login screen background wallpaper.

i write down the process here so in future it might help other if encounter same problem, even for myself if i mess up the system again lol

---

