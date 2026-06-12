---
title: "Stuck at boot with error message and initramfs"
date: 2019-07-18
forum: General Help
---

### Post by danbg on 2019-07-18
Hi guys,

is there a hope I could log in . I got this screen [https://ibb.co/PZ8DTrr]("https://ibb.co/PZ8DTrr")

Thanks in advance!

---

### Post by CatKiller on 2019-07-18
You have errors with your discs. Booting from the install image will let you run fsck on them when they aren't mounted to see if it's because the filesystem is messed up or if your drive is failing.

---

### Post by danbg on 2019-07-19
> **CatKiller said:**
> You have errors with your discs. Booting from the install image will let you run fsck on them when they aren't mounted to see if it's because the filesystem is messed up or if your drive is failing.


Thanks for the reply.

How it all begun - I have dual but Win 10 and Ubuntu. Laptop was in sleep state for a week, when I opened the lid yesterday it froze for 10 minutes without indication to be ok. So I long pressed switch off. And when It booted I noticed a message with few lines containing this ```
end_request I/O error, dev sda, sector xxxxxxxxx1 ... xxxxxxxxx2 xxxxxxxx3 ...
```.

So I ran a fsck from live usb and got a message for** multiple-claimed block(s), shared with 1 file(s)**. There was a question "Clone multiply-claimed blocks" when I ran e2fsck. I skipped it, because I want to be able to boot somehow and to save data which could not be transferred via live usb.

What should I do. 
Thanks in advance.

---

### Post by CatKiller on 2019-07-19
You should still be able to copy files to another USB drive, or online storage, or somewhere else on your network, from the live USB.

You aren't going to be able to boot without fsck fixing those errors.

---

### Post by danbg on 2019-07-20
[COLOR=#000000][FONT=&quot]I pressed "yes" multiple times to fsck command, rebooted and I see the logo of Kubuntu for about 2 minutes and after that only blinking cursor on upper left of black screen. No CPU activity and nothing happens.[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]I'm not able to connect to internet via recovery mode.[/FONT][/COLOR]

[COLOR=#000000][FONT=&quot]Any suggestions? Thanks in advance![/FONT][/COLOR]

---

### Post by CatKiller on 2019-07-20
Recovery mode is not the same as running from the install disc. If you needed to do anything particular to make your Internet work after you installed, you'd need to do the same in the install disc.

The indications are that your hard drive has failed. fsck can only fix filesystem errors, it can't make a drive that is broken work. If you had filesystem errors from the improper shutdown, fsck would potentially have been able to fix most of those. If the initial freeze was because of hardware failure, there's nothing fsck can do.

I wish I had better news for you, but copying off whatever you can and then replacing the drive seems to be the thing to do at this point.

---

### Post by danbg on 2019-07-20
Is there anything you could suggest me to try before I reinstall?
Thanks in advance!

---

### Post by CatKiller on 2019-07-20
If it's hardware failure, reinstalling on the same drive won't help you.

---

### Post by danbg on 2019-07-20
> **CatKiller said:**
> If it's hardware failure, reinstalling on the same drive won't help you.

I doubt it is hardware failure because:

1 - Windows 10 Works
2 - I read others have similar problem when force turning off during update. I forgot to mention, that the system froze when I opened the lid because of system update in background.

---

### Post by danbg on 2019-07-22
So, BIG UPDATE for those who are in my position, plus a free advice in the end..

There is a reason why we all love Linux and distros - it is open source, it is free like freedom and it allows you to do "magic".

I did force halted the system while there was update in the background, and after fsck from live USB, I got the errors above. I wrote in 3 forums for Ubuntu (included Kubuntu, because I use KDE) and I got nothing similar to HELP.

So I dived in old threads, when the community was still strong and what made me switch from windows since XP late era.
Anyway, the steps:

1 - install live usb (preferably with Debian or close derivative) as light as possible. It is needed to be light because if you are with older hardware, it might freeze when it should transfer files!
2 - Install thunar file manager, and open it with sudo thunar. You must be root when you transfer!
3 - Connect mobile HDD, open in new windows as root and transfer all important data, like files and pictures. When you are root you will not get error message for file types or errors for permissions.
4 - When you are ready, turn off the computer, **install on the same USB flash or another THE SAME DISTRIBUTION AND VERSION you were using previously**! In my case it was Kubuntu 18.04.02.
5 - Boot the live usb, and press 'install"
6 - When you go to the process, it is very important not to change partition size. **Everything must be the same. Select your partition as "/", ext4 type, and DO NOT check format drive. Use the same username and password as before and press install. It will RECOVER ONLY BROKEN PACKAGES!**
7 - Before the end of the process, you might get a notification, that not all software was installed, so you should do it manually. Do not worry ;)
8 - log in, do ```
sudo apt-get update && sudo apt-get upgrade
```
9 - In my case I did not have chromium installed, so I checked in** .config folder** is there a folder with settings for chromium. There were all the folders for all software I used.
10 - Just install needed software - browsers, editors or whatever.
11 - Opened chromium and all the settings and history were there..

12 - [SIZE=4]Enjoy the freedom and share the knowledge![/SIZE]

The free advice - In some forums I even got rude comments and thread closed, when just searching for help. Everybody including here in this thread told me it is HDD error. The simple logic was, that the problem occurred while force halting during upgrade. But I guess it is easier nowadays just to say "I'm sorry nothing could be done".
So in essence - listen your own logic and search in old threads, which have universal code basics. Few years ago the community was different.

All the best. I hope I helped somebody out there:)

---

