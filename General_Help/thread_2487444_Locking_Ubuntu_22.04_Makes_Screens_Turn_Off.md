---
title: "Locking Ubuntu 22.04 Makes Screens Turn Off"
date: 2023-06-05
forum: General Help
---

### Post by sandmanfvr2 on 2023-06-05
So I am dual booting Ubuntu 22.04 at work and it runs great for what I do, but small thing that is bugging me is when I lock the computer it shows the lock screen for a second and then the displays shut off.  I don't know why as I have went into Power and Privacy settings and turned off screen blanking, but still happens.  Not a big deal, but wondered if there is other settings I am missing that is causing this?  Thank you!

---

### Post by mIk3_08 on 2023-06-06
In my Ubuntu 22.04 LTS. I don't have any Privacy settings under my Power Settings Menu.
I only have Power Mode, Power Saving Options, Suspend & Power Button. See image below:

---

### Post by sandmanfvr2 on 2023-06-06
Privacy is its own section not under Power, you should have it in the settings list.

---

### Post by mIk3_08 on 2023-06-06
> **sandmanfvr2 said:**
> Privacy is its own section not under Power, you should have it in the settings list.
Under the category 'Privacy', there should be a Screen Menu then Screen Lock Options. Under of that, you should see two options, called 'Blank Screen Delay' and 'Automatic Screen Lock.' Make sure those are set to Never and disabled.
see image below:

 If the above GUI doesn't work, you can try using this terminal command below: Regards and cheers
```
systemctl mask sleep.target suspend.target hibernate.target hybrid-sleep.target
```

---

### Post by sandmanfvr2 on 2023-06-06
Thank you for the reply, I changed my settings to what you showed in the GUI and still happening; then I did the terminal command, still I hit lock my pc and it shows my lock screen and fades out and screens go to sleep.  I give up, its not a big deal must be something with this machine.  Thank you.

---

### Post by mIk3_08 on 2023-06-06
Try log-off or restart your system then try to run the command when your system logs back on. Regards and cheers,.

---

### Post by sandmanfvr2 on 2023-06-07
Same thing. :)  Oh well I will live with it.

---

### Post by mIk3_08 on 2023-06-07
Are you using some DE? can you run the command below and paste the result here in thread wrap with code: 
```
neofetch
```
If ask to install the neofetch, please run the command below:
```
sudo apt install neofetch
```

---

### Post by sandmanfvr2 on 2023-06-07
```

           .-/+oossssoo+/-.               michael@michael-Inspiron-3880 
        `:+ssssssssssssssssss+:`           ----------------------------- 
      -+ssssssssssssssssssyyssss+-         OS: Ubuntu 22.04.2 LTS x86_64 
    .ossssssssssssssssssdMMMNysssso.       Host: Inspiron 3880 
   /ssssssssssshdmmNNmmyNMMMMhssssss/      Kernel: 5.19.0-43-generic 
  +ssssssssshmydMMMMMMMNddddyssssssss+     Uptime: 16 hours, 54 mins 
 /sssssssshNMMMyhhyyyyhmNMMMNhssssssss/    Packages: 1851 (dpkg), 16 (snap) 
.ssssssssdMMMNhsssssssssshNMMMdssssssss.   Shell: bash 5.1.16 
+sssshhhyNMMNyssssssssssssyNMMMysssssss+   Resolution: 1920x1080 
ossyNMMMNyMMhsssssssssssssshmmmhssssssso   DE: GNOME 42.5 
ossyNMMMNyMMhsssssssssssssshmmmhssssssso   WM: Mutter 
+sssshhhyNMMNyssssssssssssyNMMMysssssss+   WM Theme: Adwaita 
.ssssssssdMMMNhsssssssssshNMMMdssssssss.   Theme: Yaru-dark [GTK2/3] 
 /sssssssshNMMMyhhyyyyhdNMMMNhssssssss/    Icons: Yaru [GTK2/3] 
  +sssssssssdmydMMMMMMMMddddyssssssss+     Terminal: gnome-terminal 
   /ssssssssssshdmNNNNmyNMMMMhssssss/      CPU: Intel i5-10400 (12) @ 4.300GHz 
    .ossssssssssssssssssdMMMNysssso.       GPU: Intel CometLake-S GT2 [UHD Grap 
      -+sssssssssssssssssyyyssss+-         Memory: 7749MiB / 15745MiB 
        `:+ssssssssssssssssss+:`
            .-/+oossssoo+/-.                                       
                                                                   



```

---

### Post by mIk3_08 on 2023-06-07
Did you try to move around the mouse every-time the screen turns blank? In my case, I just move the mouse around and the time appears and it never turns blank screen again from the moment I move the mouse. I just see a "Click or Press a key to unlock" Regards and cheers.

---

### Post by sandmanfvr2 on 2023-06-07
I just tried that and it turned the screens back off in under a minute.  

Edit:  FIXED

I found Gnome Extensions and one is to ublank the lock screen.  Using the site below I installed the extention manager and then searched for unblank and found it for unblanking the screen at lock.  Installed that and locked screens and they stayed up!  Hopefully this helps others.  

[https://www.ubuntubuzz.com/2022/08/useful-10-gnome-extensions-for-ubuntu-2204.html](https://www.ubuntubuzz.com/2022/08/useful-10-gnome-extensions-for-ubuntu-2204.html)

---

### Post by mIk3_08 on 2023-06-07
In settings under "Power Menu" then "Power Saving Options" did you try to change the Screen Blank to "Never"? See image below.
Regards and cheers.

---

### Post by sandmanfvr2 on 2023-06-07
Yes I have that setting set to never, it still did it.  I guess why this extension is out there this is happening to others where gnome will blank the screens no matter what.  Its fixed now, the extension I installed for gnome fixed it.

---

### Post by mIk3_08 on 2023-06-07
> **sandmanfvr2 said:**
> Yes I have that setting set to never, it still did it.  I guess why this extension is out there this is happening to others where gnome will blank the screens no matter what.  Its fixed now, the extension I installed for gnome fixed it.
What extension is that, can you share it with us here? Is it the "Unblank lock Screen"? Regards and cheers.

---

### Post by sandmanfvr2 on 2023-06-07
Unblank lock screen

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292360&stc=1[/IMG]

---

### Post by mIk3_08 on 2023-06-07
Oh. That was cool. Thanks for sharing. Regards and cheers.

---

### Post by noletolucas on 2024-05-08
> **sandmanfvr2 said:**
> Unblank lock screen

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292360&stc=1[/IMG]

the "Unblank lock screen" Gnome plugin worked on Ubuntu 22.04.

thank you for the info. 

I don't know who's fault is this (Ubuntu, Gnome, ...), nevertheless this is so messed up. :( :(

---

