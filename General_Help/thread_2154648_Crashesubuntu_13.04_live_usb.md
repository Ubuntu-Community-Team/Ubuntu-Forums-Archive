---
title: "Crashes:ubuntu 13.04 live usb"
date: 2013-06-15
forum: General Help
---

### Post by manngaurav on 2013-06-15
HEY I HAVE BEEN USING UBUNTU 13.04 WITH LIVE USB FOR THE PAST 30MIN, and my laptop acer aspire 4752,2gb ram and my sytstem HANGED 3 times so i had to force shut down .
Now instead of hanging it CRASHES with a BLACK screen and some highly non-understanble TEXT , i dont know what to do ,it had happened 2times .  I was about to wipe my system and install only ubuntu, so is this the problem with live usb or the OS ..? or my system..? please help         [ATTACH=CONFIG]243902[/ATTACH][ATTACH=CONFIG]243898[/ATTACH][ATTACH=CONFIG]243899[/ATTACH][ATTACH=CONFIG]243904[/ATTACH][ATTACH=CONFIG]243903[/ATTACH][ATTACH=CONFIG]243905[/ATTACH]
I HAVE NOTICED THAT THIS HAPPENS ONLY WHEN I RUN WIFIRADAR OR AIRMON-NG , my wifi has got a problem:it doesnt show any networks although its enabled

---

### Post by 2F4U on 2013-06-15
There is near to no information in your post, so I guess you won't get much feedback. You should at least post this "non-understandable" text, for example by taking a picture with a camera.
How did you create the liveUSB? It may be corrupt, i.e. a bad burn. Did you verify the checksum of the downloaded iso file? The download may be corrupt.

---

### Post by manngaurav on 2013-06-15
I am sorry for that but i don't have any camera :(  (i know it might look like i am from stone age but that's true i dont have anything except a laptop). yes i verified the checksum, . I created the usb with unetbootin ,

---

### Post by manngaurav on 2013-06-16
Can soemone please tell me how to make my post more informative , i dont know any commands , is there a crash file like minidump in windows..?  something that might help .. ?

---

### Post by carboi82 on 2013-06-16
Chances are the hanging is just from using a usb drive... remember the read/writes on just about any usb are going to be far slower than a hdd response time. If you want to give it a better trial without wiping windows, use windows disk management to create a partition (10gb will be plenty) and install linux on it with wubi. Just make sure youre installing linux to the right partition (and when in doubt back up your stuff whenever possible!).

After, youll have the option of which os to boot to on startup, and can give linux a shot. If you still have issues with it crashing then, you can choose to try and solve them, or just stick with windows. If you decide its unworkable, uninstall it and add the partitioned space back to your c drive or wherever you took it from initially. If you do decide to stick with linux (and have backed up your data), you can always repartition the drive and reinstall it as the only os.

---

### Post by manngaurav on 2013-06-16
hmm..  i have tried to install but got stuck so have started another thread because i can not EVEN install ubuntu after selecting the language and partiiton nothing happens just black screen :( and system reboots

---

### Post by sudodus on 2013-06-16
Maybe Ubuntu 13.04 needs a more powerful computer to run well (but we can only guess until we get more information from you). 

Please specify the specification of you computer:

- desktop or laptop
- brand name and model, cpu, ram size, graphics card/chip

This information is available from Windows (if you have it) or linux. When booted from the USB drive, run the terminal window command

```
 sudo lshw > lshw.txt
```

and get the relevant information from the file **[FONT=courier new]lshw.txt[/FONT]**

or run the GUI tool ***hardinfo*** and get the relevant information from the menus.

When we know about your computer, we can give better advice, which version and flavour of Ubuntu to run. There are desktop environments with much lighter foot-print than standard Ubuntu.

---

### Post by manngaurav on 2013-06-16
i have acer aspire 4752
inter core-i3 2330M sandy-bridge
64bit,  2gb ram, intel hd graphics 3000

---

### Post by sudodus on 2013-06-16
Now we know that your computer is capable to run any Ubuntu version and flavour live and installed. If I should advice anything, it is that the 64-bit version wants more memory, so the 32-bit version might work better with 2 GB RAM.

There might be an issue with some driver, maybe with the wifi chip. You can check if it is possible switch the wifi off (either with a hardware switch or in a bios menu). You can also try some boot option, but intel graphics is usually working without problems (unless it is combined with some other graphics).

And you can choose *your* sweet point between speed and eye-candy

```

fast and simple
^  Lubuntu with LXDE
|  Xubuntu with XFCE
|  Ubuntu with Unity
v  Kubuntu with KDE
slow and fancy
```

Can you repeat the crash and write down the error messages (the text on the screen)?

---

### Post by Irihapeti on 2013-06-17
We don't support Aircrack in this forum, even though it's in the repos. Aircrack has its own forums where you can get help.

Since the problem mentioned in this thread appears to be related to Aircrack only, it's being closed. If you have other problems that aren't related, please start a new thread.

---

