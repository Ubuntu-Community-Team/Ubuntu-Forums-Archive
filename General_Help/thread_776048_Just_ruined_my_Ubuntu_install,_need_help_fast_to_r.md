---
title: "Just ruined my Ubuntu install, need help fast to recover critical files"
date: 2008-04-30
forum: General Help
---

### Post by NoPantsJim on 2008-04-30
My system is setup on a laptop with two partitions, one has Ubuntu 7.10 while the other runs Windows XP. I just recently changed some Compiz settings and added some plugins, now Ubuntu does not boot properly.

When I boot Ubuntu, I am able to login, but the system hangs when the desktop wall paper shows up. The mouse moves around and such, but all of my desktop icons are gone and there is no taskbar. I am able to switch back and forth between the two available workspaces (I usually use 4, now only 2 show up) but they are identical.

I tried booting with my Ubuntu cd and got into the live version to move all my files onto a usb drive, but ran into issues. Some of the more critically important documents and folders have a small circle with an X in it over the icon. When I try to open or copy them, I am told I do not have permission. These are not system files or anything, but just Open Office documents, presentations, and some other various files on the desktop.

I need to get to these files before Thursday night or I'm going to be in a serious world of hurt. Any help is greatly appreciated.

---

### Post by tom66 on 2008-04-30
Have you tried using sudo? Although not recommended, open up Terminal, type "sudo nautilus" (if a password prompt comes up, enter nothing), then try copying the files. Note that the manager won't have your favourite locations, if any, and you might have to manually find the disks under /media, but it should work. 

If that fails, start Ubuntu in recovery mode, and select 'drop to root shell/prompt'. Then use the cp command to copy files to your usb stick. Or you could try starting X by typing 'startx', but it may end up in the same situation. 

Hope this helps

---

### Post by TeoBigusGeekus on 2008-04-30
Solution No1:

Enter in recovery mode and type

```
sudo dkpg-reconfigure -phigh xserver-xorg
```

to readjust your graphical settings.




Solution No2:

Boot up in window$, install IFS
[http://www.fs-driver.org/]("http://www.fs-driver.org/")
and do your backup from there.

---

### Post by lemming465 on 2008-04-30
If you are comfortable with command lines, from the live version you can open up a terminal window, type *sudo -i*, and use things like "cp" at will.

For a GUI version, press [Alt]+[F2], type *gksu nautilus*, and drag & drop.

The live CD isn't running as either your permanent user or as root, which is why it lacks permissions to read some files.  Running as root will definitely give you full permissions, which is why physical access to hosts is the start of all security.

---

### Post by NoPantsJim on 2008-04-30
Thanks for the suggestions. I'm currently at work so I can't try anything til I get home.

I don't suppose there's an easy way to just disable Compiz from running at startup is there?

---

### Post by jimv on 2008-04-30
You could try removing your compiz settings so they get set back to default. 

Switch to a terminal (control+alt+f1) and type:

mv ~/.compiz ~/.compiz.old

---

### Post by NoPantsJim on 2008-04-30
Thanks for all the suggestions, but I found a way to solve the issue.

Luckily for me, popping my USB drive into the laptop caused Ubuntu to open a window showing the contents of the drive. From there I was able to navigate the hard drive, copying files and then pasting them to the USB drive. It's going to take me awhile to complete the process, but it'll be worth it to not lose everything.

The Ubuntu install still seems unusable. I suppose this is a good excuse to install 8.04 sooner than I had originally intended.

---

### Post by jimv on 2008-04-30
OH yeah, put some pants on.

---

### Post by NoPantsJim on 2008-04-30
> **jimv said:**
> OH yeah, put some pants on.

Not happening.

---

