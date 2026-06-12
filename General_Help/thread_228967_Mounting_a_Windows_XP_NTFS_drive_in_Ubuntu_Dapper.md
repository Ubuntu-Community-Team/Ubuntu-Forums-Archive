---
title: "Mounting a Windows XP NTFS drive in Ubuntu Dapper"
date: 2006-08-03
forum: General Help
---

### Post by nightfire117 on 2006-08-03
Hello all. First post - hehe.

I have a question. I am using Ubuntu 6.06 Dapper Drake. I have 2 hard drives in my computer, my primary Ubuntu drive and my secondary Windows XP drive. (I have it set up this way so I can use the Linux boot manager, whatever it's called - Grub, is it...?) Anyway.

I have a problem. I am trying to mount my Windows XP drive in /mnt/win. First, I created this directory in the terminal (sudo mkdir /mnt/win). Then, I went to edit my FSTAB (sudo gedit /etc/fstab). Here is what it contains:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /mnt/win	ntfs    nls=utf8,umask=0222 0       0
```

I have modified it several times. Before, I was getting permission errors. Now, it seems to be working fine... sort of. I go to "Places>Computer" in the Gnome menu/taskbar, and try to double-click my Windows drive (57.3 GB Volume: /mnt/win), it seems to be working and goes into /mnt/win (apparently), but nothing shows up. It's like a blank folder.

When I right-click the drive and select Properties, in the Permission tab, it says:

```

File owner: unknown
File group: unknown

Owner: [X] Read [ ] Write [ ] Execute
Owner: [X] Read [ ] Write [ ] Execute
Owner: [X] Read [ ] Write [ ] Execute

Special flags: [ ] Set user ID
               [ ] Set group ID
               [ ] Sticky

Text view: -r--r--r--
Number view: 444
Last changed: unkown
```

However, I can access the folder with no problem when I go into the Terminal and type su and enter my password. I just type cd /mnt/win/ and then browse the drive in the terminal. It's not very convenient though, especially making myself a superuser. 

So, what I would like to do would be to BROWSE my Windows drive within any user account in Ubuntu. There doesn't seem to be a root account in Ubuntu, at least none that I've been able to find.

I'm fairly new to Linux. My first distro was Debian, and when I used it I had no idea what Linux was (pretty much, hehe.), but it accomplished what I wanted it to do. Then, I moved to Freespire, which I didn't like because of CNR and it only had KDE, and now I'm over to Ubuntu. I might consider going back to Debian if noone is able to help me with this issue, since I never had any problems with Debian.

Any help would be MUCH appreciated.

-=Nightfire=-

---

### Post by ciscosurfer on 2006-08-03
That looks correct.  Have you remounted your list?```
sudo mount -a
``` Try this line in place of 'nls=utf8....'```
defaults,nls=utf8,umask=007,gid=46 0 1
```

---

### Post by nightfire117 on 2006-08-03
I've remounted it, same results. Let me try that replacement, as soon as I get around to it. Unfortunately I messed something up and X window manager won't start. Don't ask. Hehehe. I tried an unofficial method to install nVidia drivers. Anyway, I'll try that and let you know how it goes.

~Nightfire

[EDIT]: After remounting it and adding that line you specified, it works, and very nicely too. Thank you very much, I am very glad you could help me!!! I am indebted to you hehe. :D Thanks alot! :D ^_^

~Nightfire

---

