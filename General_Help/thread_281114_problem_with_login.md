---
title: "problem with login"
date: 2006-10-20
forum: General Help
---

### Post by Khan1 on 2006-10-20
Hello!

Yesterday I came home and computer was still working (I left it). There were some "errors" shown in torrent downloading in Ktorrent aplication. I restarted computer and next time I couldn't login.
](*,) 
When I write down password (and the password is correct) there are some "clicks" in my monitor and then "Login manager" appeares again asking me for password. I can' go into my sistem. Everything was allright until now.
I can login but only in non-graphic view (console).

What could be wrong?

All my data are in computer, so I must resolve this problem.

Thank you for helping me.

---

### Post by CatKiller on 2006-10-20
> **Khan1 said:**
> What could be wrong?

It's possible that a problem with your X configuration means that X can't find a resolution that works. I don't know why this might have happened to you, but a ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` may help you to resolve it.

---

### Post by Khan1 on 2006-10-20
> **CatKiller said:**
> It's possible that a problem with your X configuration means that X can't find a resolution that works. I don't know why this might have happened to you, but a ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` may help you to resolve it.

Thanks for helping. I tried, but nothing happened. It's all the same.

I wrote a code. It says something like "file may be overwriting. backup saved at xxxxxx" (I hope I recalled it in my memory correctly) then I restarted and unfortunately it's all the same.

Maybe some other suggestions?

---

### Post by Khan1 on 2006-10-21
If there are no suggestions further, is then there possibiity to acces hard drive via "Live CD"?

I tried but it can't mount it, because it says "Could not mount device. The reported error was: mount: can't find /dev/hda4 in /etc/fstab or /etc/mtab".

It would be very helpfull so I can backup my data from it.

Thanks.

---

### Post by CatKiller on 2006-10-21
In what way did nothing happen? Did you try to change the configuration? The "vesa" driver may help somewhat to get your graphical setup back - it's very basic.

You can probably back up your stuff from the command line, but if you'd rather do it from a graphical environment, you could boot from the live cd and do something like ```
sudo mkdir /mnt/linux
sudo mount /dev/hda4 /mnt/linux
```

---

### Post by Khan1 on 2006-10-22
> **CatKiller said:**
> In what way did nothing happen? Did you try to change the configuration? The "vesa" driver may help somewhat to get your graphical setup back - it's very basic.

When I write down code:

> "sudo dpkg-reconfigure -phigh xserver-xorg"

I got this message from konsole:

> "xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in etc/x11/xorg.conf.20061022095758"

I wrote this code both in "recovery mode" and "login from konsole". That's all what happens.
----------------------------------------------------------------


And one more thing:
1. where are stored files where I have e-mails in kmail? (so I can recover my e-mails with saving that files in same directory in new fresh clean install of kubuntu)

2.  where I have files of my not fully downloaded files of torrents (I know where are data files but what I mean is .torrent files) so I can start downloading torrents in fresh installed Kubuntu just where I stopped in old one? And how can I do it? (I hope it can be done just how I have in mind)

(for these two lines I hope I found correct files and resolved problems)
3. where are stored files where I have my contacts in Kontact (and do the same as in 1. line)?
(/home/user/.kde/share/apps/kabc/std.vcf) - I hope this is correct

4. and where are files for calendar? (and do the same as in 1. line)
(/home/user/.kde/share/apps/korganizer/std.ics) - I hope this is correct

Thank you in advance.

PS.
Thanks CatKiller for last code you give me (about mounting hda from live cd). Is very helpful (however I can't open locked folders, (example: /.kde), but I can acces them through Windows which I have in dual boot when migrating to Kubuntu)

I really don't know what went wrong with Kubuntu. Probably (as I booted in recovery mode) I saw konsole reporting me some bad CRC in hard disk (I don't remember reporting it for the first time I logged in in recovery mode). So maybe there's something wrong with hard disk or maybe konsole was reporting this because its way treating of not succeded logins all the times I tried.

---

### Post by CatKiller on 2006-10-22
Ah. That does sound like something bad has happened to the X server. Normally that command would bring up an interactive configuration tool that lets you select drivers and resolutions and the like. I suppose that hard drive problems might cause this, but I don't know for sure. Have you installed on a FAT partition to be able to access the files from Windows or install the Windows driver? You probably shouldn't install Linux on a FAT partition.

I haven't used KDE so I don't know specifically where your configuration files are, but they'll be in your Home folder somewhere. Your Home folder may not be very large in its entirety, to copy the whole thing somewhere and then copy it back when you've reinstalled.

You could do a ```
sudo updatedb
locate .torrent
``` to find where your .torrent files have been put.

For mounting things in the live cd, you could use ```
kdesu konqueror
``` (I think) to browse the files as root. I forgot that you'd be a **different** standard user when using the live disk.

---

### Post by Khan1 on 2006-10-22
> **CatKiller said:**
> Have you installed on a FAT partition to be able to access the files from Windows or install the Windows driver? You probably shouldn't install Linux on a FAT partition.

No, Kubuntu is installed in ext3 partition. Win xp in ntfs. But I looked a little bit this forum and found this thread [http://www.ubuntuforums.org/showthread.php?t=281399]("http://www.ubuntuforums.org/showthread.php?t=281399")
and installed driver in windows with which I can acces on ext3 partition read/write from it. Very usefull.

---

