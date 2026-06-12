---
title: "[Question] &quot;Minimal BASH-like line editing is supported...&quot; after Ubuntu installed"
date: 2018-12-30
forum: General Help
---

### Post by auhs on 2018-12-30
Dear all,
After I follow the steps to install Ubuntu in my USB, I have faced that every time I start up my laptop when "[COLOR=#ff0000]I did not insert USB[/COLOR]", the screen will jump into "Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions      grub>" first.
Anyone can help to avoid this happen?

I following the below steps:

[FONT=Calibri]-Create a bootableUSB stick on Windows[/FONT]
[FONT=Calibri][https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#9](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#9)[/FONT]

[FONT=Calibri]-Install Ubuntudesktop[/FONT]
[FONT=Calibri][https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#0](https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop#0)[/FONT]

[FONT=Calibri]-Download UbuntuDesktop[/FONT]
[FONT=Calibri][https://www.ubuntu.com/download/desktop](https://www.ubuntu.com/download/desktop)[/FONT]

---

### Post by deadflowr on 2018-12-30
Something happened that broke the bootloader.
Please follow these links on running boot-info and boot-repair and post the pastebin link it gives
[https://help.ubuntu.com/community/Boot-Info]("https://help.ubuntu.com/community/Boot-Info")
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by clementc on 2018-12-31
Hi [**[COLOR=#000000]auhs[/COLOR]**]("https://ubuntuforums.org/member.php?u=2115150"),

In addition to what [**[COLOR=#C61919][B]deadflowr**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1276577") said, you could try following the steps listed on [this page]("https://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/") and report back if this has helped resolve your issue.

Please keep in mind that modifying the boot loader is always a risky process if something goes wrong. It is highly recommended to back up your files first.

---

### Post by auhs on 2019-01-06
Hello Deadflowr
Please check the [link]("https://drive.google.com/file/d/1usevMoqgbDw9Wo_PcyUyy5uxurAimp3T/view?usp=sharing"), about the outputs of "Boot-Info" & "Boot-Repair".

[B][SIZE=2][[COLOR=#000000]https://help.ubuntu.com/community/Boot-Info[/COLOR]]("https://help.ubuntu.com/community/Boot-Info")[/SIZE]
         => [/B]Please write on a paper the following URL:               [http://paste.ubuntu.com/p/5QwHnjnSKp/](http://paste.ubuntu.com/p/5QwHnjnSKp/)

_**[COLOR=#000000][SIZE=2]https://help.ubuntu.com/community/Boot-Repair[/SIZE][/COLOR]**_
                =>
                     Boot successfully repaired.


                     Please write on a paper the following URL:
                     [http://paste.ubuntu.com/p/j6nKXV8pgX/](http://paste.ubuntu.com/p/j6nKXV8pgX/)
========================================================================
After I done the Boot-Repair, I still suffer the same error as below (check the following link):
[IMG]https://drive.google.com/file/d/1GGcT_LKL8pE7zC0o4HDRmMCgmQ6XmiTa/view?usp=sharing[/IMG]
                        [https://drive.google.com/file/d/1GGcT_LKL8pE7zC0o4HDRmMCgmQ6XmiTa/view?usp=sharing](https://drive.google.com/file/d/1GGcT_LKL8pE7zC0o4HDRmMCgmQ6XmiTa/view?usp=sharing)

The weird thing is, I thought I just installed Ubuntu in my USB, will not have any impact with my original disks in laptop.
However, I just suffered the issue when I start up my laptop [COLOR=#ff0000]without[/COLOR] insert the USB...

---

### Post by deadflowr on 2019-01-06
I would think that new EFI/ESP partitions (redundant) would throw big fat wrenches into that methodology these days.
(The methodology of being able to install to an external drive and then insert and eject said device at will.) 
[https://askubuntu.com/questions/749350/where-should-the-bootloader-be-installed-when-i-want-to-run-ubuntu-from-an-exter?rq=1]("https://askubuntu.com/questions/749350/where-should-the-bootloader-be-installed-when-i-want-to-run-ubuntu-from-an-exter?rq=1")

---

