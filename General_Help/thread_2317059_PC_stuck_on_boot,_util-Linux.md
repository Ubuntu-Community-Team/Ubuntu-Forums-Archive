---
title: "PC stuck on boot, util-Linux"
date: 2016-03-13
forum: General Help
---

### Post by robertt3 on 2016-03-13
I've had so many problems I wish I could go back to Windows. My PC is screwed now. Anyway I'm trying to fix it but it's stuck on boot for hours. And it won't go past. I can go on CTRL + ALT + F1,

I've tried booting from USB but it still goes on that.

Error;

Fsck from util-linux 2.26.2

/dev/sda6: clean ******\******** files, ********\*********** blocks 

Everything past this       has a prefix of [ OK ]


Created slice user124.slice
Starting user manager for UID124
Started session c1 of user gdm
Started user manager for UID124
Stopping user manager for UID124

Started LSB: start samba daemons for the AD DC.
Started LSB: start Samba NETBIOS NAMESERVER (nmbd)
Starting LSB: start Samba SMB/CIFS daemon (smbd)
Started LSB: start samba SMB/CIFS daemon (smbd)
Started detect the available GPUs and deal with any system changes
Starting gnome display manager
Started GNOME display manager

Hope someone can help, thanks

---

### Post by coldraven on 2016-03-13
> I've tried booting from USB but it still goes on that.
I don't understand what you are trying to say.

---

### Post by robertt3 on 2016-03-13
Sorry, what I meant was I tried booting up Ubuntu (fresh copy) on a USB (from BIOS) and it still went on that loading screen.

---

### Post by RobGoss on 2016-03-13
Give us in details how you created your boot able USB stick and what version of Ubuntu are you trying to install, the more information you provide the better we can assist you. Presenting us with the specs of your machine would also be a good idea

It could be a bad download or something your doing incorrectly

Are you trying to setup a dual boot of just installing Ubuntu on this machine?

---

### Post by sammiev on 2016-03-13
You give us no computer specs.

You do not give us the version and flavor of the OS you downloaded.

Have you checked the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") of the download?

---

### Post by robertt3 on 2016-03-13
On the USB I have the latest version of Ubuntu. On the PC, it's 14.03. My PC was prebuilt, how would I find the specs if I can only get on the terminal?

Thanks.

---

### Post by sammiev on 2016-03-13
This will list your computer spec.  Please use code tags to post the info from the command.

```
sudo lshw
```

You haven't posted if you checked the md5sum of you downloads yet.

---

### Post by robertt3 on 2016-03-14
I have not checked the Md5 sums.
I used the command but but comes up with a lot of writing, how am I supposed to copy it all down?

Thanks.

---

### Post by mastablasta on 2016-03-14
```
sudo lshw -sanitize >> myspecs.txt
```

then you can attach file myspecs.txt (or whatever you called it in command above) here.

edit: sanitize will remove any sensitive information you may not want to share (hardware ID number, IP)

---

### Post by robertt3 on 2016-03-14
I can't get on the Internet.
I only have access to the terminal via CTRL ALT F1.

---

### Post by mastablasta on 2016-03-14
it doesn't matter. just copy the txt file to USB or other media and then use another computer to post it.

by the way - Lynx is a text web browser that works in terminal (you will get all pages as ***text only***).

---

### Post by grahammechanical on 2016-03-14
> I can't get on the Internet. I only have access to the terminal via CTRL ALT F1.

Are you connected to the router by ethernet cable? If so, you can use recovery mode to get both an internet connection and a command line. If you do not get a Grub boot menu press Shift as the motherboard splash screen appears.

At the Grub boot menu select Advanced options for Ubuntu and then select the recovery mode kernel. At the recovery menu select Network and then when back at the recovery menu select Root - root shell prompt.

When finished type exit to get back to the recovery menu and then select Resume - resume normal boot. One of the first things I try in situations like this is recovery mode>resume that should get us to a desktop without using a proprietary video driver. It sometimes works.

Regards.

---

