---
title: "No GUI with Lubuntu 14"
date: 2017-02-16
forum: General Help
---

### Post by awemans on 2017-02-16
Hi all,

I'm trying to recover an old notebook Samsung Q30+ with the following specs:
Intel Pentium M 1.20 GHz
RAM 504 MB
Graphic Adapter Intel 915GM/GMS, 910GML Express Chipset 128 MB

Due the low RAM memory I thought better to install Lubuntu 14 instead of the 16 but I'm having a problem with GUI not showing and instead it starts with the command line.
The strange thing is if I choose recovery mode at boot and then exit from it, but without doing anything else while in the recovery mode, the Lubuntu's GUI works well. But if it is a regular boot it appears only the command line.

At this moment the notebook is with a dual boot having also a XP installation. But the problem was the same when it was a single Lubuntu installation except that in that case I had to press ALT+F1 to get tty1 and the command line.

Is there a way to correct this problem?

Best regards,
Andre

---

### Post by ajgreeny on 2017-02-16
At the command line, login using your username and password (password will not show as you type) and then run command ```
sudo apt-get install xserver-xorg-video-intel
```

This is probably the bug that the intel driver is not installed at the time the OS is installed which I suffered from as well, though I could not even get to the command line.
If you run the recovery mode and exit without a reboot the system uses the backup graphics without the proper card driver, hence you getting to a GUI that way.

See [https://ubuntuforums.org/showthread.php?t=2322941](https://ubuntuforums.org/showthread.php?t=2322941) for the thread I started about this.

---

### Post by awemans on 2017-02-16
Thanks ajgreeny.

I tried your suggestion but my problem was more drastic since it complain that that package needed two others to work and they weren't installed or were broken.

But as soon as I installed the first, xserver-xorg-core, it was solved.

Thank you very much for the help, I have been strogling with this for some time now.

Best regards,
Andre

---

### Post by Impavidus on 2017-02-16
Keep in mind that Lubuntu 14.04 will reach end of life in two months.

---

### Post by ajgreeny on 2017-02-16
> **Impavidus said:**
> Keep in mind that Lubuntu 14.04 will reach end of life in two months.

Very good point, and not one to be dismissed lightly as you will get no more updates from April this year so security could be compromised.

I suggest you do try Lubuntu 16.04, which uses no more resources than 14.04, and in my experience is a superior Lubuntu version; it runs more smoothly for me than 14.04 did on an my netbook with Atom N270 cpu and 1GB ram that had the same problem that you saw and was the the subject machine of my linked thread.

---

### Post by awemans on 2017-02-17
Thank you Impavidus and ajgreeny.

I will try the lubuntu 16 to see if the notebook can handle it. I'm not counting to do heavy loads with it so maybe it will be able to work well with 16.

Best regards,
Andre

---

